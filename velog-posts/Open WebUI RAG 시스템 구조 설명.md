<h1 id="open-webui-rag-시스템-구조-설명">Open WebUI RAG 시스템 구조 설명</h1>
<p>Open WebUI의 RAG(Retrieval-Augmented Generation) 시스템은 <code>/backend/open_webui/retrieval/</code> 디렉토리에 구현되어 있으며, 4개의 주요 컴포넌트로 구성됩니다:</p>
<h2 id="1-vector-벡터-데이터베이스"><strong>1. Vector (벡터 데이터베이스)</strong></h2>
<p><strong>경로</strong>: <code>retrieval/vector/</code></p>
<h3 id="지원하는-벡터-db-11종">지원하는 벡터 DB (11종):</h3>
<ul>
<li><strong>Chroma</strong> (기본값)</li>
<li><strong>Qdrant</strong></li>
<li><strong>Milvus</strong></li>
<li><strong>Pinecone</strong></li>
<li><strong>OpenSearch</strong></li>
<li><strong>PgVector</strong> (PostgreSQL)</li>
<li><strong>OpenGauss</strong></li>
<li><strong>Elasticsearch</strong></li>
<li><strong>Oracle23ai</strong></li>
<li><strong>Weaviate</strong></li>
<li><strong>S3Vector</strong></li>
</ul>
<h3 id="주요-기능">주요 기능:</h3>
<ul>
<li>벡터 삽입/업데이트/삭제</li>
<li>유사도 검색 (similarity search)</li>
<li>메타데이터 필터링</li>
<li>Collection 관리</li>
</ul>
<h2 id="2-loaders-문서-로더"><strong>2. Loaders (문서 로더)</strong></h2>
<p><strong>경로</strong>: <code>retrieval/loaders/</code></p>
<h3 id="지원-형식">지원 형식:</h3>
<ul>
<li><strong>YouTube</strong>: 비디오 자막 추출</li>
<li><strong>Tavily</strong>: 웹 검색 엔진 통합</li>
<li><strong>External Web</strong>: 일반 웹페이지</li>
<li><strong>External Document</strong>: 외부 문서</li>
<li><strong>Mistral</strong>: Mistral AI 통합</li>
<li><strong>Datalab Marker</strong>: 문서 마커</li>
<li><strong>MinerU</strong>: 문서 처리</li>
</ul>
<h2 id="3-web-웹-검색"><strong>3. Web (웹 검색)</strong></h2>
<p><strong>경로</strong>: <code>retrieval/web/</code></p>
<h3 id="지원-검색-엔진">지원 검색 엔진:</h3>
<ul>
<li>Google PSE, Bing, DuckDuckGo</li>
<li>Brave, Kagi, Perplexity</li>
<li>SearXNG, YaCy, Mojeek</li>
<li>Serper, SerpAPI, SearchAPI</li>
<li>Tavily, Jina Search</li>
<li>Azure Search, Ollama Search</li>
<li>외부 API</li>
</ul>
<h2 id="4-models-재순위-모델"><strong>4. Models (재순위 모델)</strong></h2>
<p><strong>경로</strong>: <code>retrieval/models/</code></p>
<ul>
<li><strong>ColBERT</strong>: 컨텍스트 기반 재순위</li>
<li><strong>Base Reranker</strong>: 기본 재순위 모델</li>
<li><strong>External</strong>: 외부 재순위 API</li>
</ul>
<h2 id="핵심-기능-utilspy"><strong>핵심 기능 (<code>utils.py</code>)</strong></h2>
<h3 id="embedding-생성"><strong>Embedding 생성</strong>:</h3>
<ul>
<li>OpenAI/Azure OpenAI embeddings</li>
<li>Ollama embeddings</li>
<li>Sentence Transformers (로컬)</li>
<li>배치 처리 및 비동기 지원</li>
</ul>
<h3 id="검색-방식"><strong>검색 방식</strong>:</h3>
<ol>
<li><p><strong>Vector Search</strong>: 임베딩 기반 유사도 검색</p>
</li>
<li><p><strong>Hybrid Search</strong>: BM25 + Vector Search 결합</p>
<ul>
<li>BM25: 키워드 기반 검색</li>
<li>Weight 조정 가능 (하이브리드 밸런스)</li>
</ul>
</li>
<li><p><strong>Enriched Texts</strong>: 메타데이터 강화 검색</p>
<ul>
<li>파일명, 제목, 섹션 헤딩 포함</li>
</ul>
</li>
</ol>
<h3 id="reranking-재순위"><strong>Reranking (재순위)</strong>:</h3>
<ul>
<li>검색 결과를 쿼리와의 관련성으로 재정렬</li>
<li>Score threshold 설정 가능</li>
<li>Top-K 결과 선택</li>
</ul>
<h3 id="데이터-소스"><strong>데이터 소스</strong>:</h3>
<ul>
<li>파일 (PDF, DOCX 등)</li>
<li>웹 URL</li>
<li>YouTube 비디오</li>
<li>채팅 이력</li>
<li>노트</li>
<li>Knowledge Base (컬렉션)</li>
</ul>
<h2 id="rag-워크플로우"><strong>RAG 워크플로우</strong></h2>
<pre><code class="language-javascript">1. 문서 업로드/URL 입력
   ↓
2. Loader로 텍스트 추출
   ↓
3. 청크 분할 (Chunking)
   ↓
4. Embedding 생성
   ↓
5. Vector DB에 저장
   ↓
6. 사용자 쿼리 → Embedding
   ↓
7. Vector/Hybrid Search
   ↓
8. Reranking (선택적)
   ↓
9. 상위 K개 결과 반환
   ↓
10. LLM에 컨텍스트로 전달</code></pre>