<h1 id="0-진행-흐름">0. 진행 흐름</h1>
<ul>
<li>서빙 자동화: vLLM을 이용해 테스트할 모델들을 순차적으로 서빙</li>
<li>검색 엔진 구축: GraphRAG를 활용하여 구조화된 컨텍스트를 추출</li>
<li>추론 및 성능 측정 (Inference): 추론 및 W&amp;B를 통해 Latency와 TPS를 실시간 모니터링</li>
<li>성능 평가 (Ragas): LLM-as-a-judge를 활용해 답변의 신뢰성과 정확도를 평가</li>
</ul>
<hr />
<h1 id="1-graphrag">1. GraphRAG</h1>
<h2 id="정리">정리</h2>
<ul>
<li>Microsoft Research에서 개발한 오픈 소스 프로젝트로, 기존의 일반적인 RAG(Baseline RAG)가 가진 한계를 극복하기 위해 <strong>지식 그래프(Knowledge Graph)</strong>와 <strong>거대언어모델(LLM)</strong>을 결합한 지능형 데이터 처리 및 검색 시스템</li>
</ul>
<h2 id="쿼리-엔진-종류">쿼리 엔진 종류</h2>
<ul>
<li>Basic Search (Baseline RAG): 그래프 구조 없이 단순 벡터 유사도로만 검색함</li>
<li>Global Search (전역 검색): &quot;이 데이터의 주요 테마는 무엇인가?&quot;와 같이 전체 데이터를 아우르는 추상적인 질문에 적합함. 미리 생성된 '커뮤니티 요약'을 활용해 답변 생성</li>
<li>Local Search (지역 검색): &quot;특정 인물 A와 B의 관계는?&quot;과 같이 특정 개체나 세부 사실에 대한 질문에 적합 지식 그래프의 노드와 인접 노드(이웃) 정보를 탐색하여 답변</li>
<li>DRIFT Search: 최근 추가된 모드로, 지역 검색의 정교함에 전역적인 커뮤니티 문맥을 결합하여 더욱 풍부하고 정확한 답변 도출</li>
</ul>
<hr />
<h1 id="2-ragas">2. RAGAS</h1>
<h2 id="a-정리">a. 정리</h2>
<ul>
<li>RAG(검색 증강 생성) 파이프라인의 성능을 정량적으로 평가하기 위해 설계된 오픈소스 프레임워크</li>
</ul>
<h2 id="b-평가-지표">b. 평가 지표</h2>
<h3 id="1-faithfulness충실도">1. Faithfulness(충실도)</h3>
<ul>
<li>생성된 <strong>응답(Response)</strong>이 <strong>검색된 컨텍스트(Context)</strong>와 얼마나 사실적으로 일관되는지를 측정함, 이 수치는 0에서 1 사이의 범위를 가지며, 점수가 높을수록 일관성이 뛰어남</li>
<li><code>Answer</code>, <code>Context</code> 비교</li>
</ul>
<h3 id="2-answer-relevancy답변-관련성">2. Answer Relevancy(답변 관련성)</h3>
<ul>
<li>생성된 <strong>응답(Response)</strong>이 <strong>질문(qusetion)</strong>과 얼마나 관련성이 있는지를 측정함 이 지표는 0에서 1 사이의 값을 가지며, 점수가 높을수록 사용자 입력과의 관련성이 높다는 것을 나타냄(질문 정확성 여부는 판단하지 않음)</li>
<li><code>Answer</code>, <code>Question</code> 비교</li>
</ul>
<h3 id="3-answer-correctness답변-정확도">3. Answer Correctness(답변 정확도)</h3>
<ul>
<li>생성된 답변(Generated Answer)이 실제 정답(Ground Truth)과 비교했을 때 얼마나 정확한지를 평가</li>
<li>Answer Correctness는 다음 두 가지 요소를 가중 평균하여 계산함</li>
<li>Semantic Similarity (의미적 유사성): 생성된 답변과 정답이 의미적으로 얼마나 비슷한지 측정 (주로 임베딩 모델을 사용하여 의미적 거리를 계산)</li>
<li>Factual Similarity (사실적 유사성): 답변에 포함된 개별 사실들이 정답과 얼마나 일치하는지를 측정</li>
</ul>
<hr />
<h1 id="3-graphrag를-이용한-llm-추론">3. GraphRAG를 이용한 LLM 추론</h1>
<ul>
<li>3090, 24GB VRAM 환경에서 진행<h2 id="a-지식-그래프-구축">a. 지식 그래프 구축</h2>
</li>
<li>분석하고자 하는 텍스트 파일을 LLM을 이용해 엔티티(Entity)와 관계(Relationship)를 추출하고, 커뮤니티(Community)를 구조화함</li>
<li>추출된 텍스트 유닛과 커뮤니티 요약본을 벡터 데이터베이스에 저장</li>
<li>실행 방법<pre><code class="language-python"># 0. 사용할 모델을 vllm을 이용하여 서빙
# 임베딩 모델
python -m vllm.entrypoints.openai.api_server \
  --model BAAI/bge-m3 --served-model-name bge-m3 \
  --port 8000 --gpu-memory-utilization 0.05 \
  --task embed --max-model-len 2048
