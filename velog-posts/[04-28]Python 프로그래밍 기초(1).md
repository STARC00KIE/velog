<ul>
<li>Github 링크: <a href="https://github.com/STARC00KIE/bootcamp/blob/main/python_study/0428.ipynb">[실습 코드]</a></li>
</ul>
<h1 id="파이썬-기초-개념정리">파이썬 기초 개념정리</h1>
<ol>
<li>1991년 귀도 반 로섬이 개발한 대화형 프로그래밍, 객체지향 프로그래밍 언어</li>
<li>높은 생산성, 오픈소스, 풍부한 라이브러리, 직관적인 문법, 다양한 플랫폼 지원</li>
<li>구글에서 만든 GO 언어 출시됨(Python보다 하드웨어에 부하가 적음)</li>
<li>Python은 메모리 관리에 어려움이 있음</li>
<li>오픈소스의 특징: 하위버전을 서포트할 의무가 없음, 버전의 차이별로 코드 작성에 어려움이 있음</li>
</ol>
<hr />
<h1 id="자료형">자료형</h1>
<ol>
<li>수치: int, float, complex(복소수), bool</li>
<li>시퀀스: str, list, tuple</li>
<li>매핑: dict</li>
<li>집합: set, frozenset</li>
</ol>
<hr />
<h1 id="변수variable">변수(Variable)</h1>
<ol>
<li>파이썬의 모든 객체는 클래스로부터 만들어진 객체</li>
<li>변수는 모든 객체를 참조하는 참조자 또는 포인터 역할</li>
</ol>
<hr />
<h1 id="연산자">연산자</h1>
<ol>
<li>/(나누기, 실수), //(몫, 정수)</li>
<li>제곱: **</li>
<li>단항 연산자: +=, -+</li>
<li>관계 연산자: &gt;, &lt;, &lt;=, &gt;=, ==, !=</li>
<li>불리언 연산: ||, &amp;&amp;, !, or, and, not</li>
<li>in, not in</li>
</ol>
<hr />
<h1 id="조건문">조건문</h1>
<ol>
<li>if, else, elif</li>
</ol>
<hr />
<h1 id="제어문">제어문</h1>
<ol>
<li>반복문: for ~ in ~, while</li>
<li>range(a, b, d): a부터 b-1까지 d간격으로 출력</li>
</ol>
<hr />
<h1 id="함수">함수</h1>
<ol>
<li>내장 함수: input(), type(), len(), ord()등</li>
<li>사용자 함수: def [함수명] 작성</li>
</ol>
<hr />
<h1 id="스코프변수의-범위">스코프(변수의 범위)</h1>
<ol>
<li>내장 범위(built-in scope)<ul>
<li>언어의 일부로 정의된 변수와 리터럴등</li>
<li>프로그램의 어디에서나 사용할 수 있음</li>
</ul>
</li>
<li>전역 범위(global scope)<ul>
<li>소스 파일의 맨 꼭대기 레벨(함수나 클래스 밖)에서 생성</li>
<li>그 안에서만 사용, 함수의 매개변수들도 지역범위</li>
</ul>
</li>
<li>인스턴스 범위(instance scope)<ul>
<li>클래스의 데이터 멤버로 생성된 변수</li>
<li>클래스 내의 다른 함수들에서 사용할 수 있음</li>
</ul>
</li>
</ol>
<hr />
<h1 id="list-메서드">list 메서드</h1>
<ol>
<li>s.append(item): 항목의 item을 리스트 s의 맨 뒤에 추가</li>
<li>s.extend(lst): 리스트 lst를 리스트 s 뒤에서부터 결합함</li>
<li>s.count(item): 리스트에서 항목 item의 개수를 세고 그 개수를 반환함</li>
<li>s[시작:종료].count(item): 리스트에서 항목 item을 찾아 가장 작은 인덱스를 반환함, 탐색의 시작 위치와 종료 위치를 지정할 수도 있음</li>
<li>s.insert(pos, item): pos 위치에 항목 item을 삽입함</li>
<li>s.pop(pos): pos 위치의 항목을 s에서 꺼내고 반환함</li>
<li>s.remove(item): 항목 item을 s에서 제거</li>
<li>s.reverse(): 리스트 항목 순서 뒤집음</li>
<li>s.sort([key], [reverse]): 항목을 정렬함</li>
<li>s.index(item): item의 index를 출력</li>
</ol>