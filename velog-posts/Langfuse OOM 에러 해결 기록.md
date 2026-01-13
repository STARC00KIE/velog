<h1 id="1-현재-서버에-langfuse로-opewebui-모니터링-하고-있지만-oomout-of-memory-에러-발생">1. 현재 서버에 Langfuse로 OpewebUI 모니터링 하고 있지만 OOM(Out Of Memory) 에러 발생</h1>
<hr />
<h1 id="2-코드-수정할-수-없는-상황이므로-다음과-같은-방법으로-해결">2. 코드 수정할 수 없는 상황이므로 다음과 같은 방법으로 해결</h1>
<pre><code class="language-bash"># 1. 서버 접속 및 langfuse 폴더 진입

# 2. docker-compose 내리기
docker compose down

# 3. docker-compose 실행
docker compose up -d

# 4. 실행 잘 되고 있는지 확인
docker logs -f {CONTAINER_ID}</code></pre>
<hr />
<h1 id="3-추가-truncate-명령어-이용하여-메모리-정리-방법">3. 추가: TRUNCATE 명령어 이용하여 메모리 정리 방법</h1>
<pre><code class="language-bash"># 1. 도커 컨테이너 내부로 들어가서 SQL 쿼리 날릴수 있게 터미널 오픈
sudo docker exec -it langfuse-clickhouse-1 clickhouse-client</code></pre>
<pre><code class="language-sql"># 다음 명령어 복붙하여 시스템 log 데이터 삭제

TRUNCATE TABLE system.trace_log;
TRUNCATE TABLE system.text_log;
TRUNCATE TABLE system.metric_log;
TRUNCATE TABLE system.asynchronous_metric_log;
TRUNCATE TABLE system.query_log;
TRUNCATE TABLE system.part_log;
TRUNCATE TABLE system.opentelemetry_span_log;
TRUNCATE TABLE system.processors_profile_log;
TRUNCATE TABLE system.query_views_log;</code></pre>