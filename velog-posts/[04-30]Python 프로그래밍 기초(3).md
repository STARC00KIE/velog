<h1 id="문자열">문자열</h1>
<ul>
<li>문자의 집합을 의미하며, 텍스트 데이터를 다룰 때 매우 중요함</li>
<li>문자열을 위치에서 업데이트 되지 않음 예)<code>str[0] = &quot;a&quot;</code></li>
<li><table>
<thead>
<tr>
<th>항목</th>
<th>설명</th>
</tr>
</thead>
<tbody><tr>
<td>정의</td>
<td>하나 이상의 문자(character)가 나열된 데이터</td>
</tr>
<tr>
<td>자료형</td>
<td><code>str</code> (string)</td>
</tr>
<tr>
<td>표현 방법</td>
<td>작은따옴표 <code>'Hello'</code>, 큰따옴표 <code>&quot;Hello&quot;</code> 모두 가능</td>
</tr>
<tr>
<td>불변성</td>
<td>문자열은 <strong>immutable(변경 불가)</strong> 자료형 – 수정 불가, 새로 만들어야 함</td>
</tr>
</tbody></table>
</li>
<li><strong>주요 메서드</strong></li>
<li><table>
<thead>
<tr>
<th>메서드</th>
<th>설명</th>
<th>예시</th>
</tr>
</thead>
<tbody><tr>
<td><code>.lower()</code></td>
<td>소문자 변환</td>
<td><code>&quot;HELLO&quot;.lower()</code> → <code>'hello'</code></td>
</tr>
<tr>
<td><code>.upper()</code></td>
<td>대문자 변환</td>
<td><code>&quot;hi&quot;.upper()</code> → <code>'HI'</code></td>
</tr>
<tr>
<td><code>.strip()</code></td>
<td>공백 제거</td>
<td><code>&quot;  hello  &quot;.strip()</code> → <code>'hello'</code></td>
</tr>
<tr>
<td><code>.replace(a, b)</code></td>
<td>a를 b로 대체</td>
<td><code>&quot;apple&quot;.replace(&quot;p&quot;, &quot;b&quot;)</code> → <code>'abble'</code></td>
</tr>
<tr>
<td><code>.split()</code></td>
<td>문자열 나누기</td>
<td><code>&quot;a,b,c&quot;.split(&quot;,&quot;)</code> → <code>['a', 'b', 'c']</code></td>
</tr>
<tr>
<td><code>.join()</code></td>
<td>리스트를 문자열로</td>
<td><code>&quot;,&quot;.join(['a', 'b'])</code> → <code>'a,b'</code></td>
</tr>
<tr>
<td><code>.find()</code> / <code>.index()</code></td>
<td>위치 반환</td>
<td><code>&quot;hello&quot;.find(&quot;e&quot;)</code> → <code>1</code></td>
</tr>
<tr>
<td><code>.startswith()</code> / <code>.endswith()</code></td>
<td>시작/끝 확인</td>
<td><code>&quot;hi&quot;.startswith(&quot;h&quot;)</code> → <code>True</code></td>
</tr>
</tbody></table>
</li>
</ul>
<hr />
<h1 id="튜플">튜플</h1>
<ul>
<li>리스트와 동일하지만 크기와 값을 바꿀 수 있음</li>
<li>튜플(tuple)은 여러 개의 값을 하나로 묶는 자료형이며, 리스트와 비슷하지만 <strong>수정할 수 없다는 점(불변성)</strong>이 가장 큰 차이</li>
<li><table>
<thead>
<tr>
<th>항목</th>
<th>설명</th>
</tr>
</thead>
<tbody><tr>
<td>자료형</td>
<td><code>tuple</code></td>
</tr>
<tr>
<td>표기법</td>
<td>소괄호 <code>()</code> 사용: <code>t = (1, 2, 3)</code></td>
</tr>
<tr>
<td>특징</td>
<td>순서 있음, <strong>수정 불가</strong>, 중복 허용</td>
</tr>
<tr>
<td>용도</td>
<td>리스트보다 <strong>변경이 없어야 할 데이터</strong> 저장에 적합 (예: 좌표, RGB, DB row 등)</td>
</tr>
</tbody></table>
</li>
<li>주요 메서드</li>
<li><table>
<thead>
<tr>
<th>함수/메서드</th>
<th>설명</th>
</tr>
</thead>
<tbody><tr>
<td><code>len(t)</code></td>
<td>튜플 길이 반환</td>
</tr>
<tr>
<td><code>t.count(x)</code></td>
<td>x의 개수 세기</td>
</tr>
<tr>
<td><code>t.index(x)</code></td>
<td>x의 첫 인덱스 반환</td>
</tr>
<tr>
<td><code>tuple(iterable)</code></td>
<td>반복 가능한 객체 → 튜플로 변환</td>
</tr>
</tbody></table>
</li>
</ul>
<hr />
<h1 id="튜플과-리스트-비교">튜플과 리스트 비교</h1>
<table>
<thead>
<tr>
<th>구분</th>
<th>튜플 (<code>tuple</code>)</th>
<th>리스트 (<code>list</code>)</th>
</tr>
</thead>
<tbody><tr>
<td>가변성</td>
<td>❌ 불변 (immutable)</td>
<td>✅ 가변 (mutable)</td>
</tr>
<tr>
<td>괄호</td>
<td><code>()</code></td>
<td><code>[]</code></td>
</tr>
<tr>
<td>메모리</td>
<td>더 적게 사용</td>
<td>더 많이 사용</td>
</tr>
<tr>
<td>속도</td>
<td>더 빠름</td>
<td>더 느림</td>
</tr>
<tr>
<td>사용 용도</td>
<td>변경하면 안 되는 데이터</td>
<td>자주 변경되는 데이터</td>
</tr>
</tbody></table>
<hr />
<h1 id="딕셔너리">딕셔너리</h1>
<ul>
<li>키(key)-값(value) 쌍으로 데이터를 저장하는 Python의 매우 강력한 자료형</li>
<li><table>
<thead>
<tr>
<th>항목</th>
<th>설명</th>
</tr>
</thead>
<tbody><tr>
<td>자료형</td>
<td><code>dict</code></td>
</tr>
<tr>
<td>형태</td>
<td><code>{key: value, key2: value2, ...}</code></td>
</tr>
<tr>
<td>특징</td>
<td>순서 있음(Python 3.7+), <strong>키 중복 불가</strong>, <strong>값은 중복 가능</strong>, 가변 자료형</td>
</tr>
</tbody></table>
</li>
<li><strong>주요 메서드</strong> </li>
<li><table>
<thead>
<tr>
<th>메서드</th>
<th>설명</th>
</tr>
</thead>
<tbody><tr>
<td><code>dict.keys()</code></td>
<td>모든 키 반환</td>
</tr>
<tr>
<td><code>dict.values()</code></td>
<td>모든 값 반환</td>
</tr>
<tr>
<td><code>dict.items()</code></td>
<td>(key, value) 튜플 목록 반환</td>
</tr>
<tr>
<td><code>dict.get(k, x)</code></td>
<td>키 k의 값, 없으면 x 반환</td>
</tr>
<tr>
<td><code>dict.pop(k)</code></td>
<td>키 k의 값 꺼내고 삭제</td>
</tr>
<tr>
<td><code>dict.popitem()</code></td>
<td>가장 마지막 (key, value) 제거</td>
</tr>
<tr>
<td><code>dict.clear()</code></td>
<td>모두 삭제</td>
</tr>
<tr>
<td><code>dict.update({...})</code></td>
<td>여러 항목 추가/변경</td>
</tr>
</tbody></table>
</li>
</ul>
<hr />
<h1 id="set">set</h1>
<ul>
<li>중복 없는 데이터의 모음을 표현하는 데 유용하며 수학의 집합과 유사한 연산도 가능</li>
<li><table>
<thead>
<tr>
<th>항목</th>
<th>설명</th>
</tr>
</thead>
<tbody><tr>
<td>자료형</td>
<td><code>set</code></td>
</tr>
<tr>
<td>형태</td>
<td><code>{값1, 값2, ...}</code> 또는 <code>set(iterable)</code></td>
</tr>
<tr>
<td>특징</td>
<td><strong>중복 허용 X</strong>, <strong>순서 없음</strong>, <strong>mutable(가변)</strong></td>
</tr>
<tr>
<td>주요 용도</td>
<td>중복 제거, 교집합·합집합·차집합 등 집합 연산</td>
</tr>
</tbody></table>
</li>
<li>** 주요 메서드**</li>
<li><table>
<thead>
<tr>
<th>메서드</th>
<th>설명</th>
<th>예시</th>
</tr>
</thead>
<tbody><tr>
<td><code>add(x)</code></td>
<td>원소 추가</td>
<td><code>s.add(4)</code></td>
</tr>
<tr>
<td><code>update([...])</code></td>
<td>여러 원소 추가</td>
<td><code>s.update([5, 6])</code></td>
</tr>
<tr>
<td><code>remove(x)</code></td>
<td>원소 제거 (없으면 에러)</td>
<td><code>s.remove(2)</code></td>
</tr>
<tr>
<td><code>discard(x)</code></td>
<td>원소 제거 (없으면 무시)</td>
<td><code>s.discard(9)</code></td>
</tr>
<tr>
<td><code>pop()</code></td>
<td>임의의 원소 제거 및 반환</td>
<td><code>s.pop()</code></td>
</tr>
<tr>
<td><code>clear()</code></td>
<td>전체 제거</td>
<td><code>s.clear()</code></td>
</tr>
</tbody></table>
</li>
</ul>