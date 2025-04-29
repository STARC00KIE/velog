<ul>
<li><a href="https://github.com/STARC00KIE/bootcamp/blob/main/python_study/0429.ipynb">Github</a></li>
</ul>
<hr />
<h1 id="함수">함수</h1>
<ul>
<li>함수는 어떤 일을 하는 것에 대한 묶음</li>
<li>키보드 입력 함수: <code>input()</code></li>
<li>화면 출력 함수: <code>print()</code></li>
<li>내장 함수: <code>type()</code>, <code>len()</code>, <code>ord()</code></li>
<li>사용자 정의 함수: 여러 개의 반환값 지정 가능, 함수의 인수에 디폴트 인수로 설정해줄 수 있음 </li>
<li>ex) <code>def sum_range(begin, end, step=1)</code></li>
<li>전역 변수: 프로그램 전체에서 접근할 수 있는 변수</li>
</ul>
<hr />
<h1 id="전역-변수와-지역-변수">전역 변수와 지역 변수</h1>
<ul>
<li><table>
<thead>
<tr>
<th align="left">구분</th>
<th align="left">전역 변수</th>
<th align="left">지역 변수</th>
</tr>
</thead>
<tbody><tr>
<td align="left">선언 위치</td>
<td align="left">함수 바깥</td>
<td align="left">함수 안</td>
</tr>
<tr>
<td align="left">사용 범위</td>
<td align="left">프로그램 전체</td>
<td align="left">해당 함수 안에서만</td>
</tr>
<tr>
<td align="left">생명주기</td>
<td align="left">프로그램 끝날 때까지</td>
<td align="left">함수 실행 중에만</td>
</tr>
<tr>
<td align="left">함수 안 수정 방법</td>
<td align="left">global 선언 필요</td>
<td align="left">그냥 수정 가능</td>
</tr>
</tbody></table>
</li>
<li><p><code>global</code>을 사용하여 지역 변수를 전역 변수로 사용 가능</p>
</li>
<li><p>코드 예시</p>
<pre><code class="language-python">def abc(rad):
  param = rad + pi  # (1) rad + pi를 계산해서 param에 저장
  return param      # (2) param을 반환
</code></pre>
</li>
</ul>
<p>pi = 1               # (3) 전역 변수 pi = 1
param = 0            # (4) 전역 변수 param = 0
print(abc(10))       # (5) abc(10)을 호출하고 결과를 출력, 결과 11</p>
<pre><code>
---

# 모듈과 네임스페이스
1. 모듈
- 코드 묶음이야.
- 파이썬 파일 하나 (.py)가 모듈
- 기능별로 코드를 분리할 때 사용

2. 네임스페이스
- &quot;이름(name)&quot;과 &quot;값(value)&quot;을 저장하는 공간
- 변수, 함수 이름들이 어디에 속하는지 구분하는 시스템

3. 네임스페이스의 종류
- |네임스페이스 종류 | 설명|
|:--|:--|
|전역 네임스페이스(Global Namespace) | 모듈(파일) 전체에서 쓰는 이름들|
|지역 네임스페이스(Local Namespace) | 함수 안에서 쓰는 이름들|
|내장 네임스페이스(Builtin Namespace) | print, len 같은 기본 제공 함수들|

---

# 시퀀스에서 가능한 주요 연산

|연산    |설명    |예시|
|:--|:--|:--|
|x in s|    시퀀스 s에 x가 존재하는지 확인|    'a' in ['a', 'b', 'c'] → True|
|x not in s|    시퀀스 s에 x가 없는지 확인|    3 not in (1, 2, 4) → True|
|s + t|    두 시퀀스를 이어붙임 (같은 타입)|    [1, 2] + [3, 4] → [1, 2, 3, 4]|
|s * n 또는 n * s|    시퀀스를 n번 반복|    'ab' * 3 → 'ababab'|
|s[i]|    인덱스 i에 해당하는 요소 접근|    'hello'[1] → 'e'|
|s[i:j]|    인덱스 i부터 j-1까지 슬라이싱|    [0,1,2,3,4][1:4] → [1,2,3]|
|len(s)|    시퀀스 길이 반환|    len((1,2,3)) → 3|
|min(s) / max(s)|    최소/최대 요소 반환|    min([3,1,4]) → 1|
|sum(s)|    숫자 시퀀스의 합|    sum([1,2,3]) → 6|
|sorted(s)|    정렬된 리스트 반환|    sorted((3,1,2)) → [1,2,3]|
|reversed(s)|    역순 반복자 반환|    list(reversed('abc')) → ['c','b','a']|

---

# 시퀀스 관련 주요 내장 함수

|함수    |설명    |예시|
|:--|:--|:--|
|enumerate(s)|    인덱스와 요소를 튜플로 반환하는 반복자 생성    |list(enumerate(['a','b'])) → [(0,'a'),(1,'b')]
|zip(s1, s2, ...)|    여러 시퀀스를 병렬로 묶음    |list(zip([1,2], ['a','b'])) → [(1,'a'),(2,'b')]|
|list(s) / tuple(s) / str(s)|    다른 타입으로 변환|    list((1,2,3)) → [1,2,3]|
|all(s)|    모든 요소가 참이면 True    |all([True, 1, 'a']) → True|
any(s)|    하나라도 참이면 True    |any([0, '', None, 5]) → True|


# 가변 시퀀스(list) 전용 메서드
|메서드|    설명|    예시|
|:--|:--|:--|
|append(x)    |요소 x를 끝에 추가    |lst.append(4)|
|extend(t)    |시퀀스 t를 리스트에 추가|    lst.extend([5,6])|
|insert(i, x)|    인덱스 i에 요소 x 삽입|    lst.insert(1, 'a')|
|remove(x)    |첫 번째로 등장하는 x 제거|    lst.remove(3)|
|pop([i])    |인덱스 i 요소 제거 후 반환|    lst.pop() or lst.pop(2)|
|clear()    |모든 요소 제거    |lst.clear()|
|index(x)    |요소 x의 첫 번째 인덱스 반환    |lst.index(2)|
|count(x)    |요소 x 개수 반환|    lst.count(2)|
|reverse()|    리스트 역순으로 변경|    lst.reverse()|
|sort()|    리스트를 정렬    |lst.sort()|

---

# 불변 시퀀스(tuple, str)의 특징
1. 수정 불가(immutable): 튜플과 문자열은 생성 후 요소 변경이 불가능
2. 메서드 제한: append(), remove() 같은 변경 메서드는 사용할 수 없음
3. 슬라이싱, 연결, 반복 연산은 가능

---

# 리스트 컴프리헨션
1. 리스트 컴프리헨션이란?
    - 리스트를 간결하게 생성하는 방법
    - 기존의 for문과 append()를 한 줄로 압축
    - 읽기 쉽고 작성이 빠르다

---

# 기본 문법
```[ 표현식 for 변수 in 반복가능한객체 (if 조건문) ]```
- 표현식: 리스트에 담을 값
- for 변수 in 반복가능한객체: 반복문
- (선택) if 조건문: 필터링
</code></pre>