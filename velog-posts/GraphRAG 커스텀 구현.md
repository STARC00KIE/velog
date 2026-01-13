<h1 id="0파이프라인">0.파이프라인</h1>
<p><img alt="" src="https://velog.velcdn.com/images/starcookie/post/e1f162db-0195-40db-b3f9-77e104a30f7f/image.png" /></p>
<hr />
<h1 id="1-프롬프트-튜닝선택적">1. 프롬프트 튜닝(선택적)</h1>
<ul>
<li>MS GraphRAG CLI 사용<pre><code class="language-bash">graphrag prompt-tune --root . --config settings.yaml --output prompts</code></pre>
<h2 id="변경된-프롬프트">변경된 프롬프트</h2>
</li>
<li><code>community_report_graph.txt</code><pre><code class="language-text">...
You are an expert in Human Resources and Employment Law. You are killed at analyzing organizational structures, understanding employment regulations, and
...</code></pre>
</li>
<li><code>extract_graph.txt</code><pre><code class="language-text">...
(&quot;relationship&quot;{tuple_delimiter}징계{tuple_delimiter}직장 내 괴롭힘{tuple_delimiter}직장 내 괴롭힘 행위는 징계의 대상이 된다.{tuple_delimiter}9)
{completion_delimiter}
#############################

</code></pre>
</li>
</ul>
<p>Example 2:</p>
<p>entity_types: [organization, employee, employment contract, disciplinary action, compensation, working hours, leave policy, gender equality, workplace harassment, performance evaluation, social security system]
text:
계 구분 
징계의 대상이 되는 사유 중 그 경중에 따라서 면직, 정직, 감봉, 견책, 경고로 구분한다.
...</p>
<pre><code>- `summarize_descriptions.txt`
```text
You are an expert in Human Resources and Employment Law. You are skilled at analyzing organizational structures, understanding employment regulations, and identifying key relationships within professional communities. You are adept at helping people navigate complex HR issues, ensuring compliance with employment laws, and fostering a cohesive and legally sound workplace environment.
Using your expertise
...</code></pre><hr />
<h1 id="2-인덱싱-및-데이터-적재">2. 인덱싱 및 데이터 적재</h1>
<ul>
<li>2.1. MS GraphRAG CLI 사용하여 인덱싱 진행<pre><code class="language-bash">graphrag index --root . --config settings.yaml
</code></pre>
</li>
</ul>
<h1 id="실행-후-output폴더에filenameparquet-파일로-데이터-적재됨">실행 후 output<code>폴더에</code>{filename}.parquet` 파일로 데이터 적재됨</h1>
<pre><code>- 2.2. `neo4j`와 `Qdrant`는 `docker-compose.yml` 파일 이용하여 로컬에서 실행
  - 도커 종료해도 적재된 데이터 유지될 수 있도록 스크립트 작성
  - `DOC_RAG/data/`  폴더 내에 데이터 적재
  - `load.py`로 적재 및 `verify.py`로 검증
  - **현재는 DB에 적재할 때마다 기존에 존재하던 데이터는 삭제 후 적재가 되도록 설정되어 있음**

## 2.3. 데이터 유형별 적재 위치
### neo4j (그래프 데이터베이스)
- 그래프 구조 데이터가 저장됨
#### 1. __Entities (엔티티 노드)__
- __내용__: 문서에서 추출된 개체 (사람, 조직, 개념 등)
- __속성__:
  - `id`: 엔티티 고유 ID
  - `name`: 엔티티 이름
  - `type`: 엔티티 유형 (PERSON, ORGANIZATION 등)
  - `description`: 엔티티 설명
  - `community_ids`: 소속 커뮤니티 ID 리스트
- __예시__: &quot;인사팀&quot;, &quot;연차&quot;, &quot;휴가 제도&quot;

#### 2. __Relationships (관계 엣지)__
- __내용__: 엔티티 간의 연결 관계
- __속성__:
  - `description`: 관계 설명
  - `weight`: 관계 강도/가중치
- __예시__: &quot;인사팀&quot; → MANAGES → &quot;휴가 제도&quot;

#### 3. __Communities (커뮤니티 노드)__
- __내용__: Leiden 알고리즘으로 감지된 엔티티 그룹
- __속성__:
  - `id`: 커뮤니티 ID
  - `level`: 계층 레벨
  - `title`: 커뮤니티 제목
- __역할__: 관련된 엔티티들을 묶어서 주제별 그룹화
---
### Qdrant (벡터 데이터베이스)
- 벡터 임베딩과 검색용 데이터가 저장됩

