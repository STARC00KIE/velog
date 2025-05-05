<h2 id="문제-상황">문제 상황</h2>
<ul>
<li>삼성전자(005930)의 연결 재무제표 데이터를 가져오기 위해 dapada.io API를 호출하는 코드 실행 중,</li>
<li>다음과 같은 오류가 발생함.</li>
</ul>
<pre><code>status_code: 502
response_text:
&lt;html&gt;
&lt;head&gt;&lt;title&gt;502 Bad Gateway&lt;/title&gt;&lt;/head&gt;
&lt;body&gt;&lt;center&gt;&lt;h1&gt;502 Bad Gateway&lt;/h1&gt;&lt;/center&gt;&lt;/body&gt;
&lt;/html&gt;

JSONDecodeError: Expecting value: line 1 column 1 (char 0)</code></pre><hr />
<h2 id="원인-분석">원인 분석</h2>
<ul>
<li><code>502 Bad Gateway</code>는 <strong>클라이언트(나)의 문제</strong>가 아니라, <strong>서버(dapada.io)의 문제</strong>를 의미한다.</li>
<li>정상적으로 요청을 보냈지만, 서버 내부 문제(백엔드 서버 장애, 프록시 문제 등)로 제대로 응답하지 못했음을 뜻함.</li>
<li>문제 발생 시 응답 내용은 HTML 형식인데, 코드에서 무조건 <code>response.json()</code>을 시도하면서 추가로 <code>JSONDecodeError</code>가 발생함.</li>
</ul>
<h3 id="결론">결론</h3>
<ul>
<li><strong>502 오류 자체는 내 코드 문제 아님.</strong></li>
</ul>
<hr />
<h2 id="해결-방법">해결 방법</h2>
<h3 id="1-api-요청-코드-수정">1. API 요청 코드 수정</h3>
<ul>
<li><code>status_code</code>를 확인하고, 정상 응답(200)일 때만 <code>response.json()</code>을 호출하도록 수정.</li>
<li>비정상 응답이 오면 예외 처리로 넘어가게 함.</li>
</ul>
<h3 id="수정된-코드-예시">수정된 코드 예시</h3>
<pre><code class="language-python">import requests
import pandas as pd
from urllib.parse import quote

def get_financials(stockCode, indicatorName, apiKey, consolidated=True, ttm=True):
    indicatorName_encoded = quote(indicatorName)

    if consolidated:
        if ttm:
            url = f&quot;https://api.dapada.io/company/getConsolidatedFinancialDataByTTM?apiKey={apiKey}&amp;indicatorName={indicatorName_encoded}&amp;stockCode={stockCode}&quot;
        else:
            url = f&quot;https://api.dapada.io/company/getConsolidatedFinancialDataByCUR?apiKey={apiKey}&amp;indicatorName={indicatorName_encoded}&amp;stockCode={stockCode}&quot;
    else:
        if ttm:
            url = f&quot;https://api.dapada.io/company/getSeparatedFinancialDataByTTM?apiKey={apiKey}&amp;indicatorName={indicatorName_encoded}&amp;stockCode={stockCode}&quot;
        else:
            url = f&quot;https://api.dapada.io/company/getSeparatedFinancialDataByCUR?apiKey={apiKey}&amp;indicatorName={indicatorName_encoded}&amp;stockCode={stockCode}&quot;

    headers = {&quot;apiKey&quot;: f&quot;{apiKey}&quot;}
    response = requests.get(url, headers=headers)
    print(&quot;status_code:&quot;, response.status_code)
    print(&quot;response_text:&quot;, response.text[:200])  # 긴 응답은 자름

    if response.status_code != 200:
        print(f&quot;요청 실패: {response.status_code} 에러 발생&quot;)
        return None

    try:
        result = response.json()
        return pd.DataFrame(result)
    except Exception as e:
        print(f&quot;JSON 변환 실패: {e}&quot;)
        return None</code></pre>
<hr />
<h2 id="추가로-알게-된-점">추가로 알게 된 점</h2>
<ul>
<li><code>502 Bad Gateway</code>는 서버 장애이므로, 클라이언트(나)는 기다리거나, 서버 상태를 확인하는 수밖에 없다.</li>
<li>코드 내에서는 방어적으로 작성해서, 서버 장애가 발생해도 프로그램이 죽지 않게 해야 한다.</li>
<li>특히, API 호출 시 한글 파라미터(<code>indicatorName='매출액'</code>)는 반드시 <code>quote()</code>로 URL 인코딩해야 함.</li>
<li>파일 경로 작성할 때도 <code>\</code>(역슬래시) 문제를 피하기 위해 <code>r'경로'</code> 또는 <code>\\</code> 두 번 써야 함.</li>
</ul>
<hr />
<h2 id="느낀-점">느낀 점</h2>
<ul>
<li>외부 API를 사용할 때는 서버 장애를 항상 염두에 두고 코드를 짜야 한다는 교훈을 얻음.</li>
<li>네트워크/서버 오류는 내 코드 문제일 수도 있지만, 대개는 서버 문제일 수 있다. 문제를 정확히 구분하는 것이 중요하다.</li>
<li>status_code 체크, 예외 처리(try-except), 재시도 로직까지 준비해두면 더 안정적인 프로그램을 만들 수 있을 것 같다.</li>
</ul>
<hr />
<h1 id="마무리">마무리</h1>
<ul>
<li>502 에러는 서버 문제  </li>
</ul>