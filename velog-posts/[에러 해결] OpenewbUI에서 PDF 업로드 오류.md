<h2 id="오류-메시지">오류 메시지</h2>
<ul>
<li><strong>PDF 업로드할 때 에러 발생</strong><pre><code class="language-bash">Unexpected token '&lt;', &quot;&lt;html&gt; &lt;h&quot;... is not valid JSON</code></pre>
</li>
</ul>
<hr />
<h2 id="발견한-오류-원인">발견한 오류 원인</h2>
<ul>
<li><code>nginx</code>의 <code>/api</code> location에 <code>client_max_body_size</code> 설정 누락</li>
<li>기본값 1MB 제한으로 인한 업로드 실패</li>
<li>HTML 오류 페이지가 JSON으로 파싱되며 발생한 오류</li>
</ul>
<hr />
<h2 id="nginx-설정-비교">nginx 설정 비교</h2>
<ul>
<li><code>/</code> location: 5MB 허용<pre><code class="language-yaml">location / {
  client_max_body_size 5M;
  ...}</code></pre>
</li>
<li><code>/api</code> location: 설정 없음 (1MB 기본값)</li>
</ul>
<hr />
<h2 id="에러-해결-방법">에러 해결 방법</h2>
<ul>
<li><code>/api</code> location: 설정에 <code>client_max_body_size 5M;</code> 추가</li>
</ul>