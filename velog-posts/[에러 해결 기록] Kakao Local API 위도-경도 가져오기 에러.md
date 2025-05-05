<h2 id="1-문제-상황">1. 문제 상황</h2>
<ul>
<li>Python 코드로 Kakao Local API 호출</li>
<li>처음에는 401 Unauthorized 에러 발생</li>
<li>이후에도 None 반환, AccessDeniedError, documents 비어 있음 등 다양한 문제가 발생</li>
</ul>
<hr />
<h2 id="2-문제-발생-및-에러-상황">2. 문제 발생 및 에러 상황</h2>
<h3 id="21-authorization-인증-실패-401-unauthorized">2.1 Authorization 인증 실패 (401 Unauthorized)</h3>
<p><strong>에러 메시지</strong></p>
<pre><code>401 Client Error: Unauthorized for url: https://dapi.kakao.com/...</code></pre><p><strong>원인</strong></p>
<ul>
<li>REST API 키를 잘못 사용했거나</li>
<li>Authorization 헤더 포맷에 문제가 있었음</li>
</ul>
<p><strong>해결 방법</strong></p>
<ul>
<li>Kakao Developers에서 <strong>정확한 &quot;REST API 키&quot;</strong> 복사</li>
<li>Authorization 헤더는 <code>&quot;KakaoAK {REST_API_KEY}&quot;</code> 형식으로 설정</li>
</ul>
<pre><code class="language-python">headers = {&quot;Authorization&quot;: f&quot;KakaoAK {my_key}&quot;}</code></pre>
<hr />
<h3 id="22-unicodeencodeerror-발생-한글-주소-인코딩-오류">2.2 UnicodeEncodeError 발생 (한글 주소 인코딩 오류)</h3>
<p><strong>에러 메시지</strong></p>
<pre><code>UnicodeEncodeError: 'latin-1' codec can't encode characters...</code></pre><p><strong>원인</strong></p>
<ul>
<li>한글 주소를 URL에 그대로 넣어서 인코딩 오류 발생</li>
</ul>
<p><strong>해결 방법</strong></p>
<ul>
<li><code>urllib.parse.quote()</code>를 사용해 한글 주소를 URL-safe 문자열로 변환</li>
</ul>
<pre><code class="language-python">from urllib.parse import quote

encoded_place = quote(place)</code></pre>
<hr />
<h3 id="23-accessdeniederror-발생-웹-브라우저로-요청-시">2.3 AccessDeniedError 발생 (웹 브라우저로 요청 시)</h3>
<p><strong>에러 메시지</strong></p>
<pre><code class="language-json">{&quot;errorType&quot;:&quot;AccessDeniedError&quot;,&quot;message&quot;:&quot;cannot find Authorization : KakaoAK header&quot;}</code></pre>
<p><strong>원인</strong></p>
<ul>
<li>웹 브라우저에서는 Authorization 헤더가 기본적으로 붙지 않음</li>
</ul>
<p><strong>해결 방법</strong></p>
<ul>
<li>API 테스트는 <strong>Python 코드</strong>나 <strong>curl 명령어</strong>를 이용해야 함</li>
<li>브라우저 주소창에서 직접 입력하는 건 의미 없음</li>
</ul>
<hr />
<h2 id="3-최종-해결-방법">3. 최종 해결 방법</h2>
<ol>
<li>Kakao Developers에 접속</li>
<li>새 애플리케이션 생성</li>
<li>새 &quot;REST API 키&quot;를 복사</li>
</ol>
<ul>
<li>이후 정상적으로 200 OK 응답 및 위도/경도 데이터 정상 수신</li>
</ul>
<hr />
<h2 id="4-최종-정상-작동-코드">4. 최종 정상 작동 코드</h2>
<pre><code class="language-python">import requests
from urllib.parse import quote

def get_geocoding(place, my_key):
    print(f&quot;요청 주소: {place}&quot;)  # 요청할 주소 출력
    encoded_place = quote(place)  # 한글 주소 URL 인코딩
    url = f&quot;https://dapi.kakao.com/v2/local/search/address.json?query={encoded_place}&quot;
    headers = {&quot;Authorization&quot;: f&quot;KakaoAK {my_key}&quot;}  # Authorization 헤더 설정

    try:
        response = requests.get(url, headers=headers)  # GET 요청
        print(f&quot;응답 코드: {response.status_code}&quot;)  # 응답 코드 출력
        response.raise_for_status()  # 에러 발생 시 예외 처리
        result = response.json()  # JSON 형태로 파싱

        if result[&quot;documents&quot;]:
            y = result[&quot;documents&quot;][0][&quot;y&quot;]  # 위도
            x = result[&quot;documents&quot;][0][&quot;x&quot;]  # 경도
            return float(y), float(x)
        else:
            print(f&quot;검색 결과 없음: {place}&quot;)
            return None, None

    except requests.exceptions.RequestException as e:
        print(f&quot;요청 실패: {e}&quot;)
        return None, None</code></pre>
<hr />
<h2 id="5-실제-여러-주소-처리-코드">5. 실제 여러 주소 처리 코드</h2>
<pre><code class="language-python">import pandas as pd

lat = []  # 위도 저장 리스트
lng = []  # 경도 저장 리스트

# 검색할 장소 리스트
places = [&quot;서울특별시 종로구 세종대로 175&quot;, 
          &quot;서울특별시 서초구 서초동 700&quot;, 
          &quot;부산광역시 해운대구 해운대해변로 264&quot;]

# 각 장소에 대해 반복
for place in places:
    try:
        place_lat, place_lon = get_geocoding(place, my_key)  # 위도, 경도 가져오기
        lat.append(place_lat)  # 위도 저장
        lng.append(place_lon)  # 경도 저장

    except Exception as e:
        print(f&quot;에러 발생: {e}&quot;)
        lat.append(None)
        lng.append(None)

# DataFrame으로 변환
df = pd.DataFrame({'위도': lat, '경도': lng}, index=places)

df</code></pre>
<hr />
<h2 id="6-교훈-및-체크리스트">6. 교훈 및 체크리스트</h2>
<ul>
<li>REST API 키를 정확히 복사한다</li>
<li>Authorization 헤더는 <code>&quot;KakaoAK {키}&quot;</code> 형식으로 설정한다</li>
<li>한글 주소는 <code>urllib.parse.quote()</code>로 인코딩한다</li>
<li>브라우저 대신 Python 코드나 curl로 API 호출 테스트한다</li>
</ul>
<hr />
<h1 id="최종-요약">최종 요약</h1>
<table>
<thead>
<tr>
<th align="left">문제</th>
<th align="left">원인</th>
<th align="left">해결 방법</th>
</tr>
</thead>
<tbody><tr>
<td align="left">401 Unauthorized</td>
<td align="left">인증 키 잘못됨</td>
<td align="left">정확한 REST API 키 복사</td>
</tr>
<tr>
<td align="left">UnicodeEncodeError</td>
<td align="left">한글 주소 인코딩 안 됨</td>
<td align="left"><code>quote()</code> 함수 사용</td>
</tr>
<tr>
<td align="left">AccessDeniedError</td>
<td align="left">Authorization 헤더 없음</td>
<td align="left">Python 코드나 curl로 요청</td>
</tr>
</tbody></table>