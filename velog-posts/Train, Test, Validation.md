<h1 id="1-기존의-머신러닝-딥러닝">1. 기존의 머신러닝, 딥러닝</h1>
<ul>
<li>Train: 장답과 예측값이 오차를 줄임</li>
<li>Validation: 학습 중 성능이 떨어지면 학습 중지(Early Stopping)</li>
<li>Test: 정담과 일치하는지 확인</li>
</ul>
<h1 id="2llm">2.LLM</h1>
<ul>
<li>Train: 다음 단어(Token)가 나올 확률을 높임</li>
<li>Validation: 손실값이 급격하게 변하면 중단</li>
<li>Test: 답변이 문맥상 자영스러운지 정성 평가</li>
</ul>
<h1 id="기존-방식과-다른-점">기존 방식과 다른 점</h1>
<ul>
<li>기존 방식은 <code>Test dataset</code>에 대해 맞다, 틀리다로 2분법적으로 나눌 수 있었음</li>
<li>하지만 LLM과 같은 생성형 모델의 경우, 단순하게 비교하는 방식으로는 정확히 평가 불가</li>
<li>따라서 다른 평가 방식을 진행하게 됨</li>
<li><code>eval_dataset</code>을 지정하여 에포크마다 loss가 줄어드는지 확인하는 방식 사용</li>
</ul>
<h2 id="평가-진행-방법">평가 진행 방법</h2>
<ul>
<li><a href="https://velog.io/@starcookie/%EC%BB%A4%EC%8A%A4%ED%85%80-%EB%8D%B0%EC%9D%B4%ED%84%B0%EC%85%8B%EC%9C%BC%EB%A1%9C-%ED%8C%8C%EC%9D%B8%ED%8A%9C%EB%8B%9D%EB%90%9C-LLM-%ED%8F%89%EA%B0%80-%EB%B0%A9%EB%B2%95">https://velog.io/@starcookie/%EC%BB%A4%EC%8A%A4%ED%85%80-%EB%8D%B0%EC%9D%B4%ED%84%B0%EC%85%8B%EC%9C%BC%EB%A1%9C-%ED%8C%8C%EC%9D%B8%ED%8A%9C%EB%8B%9D%EB%90%9C-LLM-%ED%8F%89%EA%B0%80-%EB%B0%A9%EB%B2%95</a></li>
</ul>