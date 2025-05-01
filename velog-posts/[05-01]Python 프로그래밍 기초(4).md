<h1 id="1-class">1. Class</h1>
<hr />
<h1 id="개념">개념</h1>
<ul>
<li><p>객체지향 프로그래밍(OOP)의 핵심 개념 중 하나로, 현실 세계의 사물을 코드로 표현할 때 유용하게 사용됨</p>
</li>
<li><table>
<thead>
<tr>
<th>항목</th>
<th>설명</th>
</tr>
</thead>
<tbody><tr>
<td>정의</td>
<td><strong>속성과 동작을 묶은 사용자 정의 자료형</strong></td>
</tr>
<tr>
<td>목적</td>
<td>관련 있는 데이터(변수)와 기능(함수)을 하나로 묶어 코드 재사용성과 구조화된 설계를 가능하게 함</td>
</tr>
<tr>
<td>구성 요소</td>
<td>클래스 정의 → 객체 생성 → 속성/메서드 사용</td>
</tr>
</tbody></table>
</li>
</ul>
<hr />
<h1 id="클래스의-기본-구조">클래스의 기본 구조</h1>
<pre><code class="language-python">class 클래스이름:
    def __init__(self, 매개변수):
        self.속성 = 값

    def 메서드(self):
        동작</code></pre>
<hr />
<h1 id="예시-간단한-person-클래스">예시: 간단한 person 클래스</h1>
<pre><code class="language-python">class Person:
    def __init__(self, name, age):      # 생성자
        self.name = name
        self.age = age

    def greet(self):                    # 메서드
        print(f&quot;안녕하세요, 저는 {self.name}이고 {self.age}살입니다.&quot;)</code></pre>
<pre><code class="language-python">p1 = Person(&quot;철수&quot;, 20)    # 인스턴스(객체) 생성
p1.greet()                # 메서드 호출</code></pre>
<hr />
<h1 id="핵심-개념-정리">핵심 개념 정리</h1>
<ol>
<li><code>self</code></li>
</ol>
<ul>
<li>자기 자신 인스턴스 참조</li>
<li>메서드 안에서 객체의 속성과 메서드에 접근할 때 사용</li>
</ul>
<ol start="2">
<li><code>__init__()</code></li>
</ol>
<ul>
<li>생성자(Constructor) 역할</li>
<li>객체 생성 시 자동 호출 → 속성 초기화</li>
</ul>
<ol start="3">
<li>인스턴스 vs 클래스</li>
</ol>
<table>
<thead>
<tr>
<th align="left">구분</th>
<th align="left">설명</th>
</tr>
</thead>
<tbody><tr>
<td align="left">클래스</td>
<td align="left">설계도</td>
</tr>
<tr>
<td align="left">인스턴스</td>
<td align="left">클래스를 통해 만들어진 <strong>실제 객체</strong></td>
</tr>
<tr>
<td align="left">- `a = Person(&quot;영희&quot;, 21)  # 인스턴스 a</td>
<td align="left"></td>
</tr>
<tr>
<td align="left">`</td>
<td align="left"></td>
</tr>
</tbody></table>
<ol start="4">
<li>클래스 내부 구성요소</li>
</ol>
<table>
<thead>
<tr>
<th>구성 요소</th>
<th>설명</th>
</tr>
</thead>
<tbody><tr>
<td>속성 (Attribute)</td>
<td>객체가 가진 데이터 (<code>self.name</code>, <code>self.age</code>)</td>
</tr>
<tr>
<td>메서드 (Method)</td>
<td>객체가 할 수 있는 동작 (함수)</td>
</tr>
<tr>
<td>클래스 변수</td>
<td>모든 인스턴스가 공유</td>
</tr>
<tr>
<td>인스턴스 변수</td>
<td>객체마다 다름</td>
</tr>
</tbody></table>
<ol start="5">
<li><p>클래스 변수 vs 인스턴스 변수</p>
<pre><code class="language-python">class Dog:
 kind = &quot;mammal&quot;  # 클래스 변수

 def __init__(self, name):
     self.name = name  # 인스턴스 변수
