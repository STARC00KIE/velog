<h1 id="jadencase-문자열-만들기--python--20분">JadenCase 문자열 만들기 / Python / 20분</h1>
<h2 id="문제">문제</h2>
<hr />
<p><a href="https://school.programmers.co.kr/learn/courses/30/lessons/12951">https://school.programmers.co.kr/learn/courses/30/lessons/12951</a></p>
<h2 id="코드">코드</h2>
<hr />
<pre><code class="language-python">def solution(s):
    s = s.lower()
    answer = &quot;&quot;
    for i in range(len(s)):
        if (i!=0) and s[i-1] == &quot; &quot;:
            answer += s[i].upper()
        elif (i==0):
            answer += s[i].upper()
        else:
            answer += s[i]
    return answer</code></pre>
<h2 id="접근-방식">접근 방식</h2>
<hr />
<ul>
<li><p>코딩 문제 제목에 나와있는 데로 문자열을 이용하여 문제를 해결하려고 생각하였다.</p>
</li>
<li><p>문자열을 공백을 기준으로 split하여 리스트에 저장하고,반복문을 이용하여 split한 문자열을 슬라이싱하여 첫번째 글자는 upper()함수를 이용하여 대문자로 만들어 주었고, 나머지 글자는 lower()함수를 이용하여 소문자로 만들어 주었다.</p>
</li>
<li><p>그 후 빈 문자열에 리스트 안의 문자열과 &quot; &quot;를 더하고 rstrip 함수를 이용헤 불필요한 공백을 제거한 후 문자열을 반환하는 코드를 작성하였다.</p>
</li>
<li><p>```python
def solution(s):
  lst = s.split(&quot; &quot;) # s.split은 구분자로 분할해서 리스트로 반환
  answer = &quot;&quot;</p>
<p>  for string in lst:</p>
<pre><code>  string = string[0].upper() + string[1:].lower()
  answer += (string + &quot; &quot;)</code></pre><p>  return answer.rstrip()</p>
</li>
<li><p>위 코드는 테스트를 통과하지 못했는데, 단어와 단어 사이의 공백(&quot; &quot;)이 여러 개일 수 있는 케이스를 생각하지 못했다.</p>
</li>
<li><p>문제를 해결하기 위해 split() 함수를 이용하지 않는 방법을 고려했다.</p>
</li>
<li><p>일단 함수에서 입력값으로 받은 문자열을 lower()함수를 이용하여 모두 소문자로 만들어 주었다.</p>
</li>
<li><p>문자열을 바로 반복문으로 순회하여, 선택된 문자의 바로 왼쪽에 있는 문자가 공백이면(단어의 첫 번째 글자) 대문자로 바꿔주고 빈 문자열인 answer에 저장해 주었다.</p>
</li>
<li><p>문자열의 첫 번째 글자일 경우에는 따로 케이스를 분리하여 대문자로 바꾸어 answer에 저장하는 코드를 작성해 주었다.</p>
</li>
<li><p>시간복잡도는 O(N)으로 테스트를 통과하였다.</p>
</li>
</ul>
<h2 id="생각해-볼-내용">생각해 볼 내용</h2>
<hr />
<ul>
<li>문제 조건을 자세히 읽어보지 않아서 문제를 해결하는 데 시간이 오래 걸렸다.</li>
<li>문제에 존재하는 예외 조건들을 계속 생각해보면서 문제를 해결해야겠다.</li>
</ul>
<h2 id="기억해야-할-내용">기억해야 할 내용</h2>
<hr />
<ul>
<li>string.rstrip(): 문자열 오른쪽 글자 제거</li>
<li>string.lstrip(): 문자열 왼쪽 글자 제거</li>
<li>string.lower(): 문자열 소문자로 변환(list는 사용 불가능)</li>
<li>string.upper(): 문자열 대문자로 변환(list는 사용 불가능)</li>
</ul>