</code></pre>
</li>
</ul>
<h1 id="llm-모델">llm 모델</h1>
<p>python -m vllm.entrypoints.openai.api_server <br />    --model unsloth/Qwen3-14B-unsloth-bnb-4bit 
    --served-model-name unsloth/Qwen3-14B-unsloth-bnb-4bit <br />    --port 8001 --gpu-memory-utilization 0.85 <br />    --max-model-len 16384</p>
<h1 id="1-작업환경-초기화env와-settingsyaml-파일-생성">1. 작업환경 초기화(<code>.env</code>와 <code>settings.yaml</code> 파일 생성)</h1>
<p>graphrag init --root ./graphrag</p>
<h1 id="2-프롬프트-튜닝">2. 프롬프트 튜닝</h1>
<h1 id="settingsyaml-설정-맞춰줘야-함">settings.yaml 설정 맞춰줘야 함</h1>
<p>graphrag prompt-tune --root ./graphrag --config ./graphrag/settings.yaml <br />    --language &quot;Korean&quot; --domain &quot;취업규칙 및 인사 관리 규정&quot; <br />    --output ./graphrag/prompts --discover-entity-types</p>
<h1 id="3-인덱싱">3. 인덱싱</h1>
<p>graphrag index --root ./graphrag</p>
<pre><code>## b. 파라미터 설정
### Chunk Size: 600 (텍스트 분할 크기)
- 원문 데이터를 어느 정도 길이로 자를 것인지 결정하는 단위
- 기본값은 1000이였지만 너무 많아 600으로 하향
### Chunk Overlap: 100 (중첩 구간)
- 앞 청크의 뒷부분 토큰을 다음 청크의 앞부분에 중복해서 포함시키는 단위
- 기본값 유지
### $k$: 1, 3, 5 (GraphRAG 엔진 및 검색 범위)
- 질문과 가장 유사한 텍스트 단위(Text Units)를 몇 개나 가져올지 결정하는 값
- $k$가 작을 때 ($k=1$): 답변의 순도가 높고 관련 없는 정보가 섞일(Context Bleeding) 확률이 낮아지지만, 정답이 여러 단락에 걸쳐 있을 경우 정보 누락 현상이 발생할 수 있음
- $k$가 클 때 ($k=3 \sim 5$): 여러 조항을 복합적으로 참조해야 하는 질문(예: 임신부 근로시간 단축)에 대해 더 논리적인 답변이 가능하지만, 연산 비용이 증가하고 노이즈가 섞일 위험 존재