</code></pre>
</li>
</ol>
<p>d1 = Dog(&quot;뽀삐&quot;)
d2 = Dog(&quot;초코&quot;)
print(d1.kind)  # mammal
print(d2.name)  # 초코</p>
<pre><code>
6. 상속
```python
class Student(Person):  # Person 클래스 상속
    def __init__(self, name, age, school):
        super().__init__(name, age)
        self.school = school

    def greet(self):
        print(f&quot;저는 {self.school} 학생 {self.name}입니다.&quot;)</code></pre><ol start="7">
<li><p>캡슐화 / 정보은닉</p>
<pre><code class="language-python">class Account:
 def __init__(self, balance):
     self.__balance = balance  # private 변수 (접근 제한)

 def get_balance(self):
     return self.__balance</code></pre>
</li>
</ol>
<hr />
<h1 id="클래스를-사용하는-이유">클래스를 사용하는 이유</h1>
<table>
<thead>
<tr>
<th>이유</th>
<th>설명</th>
</tr>
</thead>
<tbody><tr>
<td>코드 재사용</td>
<td>여러 객체를 쉽게 만들 수 있음</td>
</tr>
<tr>
<td>유지보수</td>
<td>코드 구조화로 관리 쉬움</td>
</tr>
<tr>
<td>추상화</td>
<td>복잡한 동작을 감추고 필요한 인터페이스만 제공</td>
</tr>
<tr>
<td>현실 세계 표현</td>
<td>객체(사람, 자동차 등)를 직관적으로 모델링 가능</td>
</tr>
</tbody></table>
<hr />
<h1 id="super-란">super() 란?</h1>
<table>
<thead>
<tr>
<th>항목</th>
<th>설명</th>
</tr>
</thead>
<tbody><tr>
<td>정의</td>
<td><strong>부모(상위) 클래스</strong>의 메서드나 속성에 접근할 때 사용하는 함수</td>
</tr>
<tr>
<td>주 용도</td>
<td>상속받은 클래스에서 <strong>부모 클래스 기능을 확장하거나 재정의</strong>할 때 사용</td>
</tr>
<tr>
<td>형태</td>
<td><code>super().메서드()</code></td>
</tr>
</tbody></table>
<hr />
<h1 id="super를-쓰는-이유">super를 쓰는 이유</h1>
<ul>
<li>부모 클래스의 메서드를 직접 호출할 수 있음</li>
<li>코드 중복을 줄이고, 변경에도 유연하게 대응할 수 있음</li>
<li>다중 상속(Multiple Inheritance) 상황에서도 올바른 순서로 메서드가 호출됨 (MRO: Method Resolution Order).</li>
</ul>
<h1 id="기본-사용-예시">기본 사용 예시</h1>
<pre><code class="language-python">class Parent:
    def greet(self):
        print(&quot;안녕, 나는 부모야.&quot;)

class Child(Parent):
    def greet(self):
        super().greet()  # 부모의 greet 호출
        print(&quot;안녕, 나는 자식이야.&quot;)

c = Child()
c.greet()</code></pre>
<ul>
<li>출력 결과<pre><code class="language-markdown">안녕, 나는 부모야.
안녕, 나는 자식이야.
</code></pre>
</li>
</ul>
<p>결과 설명
<code>Child</code>의 <code>greet</code> 안에서 <code>super().greet()</code>를 호출 → 부모의 <code>greet</code> 먼저 실행하고, 자식 동작 을 추가</p>
<pre><code>
---

# super를 생성자(__init__)에 사용
```python
class Person:
    def __init__(self, name):
        self.name = name

class Student(Person):
    def __init__(self, name, school):
        super().__init__(name)     # 부모 생성자 호출
        self.school = school

s = Student(&quot;영희&quot;, &quot;서울고&quot;)
print(s.name, s.school)  # 영희 서울고</code></pre><ul>
<li><p>설명:</p>
</li>
<li><p>super().<strong>init</strong>(name)을 호출해서 Person 클래스의 초기화 작업을 완료한 후 Student만의 추가 속성 school을 초기화함.</p>
</li>
<li><p>주의사항:</p>
</li>
</ul>
<table>
<thead>
<tr>
<th>항목</th>
<th>설명</th>
</tr>
</thead>
<tbody><tr>
<td>꼭 괄호</td>
<td><code>super()</code> 괄호 반드시 써야 함</td>
</tr>
<tr>
<td>self 아님</td>
<td><code>self</code> 대신 <code>cls</code> (class를 기준으로 동작)</td>
</tr>
<tr>
<td>메서드 오버라이드</td>
<td>부모 메서드를 덮어쓸 때 <code>super()</code>로 부모 로직을 호출할 수 있음</td>
</tr>
</tbody></table>
<h1 id="다중-상속에서의-super">다중 상속에서의 super()</h1>
<pre><code class="language-python">class A:
    def func(self):
        print('A')

