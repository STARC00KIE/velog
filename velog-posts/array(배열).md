<h1 id="배열">배열</h1>
<ul>
<li>같은 타입의 변수들로 이루어진 집합으로 메모리의 연속공간에 값이 채워져 있는 형태의 자료구조</li>
<li>장점: 검색 성능이 좋음, 인덱스를 사용하여 원소에 바로 접근할 수 있음</li>
<li>단점: 메모리 활용에 비효율적임, 값의 삽입과 삭제에서 비효율적임. 데이터의 중간 지점에서 자료의 삽입 삭제가 일어날 경우 다음 항목의 모든 값을 이동시켜야만 함</li>
</ul>
<hr />
<h1 id="연결-리스트linked-list">연결 리스트(linked list)</h1>
<ul>
<li>값과 주소를 묶은 노드를 주소로 연결한 자료구조</li>
<li>장점: 값을 삽입하거나 삭제하는 연산의 속도가 빠름, 선언할 때 크기를 별도로 지정하지 않고 주소로 계속 연결해 나가며, 연속된 공간이 필요하지 않아 빈 공간을 활용할 수 있어 메모리 활용이 효율적임</li>
<li>단점: 리스트 원소로 바로 접근이 불가능함, Head 주소부터 차례대로 순차접근을 해야 함</li>
</ul>
<hr />
<h1 id="deque">deque</h1>
<ul>
<li>자료구조의 왼쪽 부분과 오른쪽 부분, 즉 양쪽 모두에서 자료의 삽입과 삭제가 가능한 자료구조</li>
<li>deque는 따로 정렬하는 함수가 없음</li>
<li><code>from collections import deque</code> 로 불러와서 사용</li>
<li>append(): deque의 오른쪽 부분에 자료 추가</li>
<li>appendleft(): deque의 왼쪽 부분에 자료 추가</li>
<li>popleft(): deque의 맨 왼쪽 자료 제거</li>
<li>pop(): deque의 맨 오른쪽 제거</li>
</ul>
<h1 id="deque-추가-함수들">deque 추가 함수들</h1>
<table>
<thead>
<tr>
<th align="left">함수</th>
<th align="left">실행시간</th>
<th align="left">설명</th>
</tr>
</thead>
<tbody><tr>
<td align="left">append(x)</td>
<td align="left">O(1)</td>
<td align="left">데크의 오른쪽에 x를 추가</td>
</tr>
<tr>
<td align="left">appendleft(x)</td>
<td align="left">O(1)</td>
<td align="left">데크의 왼쪽에 x를 추가</td>
</tr>
<tr>
<td align="left">clear()</td>
<td align="left">O(1)</td>
<td align="left">데크에서 모든 요소를 제거하고 길이가 0인 상태로 만듦</td>
</tr>
<tr>
<td align="left">copy()</td>
<td align="left">O(N)</td>
<td align="left">데크의 얕은 복사본을 만듦</td>
</tr>
<tr>
<td align="left">count(x)</td>
<td align="left">O(N)</td>
<td align="left">x 와 같은 데크 요소의 수를 셈</td>
</tr>
<tr>
<td align="left">extend(iterable)</td>
<td align="left">O(K)</td>
<td align="left">iterable 인자에서 온 요소를 추가하여 데크의 오른쪽을 확장</td>
</tr>
<tr>
<td align="left">extendleft(iterable)</td>
<td align="left">O(K)</td>
<td align="left">iterable에서 온 요소를 추가하여 데크의 왼쪽을 확장 일련의 왼쪽 추가는 iterable 인자에 있는 요소의 순서를 뒤집는 결과 반환</td>
</tr>
<tr>
<td align="left">index(x[, start[, stop]])</td>
<td align="left">O(N)</td>
<td align="left">데크에 있는 x의 위치를 반환 (인덱스 start 또는 그 이후, 그리고 인덱스 stop 이전). 첫 번째 일치를 반환하거나 찾을 수 없으면 ValueError를 발생</td>
</tr>
<tr>
<td align="left">insert(i, x)</td>
<td align="left">O(N)</td>
<td align="left">x를 데크의 i 위치에 삽입 삽입으로 인해 제한된 길이의 데크가 maxlen 이상으로 커지면, IndexError가 발생</td>
</tr>
<tr>
<td align="left">pop()</td>
<td align="left">O(1)</td>
<td align="left">데크의 오른쪽에서 요소를 제거하고 반환 요소가 없으면, IndexError를 발생</td>
</tr>
<tr>
<td align="left">popleft()</td>
<td align="left">O(1)</td>
<td align="left">데크의 왼쪽에서 요소를 제거하고 반 요소가 없으면, IndexError를 발생</td>
</tr>
<tr>
<td align="left">remove(value)</td>
<td align="left">O(N)</td>
<td align="left">value의 첫 번째 항목을 제거 찾을 수 없으면, ValueError를 발생</td>
</tr>
<tr>
<td align="left">reverse()</td>
<td align="left">O(N)</td>
<td align="left">데크의 요소들을 제자리에서 순서를 뒤집고 None을 반환</td>
</tr>
<tr>
<td align="left">rotate(n=1)</td>
<td align="left">O(K)</td>
<td align="left">데크를 n 단계 오른쪽으로 회전 n이 음수이면, 왼쪽으로 회전 데크가 비어 있지 않으면, 오른쪽으로 한 단계 회전하는 것은 d.appendleft(d.pop())과 동등하고, 왼쪽으로 한 단계 회전하는 것은 d.append(d.popleft())와 동등</td>
</tr>
<tr>
<td align="left">maxlen</td>
<td align="left"></td>
<td align="left">데크의 최대 크기 또는 제한이 없으면 None.</td>
</tr>
</tbody></table>