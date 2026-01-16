<h2 id="에러-증상">에러 증상</h2>
<ul>
<li><strong>발생 일시</strong>: 2026-01-16</li>
<li><strong>에러 메시지</strong>: Internal Server Error</li>
<li><strong>API 엔드포인트</strong>: <code>traces.byId</code></li>
<li><strong>영향</strong>: 특정 trace 조회 시 &quot;Internal Server Error&quot; 발생
<img alt="" src="https://velog.velcdn.com/images/starcookie/post/fc79b9c1-cb23-4df2-98b2-75ac4f5cbb41/image.png" /></li>
</ul>
<hr />
<h2 id="에러-원인-분석">에러 원인 분석</h2>
<p><strong>1. 로그 분석</strong></p>
<pre><code class="language-bash">docker compose logs langfuse-web | grep &quot;traces.byId&quot;</code></pre>
<p><strong>- 발견된 에러</strong></p>
<pre><code class="language-bash">middleware intercepted error with code INTERNAL_SERVER_ERROR 
Attempt to read after eof: (while reading column metadata): 
(while reading from part /var/lib/clickhouse/
in table default.traces) 
located on disk default of type local, from mark 0 with max_rows_to_read = 1, offset = 172</code></pre>
<p><strong>2. 근본 원인</strong></p>
<ul>
<li>ClickHouse 데이터 파트 파일 손상</li>
<li><strong>에러 타입</strong>: <code>ATTEMPT_TO_READ_AFTER_EOF</code></li>
</ul>
<hr />
<h2 id="해결-방법">해결 방법</h2>
<ul>
<li>손상된 파트 분리(DETACH)<pre><code class="language-bash">docker compose exec clickhouse clickhouse-client --query \
&quot;ALTER TABLE default.traces DETACH PART '202601_...&quot;</code></pre>
</li>
</ul>