class B(A):
    def func(self):
        print('B')
        super().func()

class C(A):
    def func(self):
        print('C')
        super().func()

class D(B, C):  # 다중 상속
    def func(self):
        print('D')
        super().func()

d = D()
d.func()</code></pre>
<ul>
<li>super()는 <strong>MRO(Method Resolution Order)</strong>를 따라 부모들을 순서대로 호출함.</li>
</ul>
<hr />
<h1 id="super-요약">super 요약</h1>
<table>
<thead>
<tr>
<th>내용</th>
<th>예시</th>
</tr>
</thead>
<tbody><tr>
<td>부모 메서드 호출</td>
<td><code>super().메서드()</code></td>
</tr>
<tr>
<td>부모 생성자 호출</td>
<td><code>super().__init__(...)</code></td>
</tr>
<tr>
<td>다중 상속 지원</td>
<td>MRO 순서로 안전하게 호출</td>
</tr>
<tr>
<td>코드 재사용성</td>
<td>높음 (부모 기능 재사용)</td>
</tr>
</tbody></table>
<hr />
<h1 id="매직-메서드란">매직 메서드란?</h1>
<ul>
<li>이름 앞뒤에 __ (밑줄 두 개)가 붙은 메서드</li>
<li>파이썬이 특별한 상황에 자동으로 호출하는 함수</li>
<li>객체의 동작을 커스터마이징할 수 있음</li>
</ul>
<hr />
<h1 id="매직-메서드를-쓰는-이유">매직 메서드를 쓰는 이유</h1>
<ul>
<li>파이썬 기본 문법(<code>+</code>, <code>in</code>, <code>for</code>, <code>print()</code>)을 내 객체에 맞게 커스터마이징할 수 있음</li>
<li>자연스럽고 직관적인 코드 작성 가능</li>
<li>클래스의 기능을 확장하고, 표준 라이브러리와 호환성을 높일 수 있음</li>
</ul>
<hr />
<h1 id="자주-쓰는-매직-메서드-정리">자주 쓰는 매직 메서드 정리</h1>
<table>
<thead>
<tr>
<th align="left">메서드</th>
<th align="left">설명</th>
<th align="left">예시</th>
</tr>
</thead>
<tbody><tr>
<td align="left"><code>__init__(self, ...)</code></td>
<td align="left">객체가 생성될 때 호출 (생성자)</td>
<td align="left"><code>p = Person(&quot;Tom&quot;)</code></td>
</tr>
<tr>
<td align="left"><code>__del__(self)</code></td>
<td align="left">객체가 소멸될 때 호출 (소멸자)</td>
<td align="left">객체 삭제할 때 자동 호출</td>
</tr>
<tr>
<td align="left"><code>__str__(self)</code></td>
<td align="left"><code>str()</code>이나 <code>print()</code>할 때 문자열 반환</td>
<td align="left"><code>print(p)</code></td>
</tr>
<tr>
<td align="left"><code>__repr__(self)</code></td>
<td align="left">객체를 &quot;개발자용&quot; 문자열로 표현</td>
<td align="left"><code>repr(p)</code></td>
</tr>
<tr>
<td align="left"><code>__len__(self)</code></td>
<td align="left"><code>len()</code> 함수 호출 시</td>
<td align="left"><code>len(obj)</code></td>
</tr>
<tr>
<td align="left"><code>__getitem__(self, key)</code></td>
<td align="left">인덱싱(<code>obj[key]</code>)할 때 호출</td>
<td align="left"><code>obj[0]</code></td>
</tr>
<tr>
<td align="left"><code>__setitem__(self, key, value)</code></td>
<td align="left">인덱스에 값 설정할 때 호출</td>
<td align="left"><code>obj[0] = 10</code></td>
</tr>
<tr>
<td align="left"><code>__delitem__(self, key)</code></td>
<td align="left">인덱스 요소 삭제할 때 호출</td>
<td align="left"><code>del obj[0]</code></td>
</tr>
<tr>
<td align="left"><code>__iter__(self)</code></td>
<td align="left">반복 가능한 객체 만들기 (<code>for</code>)</td>
<td align="left"><code>for x in obj:</code></td>
</tr>
<tr>
<td align="left"><code>__next__(self)</code></td>
<td align="left">반복자에서 다음 값 가져오기</td>
<td align="left"><code>next(obj)</code></td>
</tr>
<tr>
<td align="left"><code>__contains__(self, item)</code></td>
<td align="left"><code>in</code> 연산자 사용 시</td>
<td align="left"><code>item in obj</code></td>
</tr>
<tr>
<td align="left"><code>__eq__(self, other)</code></td>
<td align="left"><code>==</code> 연산자 오버라이딩</td>
<td align="left"><code>a == b</code></td>
</tr>
<tr>
<td align="left"><code>__lt__(self, other)</code></td>
<td align="left"><code>&lt;</code> 연산자 오버라이딩</td>
<td align="left"><code>a &lt; b</code></td>
</tr>
<tr>
<td align="left"><code>__add__(self, other)</code></td>
<td align="left"><code>+</code> 연산자 오버라이딩</td>
<td align="left"><code>a + b</code></td>
</tr>
<tr>
<td align="left"><code>__sub__(self, other)</code></td>
<td align="left"><code>-</code> 연산자 오버라이딩</td>
<td align="left"><code>a - b</code></td>
</tr>
<tr>
<td align="left"><code>__mul__(self, other)</code></td>
<td align="left"><code>*</code> 연산자 오버라이딩</td>
<td align="left"><code>a * b</code></td>
</tr>
<tr>
<td align="left"><code>__call__(self, ...)</code></td>
<td align="left">객체를 함수처럼 호출할 때</td>
<td align="left"><code>obj()</code></td>
</tr>
<tr>
<td align="left"><code>__enter__(self)</code></td>
<td align="left">with문 시작 시</td>
<td align="left"><code>with obj:</code></td>
</tr>
<tr>
<td align="left"><code>__exit__(self, exc_type, exc_val, exc_tb)</code></td>
<td align="left">with문 끝날 때</td>
<td align="left">에러 처리 포함</td>
</tr>
</tbody></table>
<hr />
<h1 id="매직-메서드-예시">매직 메서드 예시</h1>
<ol>
<li><p><code>__str__</code> 과 <code>__repr__</code></p>
<pre><code class="language-python">class Person:
 def __init__(self, name):
     self.name = name

 def __str__(self):
     return f&quot;Person 이름: {self.name}&quot;

 def __repr__(self):
     return f&quot;Person('{self.name}')&quot;
