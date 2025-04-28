<h2 id="개념-정리">개념 정리</h2>
<hr />
<ul>
<li>선입후출, FILO(First In Last Out)</li>
<li>삽입: push, 추출: pop</li>
<li>스택의 ADT(abstract data type)<ol>
<li>연산: push, isFull, isEmpty, PoP<ol start="2">
<li>상태: top, ItemType data [maxsize]</li>
</ol>
</li>
</ol>
</li>
<li>top: 최근에 삽입한 데이터 위치를 저장할 변수</li>
<li>ItemType data [maxsize]: 스택의 데이터를 관리하는 변수</li>
<li>Index 범위: 0 ~ maxsize-1</li>
<li>데이터가 하나도 없을 때: top = -1</li>
<li>데이터가 하나 있을 때: top = 0</li>
</ul>
<h2 id="구현-예시">구현 예시</h2>
<hr />
<ol>
<li><p>push(3) 연산</p>
<ul>
<li>isFull 수행(데이터가 꽉 차있는지 확인함)</li>
<li>데이터가 다 차있지 않으면 top이 1 증가(top(-1) -&gt; top(0)</li>
<li>top이 가리키는 위치에 3 추가</li>
</ul>
</li>
<li><p>pop() 연산</p>
<ul>
<li>isEmpty 수행(데이터가 하나도 없는지 확인함)</li>
<li>하나라도 있을 때 top 1 감소(top(0) -&gt; top(-1)</li>
<li>데이터 3 반환</li>
</ul>
</li>
</ol>
<h2 id="구현-방법">구현 방법</h2>
<hr />
<ul>
<li>파이썬의 리스트는 크기를 동적으로 관리하므로 max_size, isFull, isEmpty 함수는 구현하지 않아도 됨</li>
<li>append, pop 함수를 이용하여 스택 문제 해결</li>
<li>데이터를 그냥 저장하고 순서와 상관없이 임의로 접근할 때는 배열을 사용함</li>
<li>반대로 최근에 삽입한 데이터를 대상을 뭔가 연산해야 할 때 스택을 사용함</li>
<li>스택 관련 코딩테스트를 준비할 때 스택이 비었을 경우를 항상 고려하며 문제 해결하기</li>
</ul>