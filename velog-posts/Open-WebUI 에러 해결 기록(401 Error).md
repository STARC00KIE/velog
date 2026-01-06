<h1 id="에러상황">에러상황</h1>
<ul>
<li>Open-webui에서 Anthropic 계열 모델에 질의했을 때 401 에러 발생
<img alt="" src="https://velog.velcdn.com/images/starcookie/post/cb7bf372-4cee-4ebd-b4ff-e2472fde40e5/image.png" /></li>
</ul>
<h1 id="해결-과정">해결 과정</h1>
<h2 id="1-api-key-유효성-여부-확인">1. API-KEY 유효성 여부 확인</h2>
<ul>
<li>직접 API-KEY를 불러왔을 때 모델이 잘 작동함을 확인함</li>
<li>문제 원인 아님<h2 id="2-모델-지원-종료-여부-확인">2. 모델 지원 종료 여부 확인</h2>
</li>
<li>claude 3 계열 모델들이 지원 종료됨</li>
<li>문제 원인 아님<h2 id="3-open-webuipipelines-레포지토리에서-파이프라인-스크립트-다시-등록">3. open-webui/pipelines 레포지토리에서 파이프라인 스크립트 다시 등록</h2>
</li>
<li><a href="https://github.com/open-webui/pipelines/tree/main/examples/pipelines/providers">https://github.com/open-webui/pipelines/tree/main/examples/pipelines/providers</a></li>
<li>적용 후 새로고침 결과 정상적으로 작동함</li>
</ul>