</code></pre>
</li>
</ol>
<p>p = Person(&quot;Tom&quot;)
print(p)       # Person 이름: Tom
print(repr(p)) # Person('Tom')</p>
<pre><code>2. `__add__`
```python
class Number:
    def __init__(self, value):
        self.value = value

    def __add__(self, other):
        return Number(self.value + other.value)

a = Number(3)
b = Number(7)
c = a + b
print(c.value)  # 10</code></pre><ol start="3">
<li><p><code>__getitem__</code>, <code>__setitem__</code></p>
<pre><code class="language-python">class MyList:
 def __init__(self, data):
     self.data = data

 def __getitem__(self, index):
     return self.data[index]

 def __setitem__(self, index, value):
     self.data[index] = value
</code></pre>
</li>
</ol>
<p>lst = MyList([1, 2, 3])
print(lst[1])   # 2
lst[1] = 10
print(lst[1])   # 10</p>
<pre><code>
---

# 네임 맹글링(name mangling)
- 변수 이름을 내부적으로 살짝 바꿔버려서 외부에서 함부로 접근 못 하게 만드는 것

| 구분 | 설명 |
|------|------|
| 보호 목적 | 외부에서 실수로 접근하거나 변경하는 걸 막기 위해 |
| 내부 이름 변경 | `__변수명` → `_클래스명__변수명` 으로 이름 바뀜 |
| 완전 차단 아님 | 강제로 접근할 수는 있지만 일부러 어렵게 만듦 |
| 주 용도 | **캡슐화(Encapsulation)** 구현 |

---

# 네임 맹글링 예시 코드
```python
class Counter:
    def __init__(self):
        self.__count = 0   # __count는 외부에서 직접 접근 금지

    def increment(self):
        self.__count += 1

    def get_count(self):
        return self.__count

c = Counter()
c.increment()
print(c.get_count())  # 1