## c. 지식그래프 시각화 예시
![](https://velog.velcdn.com/images/starcookie/post/c90ae0d6-36dd-4a31-bf1c-5c1bae27b453/image.png)

## d. Basic Search 쿼리 엔진을 활용하여 추론 진행(CLI)
- 여러가지 쿼리 엔진이 존재하지만, 파인튜닝 모델 평가가 주 목적이므로 작업 환경을 고려하여 Basic Search 엔진을 활용함
- Basic Search는 작성한 지식그래프 사용하지 않음(entity, Relationship)
- 나머지 엔진들은 LLM 사용 필요함
- CLI를 활용한 추론 방법
```python
graphrag query --root ./graphrag --method basic --query &quot;직원의 연차 휴가는 1년에 며칠인가요?&quot;</code></pre><h2 id="e-basic-search-쿼리-엔진을-활용하여-추론-진행python">e. Basic Search 쿼리 엔진을 활용하여 추론 진행(Python)</h2>
<h3 id="실행-배경">실행 배경</h3>
<ul>
<li><p>질문에 대한 답변 외에도 참조한 문맥(context) 데이터도 필요한데, d 과정에서는 답변(answer)만 출력됨</p>
</li>
<li><p>여러 모델과 여러 질문들을 한번에 추론하기 위해 자동화 스크립트 작성</p>
<h3 id="참고한-코드">참고한 코드</h3>
</li>
<li><p><a href="https://microsoft.github.io/graphrag/examples_notebooks/local_search/">https://microsoft.github.io/graphrag/examples_notebooks/local_search/</a></p>
</li>
<li><p><a href="https://github.com/microsoft/graphrag/tree/main/graphrag/query/structured_search/basic_search">https://github.com/microsoft/graphrag/tree/main/graphrag/query/structured_search/basic_search</a></p>
<h3 id="시스템-레이어">시스템 레이어</h3>
</li>
<li><p><strong>Engine Layer (basic_search.py)</strong>: GraphRAG 라이브러리를 활용한 검색 및 답변 생성 핵심 로직</p>
<pre><code class="language-python"># GraphRAG 기반 검색 엔진 초기화
...
class GraphRAGBasicEngine:
  def __init__(self, ...):
      # 1. LanceDB 벡터 스토어 연결 (GraphRAG 전용 테이블 로드)
      self.vector_store = DebugLanceDBVectorStore(collection_name=&quot;default-text_unit-text&quot;, ...)

      # 2. 로컬 vLLM 서버와 연결되는 Chat/Embedding 모델 설정
      chat_config = LanguageModelConfig(api_base=llm_api_base, model=llm_model, ...)
      chat_model = ModelManager().get_or_create_chat_model(name=llm_model, config=chat_config)

      # 3. BasicSearch 엔진 생성 (k값 및 토큰 제한 설정)
      self.search_engine = BasicSearch(
          model=chat_model,
          context_builder=context_builder,
          model_params={&quot;max_tokens&quot;: 2000, &quot;temperature&quot;: 0.0}, # 일관성을 위한 0.0 설정
          context_builder_params={&quot;max_context_tokens&quot;: 12000, &quot;k&quot;: 3}
      )
      ...</code></pre>
</li>
<li><p><strong>Evaluation Layer (batch_runner.py)</strong>: 데이터셋 로드, 추론 시간 측정, W&amp;B 로깅 및 결과 저장</p>
<pre><code class="language-python"># 평가 루프 및 W&amp;B 실시간 로깅
...
for item in dataset:
  start_time = time.perf_counter() # 추론 시간 측정 시작
  try:
      # 1. GraphRAG 엔진으로 답변 및 참조 컨텍스트 생성
      pred_answer, context, p_tokens, o_tokens = await engine.search(q)
      duration = time.perf_counter() - start_time

      # 2. W&amp;B에 실시간 메트릭 로깅 (지연시간, 토큰 효율 등)
      wandb.log({
          &quot;question&quot;: q,
          &quot;latency_sec&quot;: duration,
          &quot;tokens_per_sec&quot;: o_tokens / duration if duration &gt; 0 else 0
      })

      # 3. 평가 데이터셋 구성을 위한 결과 저장
      results.append({
          &quot;question&quot;: q,
          &quot;answer&quot;: pred_answer,
          &quot;ground_truth&quot;: gt,
          &quot;context&quot;: context,
      })
      ...</code></pre>
</li>
<li><p><strong>Automation Layer (run_basic_search.py)</strong>: vLLM 서버 생명주기 관리 및 모델별 순회 실행</p>
<pre><code class="language-python">...
# 모델별 vLLM 서버 자동 실행 로직
for config in MODEL_CONFIGS:
  # 1. 서버 프로세스 백그라운드 실행
  full_cmd = [&quot;python&quot;, &quot;-m&quot;, &quot;vllm.entrypoints.openai.api_server&quot;, &quot;--port&quot;, str(PORT)] + config[&quot;cmd_args&quot;]
  server_process = subprocess.Popen(full_cmd)

  try:
      # 2. 서버가 준비될 때까지 Health Check (최대 300초)
      if wait_for_server(SERVER_URL):
          # 3. 서버 준비 완료 시 평가 함수 호출
          asyncio.run(run_evaluation_task(config[&quot;name&quot;], PORT))
  finally:
      # 4. 평가 종료 후 프로세스 정지 및 VRAM 정리를 위한 대기
      server_process.terminate()
      time.sleep(10)
      ...</code></pre>
<h3 id="실행-흐름">실행 흐름</h3>
</li>
</ul>
<ol>
<li><strong>모델 설정 정의</strong>: 테스트할 모델 리스트와 vLLM 실행 옵션을 설정</li>
<li><strong>서버 기동</strong>: 첫 번째 모델을 vLLM 인스턴스로 서빙</li>
<li><strong>엔진 초기화</strong>: 해당 서버 주소에 맞춰 GraphRAG 엔진을 연결</li>
<li><strong>배치 추론</strong>: 질문 데이터셋을 순회하며 답변을 생성하고 W&amp;B에 기록</li>
<li><strong>결과 저장</strong>: 로컬에 CSV와 JSON 형태로 최종 리포트를 생성</li>
<li><strong>정리 및 반복</strong>: 서버를 종료하고 다음 모델로 이동하여 2번부터 반복</li>
</ol>
<hr />
<h1 id="4-ragas를-이용한-llm-정량적-평가">4. RAGAS를 이용한 LLM 정량적 평가</h1>
<h2 id="a-사용한-지표">a. 사용한 지표</h2>
<ul>
<li><p><strong>RAGAS를 사용하는 주된 목적이 파인튜닝된 모델 VS 파인튜닝 안한 모델 평가이기 때문에 문맥을 평가하는 지표는 제외함)</strong></p>
</li>
<li><p>Faithfulness(답변의 문맥 충실도): <code>Answer</code>, <code>Context</code> 비교</p>
</li>
<li><p>Answer Relevancy(답변의 질문 관련성): <code>Answer</code>, <code>Question</code> 비교</p>
</li>
<li><p>Answer Accuracy(질문에 대한 답변과 정답 사이의 일치도): <code>Answer</code>, <code>Ground Truth</code> 비교</p>
<h2 id="b-스크립트-작성">b. 스크립트 작성</h2>
<h3 id="작성-배경">작성 배경</h3>
</li>
<li><p>여러 모델과 여러 질문들을 한번에 평가하기 위해 자동화 스크립트 작성</p>
<h3 id="참고한-코드-1">참고한 코드</h3>
</li>
<li><p><a href="https://docs.ragas.io/en/stable/concepts/metrics/available_metrics/faithfulness/">https://docs.ragas.io/en/stable/concepts/metrics/available_metrics/faithfulness/</a></p>
<h3 id="시스템-레이어-1">시스템 레이어</h3>
</li>
<li><p><strong>Ragas 기반 정량 평가 (ragas_test.py)</strong></p>
<pre><code class="language-python">...
# Ragas 평가 지표 설정 및 실행
metrics = [
  Faithfulness(llm=llm), # 답변의 근거 충실도
  AnswerRelevancy(llm=llm, embeddings=embeddings), # 질문과의 관련성
  AnswerCorrectness(llm=llm) # 정답과의 정확도
]
result = evaluate(dataset=ragas_dataset, metrics=metrics, ...) # 평가 실행
...</code></pre>
</li>
<li><p><strong>평가 자동화 루프(run_ragas_test.py)</strong></p>
<pre><code class="language-python">...
# 모든 실험 결과에 대해 Ragas 평가 자동화
for i, combo in enumerate(combinations):
  params = dict(zip(keys, combo))
  # ragas_test.py를 서브프로세스로 호출하여 순차적 평가 진행
  command = [
      &quot;python&quot;, &quot;ragas_test.py&quot;,
      &quot;--model_name&quot;, params['model_name'],
      &quot;--judge_model&quot;, params['judge_model'],
      &quot;--prompt_type&quot;, params['prompt_type']
  ]
  subprocess.run(command, check=True) # 일괄 실행
   ...</code></pre>
<h2 id="c-평가-결과">c. 평가 결과</h2>
<h3 id="지표별-비교">지표별 비교</h3>
<h4 id="ㄱ-답변-정확도-avg_answer_correctness">ㄱ. 답변 정확도 (Avg_Answer_Correctness):</h4>
<p><img alt="" src="https://velog.velcdn.com/images/starcookie/post/5d8533e8-f2bd-49b4-960b-f1b2d96b80b5/image.png" /></p>
</li>
<li><p><strong>8B 16bit 파인튜닝 모델(r32)</strong>이 0.7205로 전 모델 중 1위를 기록</p>
</li>
<li><p><strong>14B 4bit 파인튜닝 모델(r8)</strong>은 0.6747</p>
</li>
<li><p><strong>4B 4bit 파인튜닝 모델(r8)</strong>은 0.6610으로, 체급이 30B 모델보다 높은 정확도를 기록</p>
</li>
<li><p>30B Coder 모델은 0.5472에 그쳐, 파인튜닝된 소형 모델들에 비해 정확도가 낮게 측정됨</p>
</li>
<li><p>파인튜닝으로 비슷한 문맥 및 답변을 학습했기 때문에 점수가 높게 나온걸로 예상</p>
</li>
</ul>
<h4 id="ㄴ-지연-시간-avg_latency">ㄴ. 지연 시간 (Avg_Latency):</h4>
<p><img alt="" src="https://velog.velcdn.com/images/starcookie/post/0d27ff29-fa89-448c-b918-74a800e8ce7d/image.png" /></p>
<ul>
<li>8B 4bit 파인튜닝(r8) 모델이 2.3464초로 응답 속도가 가장 빠름</li>
<li>4B 4bit 파인튜닝(r32) 모델이 2.4599초로 응답 속도가 기록됨</li>
<li>14B 4bit 파인튜닝(r32) 모델은 10.8275초가 소요되어, 동일 체급 r8 설정보다 느려짐</li>
<li>30B Coder 모델은 8.5571초로, 파인튜닝을 하지 않은 모델들보다 latency가 낮음</li>
<li>공통적으로 파인튜닝을 진행한 모델들이 진행하지 않은 모델들보다 추론 속도가 빠른 경향을 보임</li>
</ul>
<h4 id="ㄷ-충실도-및-답변-관련성-faithfulness--relevancy">ㄷ. 충실도 및 답변 관련성 (Faithfulness &amp; Relevancy):</h4>
<p><img alt="" src="https://velog.velcdn.com/images/starcookie/post/e507a3ed-e7b1-4f2a-a1ba-09d2d9bfc7e9/image.png" /></p>
<ul>
<li>충실도: 8B 16bit 파인튜닝(r8) 모델이 0.9194로 가장 높으며, ground truth와 answer 간의 관련성이 높음(환각 여부 검증)</li>
</ul>
<p><img alt="" src="https://velog.velcdn.com/images/starcookie/post/9b104f3b-daa7-4c70-8c16-3e890c4fc0a5/image.png" /></p>
<ul>
<li>답변 관련성: 8B 4bit 파인튜닝(r32) 모델이 0.3250으로 answer와 question 사이 일치도가 가장 높음(질문의 의도에 맞게 잘 답변했는지 여부 검증)</li>
</ul>
<h4 id="ㄹ-파인튜닝lora-적용-여부에-따른-차이">ㄹ. 파인튜닝(LoRA) 적용 여부에 따른 차이</h4>
<ol>
<li>답변 정확도 향상:</li>
</ol>
<ul>
<li>베이스 모델 대비 파인튜닝시 정확도가 상승함</li>
<li>모든 모델에서 공통적인 특성을 보임</li>
<li>파인튜닝 적용되지 않은 모델들의 answer 길이가 길어서 생긴 현상이라고 생각</li>
</ul>
<ol start="2">
<li>추론 속도의 개선:</li>
</ol>
<ul>
<li>8B 모델은 베이스(19.0545초)에서 파인튜닝(2.3464초) 적용 시 추론 속도가 감소됨</li>
<li>모든 모델에서 공통적인 특성을 보임<h4 id="ㅁ-지표-평균-그래프">ㅁ. 지표 평균 그래프</h4>
<img alt="" src="https://velog.velcdn.com/images/starcookie/post/4224fa57-24cc-43b8-adeb-082d2c9472a9/image.png" /><h4 id="ㅂ-추론-속도-및-지표-평균-그래프">ㅂ. 추론 속도 및 지표 평균 그래프</h4>
<img alt="" src="https://velog.velcdn.com/images/starcookie/post/1a960902-a3cc-46f7-8912-ef9b93fc8dd9/image.png" /></li>
</ul>