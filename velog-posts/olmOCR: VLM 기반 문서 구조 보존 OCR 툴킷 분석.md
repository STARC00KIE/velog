<h2 id="설명">설명</h2>
<ul>
<li>PDF나 이미지 기반 문서를 읽기 순서가 자연스러운 텍스트 + 구조(표, 수식, 리스트) 형태로 변환하는 오픈소스 툴킷</li>
<li>VLM을 사용하여 이미지를 입력으로 받고, 문서의 레이아웃과 텍스트 구조를 보존한 출력물을(.md, .jsonl) 생성함</li>
</ul>
<hr />
<h2 id="아키텍처-구성-요소">아키텍처 구성 요소</h2>
<h3 id="1-입력-사전-처리">1. 입력 사전 처리</h3>
<ul>
<li>PDF -&gt; 페이지 이미지 변환: PDF 문서를 Poppler 등의 툴을 사용해 각 페이지를 이미지로 렌더링함</li>
<li>PDF 메타데이터 및 텍스트 블록 추출</li>
<li>문서 앵커링(현재 최신 모델에서는 fallback 모드에서만 )</li>
</ul>
<h3 id="2-모델-입력-및-처리vlm-기반">2. 모델 입력 및 처리(VLM 기반)</h3>
<ul>
<li>입력: 랜더링된 페이지 이미지, 앵커 텍스트/좌표 정보</li>
<li>모델 추론을 통해 텍스트 생성 및 markdown 형식으로 추출 할 수 있게 설계됨</li>
<li>Qwen2-VL 7B Instruct에서 fine-tuning 진행된 형태</li>
</ul>
<h3 id="3-출력-후처리">3. 출력 후처리</h3>
<ul>
<li>markdown 형태의 텍스트를 필요에 따라 일반 텍스트, 마크다운 파일, json 형태의 구조로 변환할 수 있음</li>
<li>해더 제거, 읽기 순서 재정렬 진행</li>
</ul>
<h3 id="4-확장성">4. 확장성</h3>
<ul>
<li>대규모 PDF 문서를 처리하기 위한 워크플로우가 제공되어 있음</li>
</ul>
<hr />
<h2 id="주요-특징-및-장점">주요 특징 및 장점</h2>
<ul>
<li>비전 + 언어 통합 모델</li>
<li>문서 내부 메타데이터 활용</li>
<li>구조 보존 출력</li>
<li>오픈소스 및 비용 효율성</li>
<li>다양한 문서 지원</li>
</ul>
<hr />
<h2 id="olmocr-모델-내부-구조">olmOCR 모델 내부 구조</h2>
<h3 id="1-기반-모델">1. 기반 모델</h3>
<ul>
<li>기반: Qwen2.5-VL 7B Instruct (멀티모달 LLM)</li>
<li>형태: 이미지 + 텍스트를 동시에 처리하는 VLM</li>
</ul>
<h3 id="2-주요-구성">2. 주요 구성</h3>
<table>
<thead>
<tr>
<th>블록</th>
<th>역할</th>
</tr>
</thead>
<tbody><tr>
<td><strong>Vision Encoder (ViT 계열, Qwen2.5-VL의 비전 백본을 상속함)</strong></td>
<td>문서 이미지를 시각 피처로 인코딩</td>
</tr>
<tr>
<td><strong>Projection Layer</strong></td>
<td>시각 피처를 텍스트 토큰 공간으로 사상</td>
</tr>
<tr>
<td><strong>Text Decoder</strong></td>
<td>이미지 정보를 기반으로 텍스트 (문서 내용 및 마크다운 구조) 생성</td>
</tr>
</tbody></table>
<h3 id="3-토크나이저--프로세서">3. 토크나이저 / 프로세서</h3>
<ul>
<li>AutoProcessor(Qwen 계열) : 텍스트를 토큰 단위로 쪼개고 ID로 변환함</li>
<li>Qwen2TokenizerFast : 멀티모달 입력을 한 번에 전처리함</li>
</ul>
<hr />
<h2 id="결과">결과</h2>
<ul>
<li>구조적인 형태로 반환<pre><code class="language-python">@dataclass(frozen=True)
class PageResponse:
  primary_language: Optional[str] # 텍스트에 사용된 언어
  is_rotation_valid: bool            # 페이지 회전 여부
  rotation_correction: int        # 회전해야 할 각도
  is_table: bool                    # 페이지가 표 중심인지 여부 확인
  is_diagram: bool                # 페이지가 그림 중심인지 여부 확인
  natural_text: Optional[str]        # 읽을 수 있는 자연어 텍스트 결과
  anchor_text: Optional[str]        # 앵커링 정보 넣었는지 확인
  raw_text: Optional[str]            # PDF에서 직접 추출한 원시 텍스트
  page_number: int                # 페이지 번호</code></pre>