print(c.__count)      # ❌ AttributeError 발생</code></pre><hr />
<h1 id="언더바-개수별-차이">언더바 개수별 차이</h1>
<table>
<thead>
<tr>
<th align="left">형태</th>
<th align="left">의미</th>
<th align="left">예시</th>
</tr>
</thead>
<tbody><tr>
<td align="left"><code>_변수명</code></td>
<td align="left">&quot;이건 내부용입니다&quot; (약속, 강제 아님)</td>
<td align="left"><code>_temp</code></td>
</tr>
<tr>
<td align="left"><code>__변수명</code></td>
<td align="left">네임 맹글링 (외부 접근 방지)</td>
<td align="left"><code>__count</code></td>
</tr>
<tr>
<td align="left"><code>__변수명__</code></td>
<td align="left">시스템 예약 메서드나 속성</td>
<td align="left"><code>__init__</code>, <code>__str__</code></td>
</tr>
</tbody></table>
<hr />
<h1 id="언더바-하나_변수명-vs-두-개__변수명-차이">언더바 하나(_변수명) vs 두 개(__변수명) 차이</h1>
<table>
<thead>
<tr>
<th align="left">구분</th>
<th align="left"><code>_변수명</code> (Protected)</th>
<th align="left"><code>__변수명</code> (Private)</th>
</tr>
</thead>
<tbody><tr>
<td align="left">의미</td>
<td align="left">&quot;이건 내부 전용입니다&quot; (약속)</td>
<td align="left">&quot;외부에서 직접 접근 막겠습니다&quot; (네임 맹글링)</td>
</tr>
<tr>
<td align="left">강제성</td>
<td align="left">없음 (외부에서 접근 가능)</td>
<td align="left">있음 (이름 변형해서 숨김)</td>
</tr>
<tr>
<td align="left">관례</td>
<td align="left">서브클래스(자식 클래스)에서는 접근할 수도 있음</td>
<td align="left">서브클래스에서도 쉽게 접근 불가</td>
</tr>
<tr>
<td align="left">사용 예시</td>
<td align="left">상속받은 클래스끼리 공유하는 내부 데이터</td>
<td align="left">철저히 숨기고 싶은 데이터</td>
</tr>
</tbody></table>
<hr />
<h1 id="super와-직접-호출-차이-정리">super()와 직접 호출 차이 정리</h1>
<table>
<thead>
<tr>
<th align="left">구분</th>
<th align="left">super() 사용</th>
<th align="left">직접 부모 호출</th>
</tr>
</thead>
<tbody><tr>
<td align="left">호출 방식</td>
<td align="left">MRO 순서에 따라 자동 진행</td>
<td align="left">명시적으로 부모 클래스 호출</td>
</tr>
<tr>
<td align="left">중복 호출</td>
<td align="left">없음 (MRO 관리)</td>
<td align="left">발생할 수 있음</td>
</tr>
<tr>
<td align="left">유지보수</td>
<td align="left">구조 변경에 강함</td>
<td align="left">구조 변경 시 수동 수정 필요</td>
</tr>
<tr>
<td align="left">코드 가독성</td>
<td align="left">좋음 (super 체인)</td>
<td align="left">나쁨 (중복 많아짐)</td>
</tr>
<tr>
<td align="left">다중 상속 대응</td>
<td align="left">완벽 (MRO 기반)</td>
<td align="left">취약 (순서 헷갈릴 수 있음)</td>
</tr>
</tbody></table>
<hr />
<h1 id="self란">self란?</h1>
<ul>
<li>self는 클래스 인스턴스 자신을 가리키는 키워드</li>
<li>클래스 안에서 <strong>속성(변수)</strong>이나 <strong>메서드(함수)</strong>를 사용할 때 반드시 필요하다</li>
<li>파이썬은 자동으로 객체를 넘겨주지 않기 때문에, 우리가 self를 명시적으로 첫 번째 인자로 써야 한다</li>
</ul>
<hr />
<h1 id="self를-쓰는-이유">self를 쓰는 이유</h1>
<table>
<thead>
<tr>
<th align="left">이유</th>
<th align="left">설명</th>
</tr>
</thead>
<tbody><tr>
<td align="left">객체 자신을 참조하기 위해</td>
<td align="left">각각의 인스턴스가 자기만의 속성/메서드를 갖게 하기 위해</td>
</tr>
<tr>
<td align="left">클래스 안 메서드 연결</td>
<td align="left">클래스 내부 메서드들이 인스턴스 속성과 자연스럽게 연결되도록</td>
</tr>
</tbody></table>
<hr />
<h1 id="self는-어떤-이름으로도-쓸-수-있나">self는 어떤 이름으로도 쓸 수 있나?</h1>
<ul>
<li>이론상 self는 그냥 첫 번째 매개변수일 뿐이라, 이름을 this, me, obj 뭐든 바꿀 수 있음. 하지만 <strong>self를 쓰는 것이 파이썬의 관례(PEP8 스타일 가이드)</strong>야.</li>
</ul>