#### 1. __Text Units (텍스트 유닛)__
- __컬렉션__: `text_units`
- __내용__: 문서를 청킹한 원본 텍스트 조각
- __벡터__: 텍스트 임베딩
- __메타데이터__: `text`, `id`, `n_tokens`
- __용도__: 유사도 기반 원문 검색

#### 2. __Entity Embeddings (엔티티 임베딩)__
- __컬렉션__: `entities`
- __내용__: 엔티티 설명의 벡터 표현
- __벡터__: 엔티티 설명 임베딩
- __메타데이터__: `name`, `type`, `description`, `id`
- __용도__: 질문과 유사한 엔티티 발견

#### 3. __Community Reports (커뮤니티 리포트)__
- __컬렉션__: `community_reports`
- __내용__: 각 커뮤니티의 요약 보고서
- __벡터__: 제목+요약 임베딩
- __메타데이터__: `community_id`, `title`, `summary`, `full_content`, `level`, `rank`
- __용도__: Global Search에서 전체적인 맥락 파악

#### 4. __Claims (사실 정보)__
- __컬렉션__: `claims`
- __내용__: 문서에서 추출된 사실/주장 정보
- __벡터__: 클레임 임베딩
- __메타데이터__: `text`, `entity_id`, `claim_id`
- __용도__: 구체적인 사실 정보 검색
---
# 3.Query Engine 구현
- `main.py`에 `Global Search`, `Local Search` 구현
- CLI 이용하려고 했지만 input 데이터 로딩 방식의 차이로 인해 MS GraphRAG 코드 참고하여 직접 구현
## Local Search &amp; Global Search 공식문서, 커스텀 비교 표
---
### 3.1. __Local Search 비교__

### 공식 vs main.py 공통 순서:

```javascript
1. 벡터 검색 → 관련 엔티티 찾기
2. 그래프 탐색 → 관계 &amp; 이웃 수집  
3. 커뮤니티 매핑 → 커뮤니티 리포트 가져오기
4. 텍스트 검색 → 원문 텍스트 찾기
5. 토큰 예산 적용 → 중요한 것만 선택
6. 컨텍스트 구성 → 통합
7. LLM 생성 → 최종 답변</code></pre><h3 id="mainpy만-추가된-단계">main.py만 추가된 단계:</h3>
<pre><code class="language-javascript">- 3.5단계: Claims 검색 (사실 정보)
- 5단계: 복합 점수 계산 (엔티티 점수 × 관계 가중치)
- 6단계: 비율 기반 토큰 배분 (10%, 20%, 20%, 10%, 40%)</code></pre>
<ul>
<li>알고리즘 골격 동일</li>
</ul>
<hr />
<h3 id="32-global-search-비교">3.2. <strong>Global Search 비교</strong></h3>
<h3 id="공식-vs-mainpy-공통-순서">공식 vs main.py 공통 순서:</h3>
<pre><code class="language-javascript">1. 커뮤니티 리포트(질문 맥락과 관련된 정보들을 묶어서 미리 요약해둔 리포트) 로드
2. MAP Phase → 각 커뮤니티에 질문 던지기
3. REDUCE Phase → 모든 응답 통합하여 최종 답변 생성</code></pre>
<h3 id="핵심-차이점">핵심 차이점:</h3>
<table>
<thead>
<tr>
<th>단계</th>
<th>MS Graph RAG 공식</th>
<th>main.py</th>
</tr>
</thead>
<tbody><tr>
<td><strong>2. MAP</strong></td>
<td>병렬 처리 (빠름)</td>
<td>순차 처리 (느림)</td>
</tr>
<tr>
<td><strong>2.5. MAP 응답</strong></td>
<td>자유 텍스트</td>
<td>JSON 구조화 <code>{&quot;score&quot;: 8}</code></td>
</tr>
<tr>
<td><strong>2.7. 필터링</strong></td>
<td>모든 응답 수집</td>
<td>점수 &gt; 0만 선택</td>
</tr>
<tr>
<td><strong>2.8. 최적화</strong></td>
<td>없음</td>
<td>점수 순 정렬 + 토큰 예산 선택</td>
</tr>
<tr>
<td><strong>3. REDUCE</strong></td>
<td>모든 응답 사용</td>
<td>선택된 중요 응답만 사용</td>
</tr>
</tbody></table>
<hr />
<h3 id="종합-비교">종합 비교</h3>
<ul>
<li>두 알고리즘 모두 공식 문서와 기본 골격 및 패턴 구현</li>
</ul>