<pre><code class="language-python">PDF (페이지) 
├──&gt; Poppler → base64 PNG 이미지 (시각 입력)
├──&gt; pypdf / pdfium → raw_text (좌표 기반 문자열)
├──&gt; 모델 입력: (image + raw_text + prompt)
└──&gt; 모델 출력: natural_text (정제된 문장)</code></pre>
</li>
</ul>
<hr />
<h2 id="현재-개선해야-할-점">현재 개선해야 할 점</h2>
<ul>
<li>병합되어져 있는 표가 마크다운에서 잘 출력되지 않고 있음</li>
<li>하나의 표가 두 페이지로 나누어져 있는 경우 두 표가 각각 다른 표로 도출됨<h3 id="참고자료">&lt; 참고자료 &gt;</h3>
</li>
<li><a href="https://github.com/pymupdf/PyMuPDF/issues/4030">https://github.com/pymupdf/PyMuPDF/issues/4030</a></li>
<li><a href="https://github.com/rednote-hilab/dots.ocr/tree/master?tab=readme-ov-file">https://github.com/rednote-hilab/dots.ocr/tree/master?tab=readme-ov-file</a></li>
<li><a href="https://discuss.huggingface.co/t/seeking-advice-reliable-ocr-ai-pipeline-for-extracting-complex-tables-from-reports/167296/5">https://discuss.huggingface.co/t/seeking-advice-reliable-ocr-ai-pipeline-for-extracting-complex-tables-from-reports/167296/5</a></li>
<li><a href="https://www.reddit.com/r/AI_Agents/comments/1midnry/seeking_advice_reliable_ocrai_pipeline_for/">https://www.reddit.com/r/AI_Agents/comments/1midnry/seeking_advice_reliable_ocrai_pipeline_for/</a></li>
</ul>
<hr />
<h2 id="주요-함수-및-클래스-정리">주요 함수 및 클래스 정리</h2>
<h3 id="main-함수-메인-실행-함수">main 함수: 메인 실행 함수</h3>
<ol>
<li>실행 전 torch, poppler(PDF 문서를 렌더링하기 위한 라이브러리, Linux 기반 시스템에서 기본적으로 사용됨) 작동 여부 점검</li>
<li><code>LocalMetrics</code> 클래스를 통해 파이프라인 진행 성공 기록 및 요약</li>
<li><code>process_pdf</code> 함수를 통해 페이지별로 OCR 처리 및 Markdown 및 Jsonl로 결과 저
장</li>
</ol>
<hr />
<h3 id="get_anchor_text-함수">get_anchor_text 함수</h3>
<ul>
<li>raw_text 내 좌표 패턴 분석</li>
<li>텍스트 블록 간 상대 위치 계산</li>
<li>제목/표/그림/각주 식별</li>
<li>시맨틱 구조화</li>
<li>요약 및 정제(최종적으로 1~2줄의 anchor 문장으로 반환)</li>
</ul>
<hr />
<h3 id="localmetrics-클래스">LocalMetrics 클래스</h3>
<ul>
<li>파이프라인 성능 기록 및 요약</li>
<li>프롬프트 토큰, 출력 토큰, 페이지 OCR 성공 여부 기록</li>
<li><code>def update</code>: 한 페이지 처리할 때마다 기록 업데이트</li>
<li><code>def summary</code>: 요약한 전체 결과 정리 및 반환</li>
</ul>
<hr />
<h3 id="process_pdf-함수">process_pdf 함수</h3>
<ul>
<li>하나의 PDF 파일을 처리해서 페이지 별 텍스트 리스트를 반환해 주는 함수</li>
<li>Markdown, json(학습 데이터셋을 제작할 때 사용되는 주요 형식) 저장 기능</li>
</ul>
<hr />
<h3 id="process_page-함수">process_page 함수</h3>
<ul>
<li>PDF 한 페이지를 모델로 OCR 처리하는 함수</li>
<li>PDF 한 페이지 -&gt; 이미지 변환 -&gt; 모델 추론 -&gt; 결과 파싱</li>
<li>페이지 처리 실패 시 재시도 최대 3번 실행</li>
<li>TEMPERATURE 0.1 ~ 1.0 까지 시도</li>
<li>스캔된 페이지 일 경우 회전 보정</li>
<li>모델 추론</li>
<li>YAML형식의 front matter 파싱</li>
<li>회전 검증 및 OCR 결과를 객체 형태로 반환(PageResult)</li>
<li>모델이 생성한 텍스트 결과는 <code>page_response</code>에 존재</li>
</ul>
<hr />
<h3 id="build_no_anchoring_yaml_prompt-함수">build_no_anchoring_yaml_prompt 함수</h3>
<ul>
<li>모델에서 주요하게 사용한 프롬프트<pre><code>&quot;Attached is one page of a document that you must process. &quot;
&quot;Just return the plain text representation of this document as if you were reading it naturally. Convert equations to LateX and tables to markdown.\n&quot;
&quot;Return your output as markdown, with a front matter section on top specifying values for the primary_language, is_rotation_valid, rotation_correction, is_table, and is_diagram parameters.</code></pre></li>
</ul>
<hr />
<h3 id="frontmatterparser-클래스">FrontMatterParser 클래스</h3>
<ul>
<li>PageResponse LLM 결과 메타데이터 정보 반환</li>
<li>모델 출력 구조화하는 역할을 함</li>
</ul>