<h1 id="참고한-글">참고한 글</h1>
<p><a href="https://docs.openwebui.com/getting-started/quick-start">https://docs.openwebui.com/getting-started/quick-start</a></p>
<hr />
<h1 id="도커로-설치-및-실행하는-방법">도커로 설치 및 실행하는 방법</h1>
<h2 id="1-이미지-가져오기">1. 이미지 가져오기</h2>
<pre><code class="language-bash"># OpenWebUI에서 최신 도커 이미지 가져오기 (기본 버전)
docker pull ghcr.io/open-webui/open-webui:main</code></pre>
<h2 id="2-컨테이너-실행">2. 컨테이너 실행</h2>
<pre><code class="language-bash"># GPU를 사용하는 경우 실행하기 위해 다음 명령어로 컨터이너 실행
docker run -d -p 3000:8080 --gpus all -v open-webui:/app/backend/data --name open-webui ghcr.io/open-webui/open-webui:cuda

# 여러 사람이 사용하지 않고 혼자 사용하고 싶을 때(로그인 생략) 다음 명령어로 컨테이너 실행
docker run -d -p 3000:8080 -e WEBUI_AUTH=False -v open-webui:/app/backend/data --name open-webui ghcr.io/open-webui/open-webui:main</code></pre>
<h2 id="3-결과-확인">3. 결과 확인</h2>
<pre><code class="language-html"># 작성한 포트(3000)로 접속 가능한지 확인
http://localhost:3000</code></pre>
<p><img alt="" src="https://velog.velcdn.com/images/starcookie/post/8a634b6e-c4ea-40f4-962d-f6a398d6f64f/image.png" /></p>
<ul>
<li>시작하기 클릭한 후 계성 생성하면 접속 완료
<img alt="" src="https://velog.velcdn.com/images/starcookie/post/d934aacf-bdd8-423b-b983-b88aab477c39/image.png" /></li>
</ul>