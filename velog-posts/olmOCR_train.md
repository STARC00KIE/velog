<h2 id="1-개요">1. 개요</h2>
<h3 id="a-요약">a. 요약</h3>
<ul>
<li><code>Qwen2.5-VL-7B</code> 기반으로 학습 진행</li>
<li>train 데이터는 단일 페이지 PDF + 해당 마크다운 파일 쌍으로 구성되어 있음</li>
<li>출력은 마크다운 텍스트 구조로 구성됨<h3 id="b-전체적인-학습-파이프라인-그림">b. 전체적인 학습 파이프라인 그림</h3>
<a href="https://mermaid.live/edit#pako:eNp9VG1r21YU_iuH-2HIYDvRi7tWjEIdx3SQklDGCpv6QbFVx9SWgiyt60IgzZRAnYZka7olzC4OddpuGKrGaasx78_so-_Vf9jRW2y5pf5gvdznnPM8zzlHG6RiVDUik1wup-hW3WpoMiw3mssLt4H7dulWBugbjzkeO3VZ7xn4z05Y-x34T56w7oV_5NDuiHU9RQ-ja6a6vgbflBQd8NeyV6MXCmHPd2jvDLiv9XXbamUUEiGC343v8djph7mDpCPgKoZ-r17LP1SbDYTenWCLiI0J0H03IOC4bGcPOHraYf8MMl-tmnPXuZVSOQu3VPN-1Xigg7-zz9p9v-2lUy1gqpt2rVbXa1BWKxrctFfD8Byw7QHrObFSetgB-tdruu_Fp4FmrIaGOB3g_N2e_2hAt4-RDOttTWpoelXRP_JhEtzuA7diGhWtlbajWje1ilU3dFi6PXlb4pEunwf_5Hh8_i_EflH3IOYGmJUe_RlTnPIv9HTvbXyQEhxFzqX0BGmedlJGlQQsLeQnhgOaw86P6ctBRMB12d_HwH7uMiepgx34b_dXhAej82oL6MEJ6z0COtxCAYmPSV8g9ND1T46Sk7jDYWKuqFqVtQyM3w0wf5qZiMzE_KUF02PKJUlevEaBmThz2TAfqGZ1rqhW7gc3sKK2WsD2-v5vj5Pm7x7iM7dkYF9gPHTYthufxGXG7hbr_xJK_n0nNqXtpYlJSEzCbh08RnToEju_wDnxDwa4LIFmnBX2_Cyp-WI09tzAIZRI22dJILf4g9rIzLhy2hl_QBaeS0-7wN35opgAPl0iRWx6oCCXu47NjS5idJE-N7vsfSfc4WXb-miJF1HwtP8zW8PNcEuvYnlqq0N1UQxKywLOG-alzuEnN-sG0obLz0dQd3ihkEgLH0GKMeSPQzr0JkOcoIQItRCjpjc_FjCTL_ovSVHA-NwdD0eXVofIxRnIcBSQixoWQ8okS2pmvUpky7S1LGlqZlMNHslGEKwQa01ragqR8baKH7LA6k2MWVf17wyjmYSZhl1bI_I9tdHCJ3u9qlpaqa5iw5qXb020SzMXDFu3iCwVrophFiJvkB-JzPNivvClNH-NxwN-fp7ns-QhkXOiUMgXBEkSrkj8NZEXN7Pkp7Aun-clXhIKIl4EocCLwub_gGyvCQ"><img alt="" src="https://mermaid.ink/img/pako:eNp9VG1r21YU_iuH-2HIYDvRi7tWjEIdx3SQklDGCpv6QbFVx9SWgiyt60IgzZRAnYZka7olzC4OddpuGKrGaasx78_so-_Vf9jRW2y5pf5gvdznnPM8zzlHG6RiVDUik1wup-hW3WpoMiw3mssLt4H7dulWBugbjzkeO3VZ7xn4z05Y-x34T56w7oV_5NDuiHU9RQ-ja6a6vgbflBQd8NeyV6MXCmHPd2jvDLiv9XXbamUUEiGC343v8djph7mDpCPgKoZ-r17LP1SbDYTenWCLiI0J0H03IOC4bGcPOHraYf8MMl-tmnPXuZVSOQu3VPN-1Xigg7-zz9p9v-2lUy1gqpt2rVbXa1BWKxrctFfD8Byw7QHrObFSetgB-tdruu_Fp4FmrIaGOB3g_N2e_2hAt4-RDOttTWpoelXRP_JhEtzuA7diGhWtlbajWje1ilU3dFi6PXlb4pEunwf_5Hh8_i_EflH3IOYGmJUe_RlTnPIv9HTvbXyQEhxFzqX0BGmedlJGlQQsLeQnhgOaw86P6ctBRMB12d_HwH7uMiepgx34b_dXhAej82oL6MEJ6z0COtxCAYmPSV8g9ND1T46Sk7jDYWKuqFqVtQyM3w0wf5qZiMzE_KUF02PKJUlevEaBmThz2TAfqGZ1rqhW7gc3sKK2WsD2-v5vj5Pm7x7iM7dkYF9gPHTYthufxGXG7hbr_xJK_n0nNqXtpYlJSEzCbh08RnToEju_wDnxDwa4LIFmnBX2_Cyp-WI09tzAIZRI22dJILf4g9rIzLhy2hl_QBaeS0-7wN35opgAPl0iRWx6oCCXu47NjS5idJE-N7vsfSfc4WXb-miJF1HwtP8zW8PNcEuvYnlqq0N1UQxKywLOG-alzuEnN-sG0obLz0dQd3ihkEgLH0GKMeSPQzr0JkOcoIQItRCjpjc_FjCTL_ovSVHA-NwdD0eXVofIxRnIcBSQixoWQ8okS2pmvUpky7S1LGlqZlMNHslGEKwQa01ragqR8baKH7LA6k2MWVf17wyjmYSZhl1bI_I9tdHCJ3u9qlpaqa5iw5qXb020SzMXDFu3iCwVrophFiJvkB-JzPNivvClNH-NxwN-fp7ns-QhkXOiUMgXBEkSrkj8NZEXN7Pkp7Aun-clXhIKIl4EocCLwub_gGyvCQ?type=png" /></a></li>
</ul>
<hr />
<h2 id="2-과정">2. 과정</h2>
<h3 id="a-파인튜닝-목적">a. 파인튜닝 목적</h3>
<ul>
<li>기존의 Qwen2.5VL은 범용 이미지 캡션이나 차트 분석에는 강하지만, 문서 내 텍스트 레이아웃, 표, 구조화 정보에는 약함</li>
<li>따라서 파인튜닝을 통해 문제 해결 진행</li>
</ul>
<h3 id="b-데이터-구조">b. 데이터 구조</h3>
<ul>
<li>단일 페이지 단위의 (PDF이미지, Markdown) 쌍<pre><code class="language-YAML">data/
├── page_00001.pdf
├── page_00001.md
├── page_00002.pdf
├── page_00002.md
...</code></pre>
<h3 id="c-학습-과정-단계별-요약">c. 학습 과정 단계별 요약</h3>
<table>
<thead>
<tr>
<th>단계</th>
<th>설명</th>
</tr>
</thead>
<tbody><tr>
<td><strong>1. 데이터 로드</strong></td>
<td><code>BaseMarkdownPDFDataset</code>으로 이미지-텍스트 쌍 로딩</td>
</tr>
<tr>
<td><strong>2. Processor 적용</strong></td>
<td>Qwen2VLProcessor가 이미지 패치화 + 텍스트 토큰화 수행</td>
</tr>
<tr>
<td><strong>3. DataCollator</strong></td>
<td>배치 구성 시 padding, attention mask, label shift 등 처리</td>
</tr>
<tr>
<td><strong>4. Forward Pass</strong></td>
<td>Vision Encoder가 이미지 feature 추출 → Text Decoder로 전달</td>
</tr>
<tr>
<td><strong>5. Loss 계산</strong></td>
<td>생성된 토큰과 정답 토큰 간 CrossEntropy Loss 계산</td>
</tr>
<tr>
<td><strong>6. Optimizer 업데이트</strong></td>
<td>AdamW로 weight 업데이트</td>
</tr>
<tr>
<td><strong>7. 스케줄러</strong></td>
<td><code>get_scheduler()</code>로 learning rate decay 적용</td>
</tr>
<tr>
<td><strong>8. Logging</strong></td>
<td>W&amp;B로 loss, lr, step, validation metric 기록</td>
</tr>
</tbody></table>
</li>
</ul>
<h3 id="d-하이퍼-파라미터-설정">d. 하이퍼 파라미터 설정</h3>
<ul>
<li><code>..._1025_FP8</code> 버전에서는 <code>qwen25_vl_olmocrv4_rotation_1epoch_mix_1025_filtered.yaml</code> 설정을 사용함</li>
</ul>
<table>
<thead>
<tr>
<th>항목</th>
<th>설정값</th>
</tr>
</thead>
<tbody><tr>
<td>모델</td>
<td>Qwen/Qwen2.5-VL-7B-Instruct</td>
</tr>
<tr>
<td>배치 크기</td>
<td>1 * 32 (유효 배치 크기)</td>
</tr>
<tr>
<td>학습률</td>
<td>2e-5</td>
</tr>
<tr>
<td>토큰 최대 길이</td>
<td>8192</td>
</tr>
<tr>
<td>정밀도(precision)</td>
<td>bfloat16 (torch compile + flash-attention 2)</td>
</tr>
<tr>
<td>최적화(optimizer)</td>
<td>adamw_torch</td>
</tr>
<tr>
<td>기울기 클리핑(gradient clipping)</td>
<td>1.0</td>
</tr>
</tbody></table>
<h3 id="e-파인튜닝-원리-요약">e. 파인튜닝 원리 요약</h3>
<table>
<thead>
<tr>
<th>단계</th>
<th>설명</th>
</tr>
</thead>
<tbody><tr>
<td><strong>Encoder는 고정(Frozen)</strong></td>
<td>Swin 기반 Vision Encoder는 대부분의 경우 파라미터를 고정(freeze)하여, 시각적 피처 추출 능력을 유지하면서 학습 효율을 중가</td>
</tr>
<tr>
<td><strong>Decoder 중심 학습</strong></td>
<td>Qwen2.5 Text Decoder 부분이 Markdown 구조 예측을 학습하며, 텍스트 토큰 예측 능력을 강화</td>
</tr>
<tr>
<td><strong>Cross-Attention 강화</strong></td>
<td>Vision Encoder의 이미지 특징 벡터와 Text Decoder의 토큰 시퀀스 사이의 Cross-Attention을 통해 이미지 영역별 텍스트 위치 및 문맥 정렬(alignment)을 학습.</td>
</tr>
<tr>
<td><strong>Teacher Forcing 사용</strong></td>
<td>학습 중 실제 정답 토큰을 입력해 다음 토큰을 예측하게 하여, 안정적인 수렴을 유도.</td>
</tr>
<tr>
<td><strong>손실 계산 (CrossEntropy Loss)</strong></td>
<td>예측 토큰과 정답 토큰 간 차이를 CrossEntropyLoss로 계산하며, 문장 구조까지 반영.</td>
</tr>
<tr>
<td><strong>bfloat16 + Flash-Attention 2 활용</strong></td>
<td><code>torch.compile</code>과 <code>FlashAttention 2</code>로 GPU 메모리 효율을 높이고, 긴 시퀀스(8192 토큰)에서도 빠른 학습이 가능하도록 최적화.</td>
</tr>
<tr>
<td><strong>Optimizer 및 Gradient Clipping</strong></td>
<td><code>adamw_torch</code>를 사용해 weight decay를 안정적으로 조정하고, <code>gradient clipping=1.0</code>으로 폭주 방지.</td>
</tr>
<tr>
<td><strong>학습 로그 및 수렴 모니터링</strong></td>
<td>학습률, 손실, step별 Markdown 예측 결과를 시각화하면서 수렴 여부를 추적.</td>
</tr>
</tbody></table>
<hr />
<h2 id="3-추가">3. 추가</h2>
<h3 id="a-olmocrtraindata--폴더-안에-존재하는-python-파일들의-역할">a. olmocr/train/data  폴더 안에 존재하는 python 파일들의 역할</h3>
<h4 id="build_openai_batch_from_olmocrmixpy-">build_openai_batch_from_olmocrmix.py :</h4>
<ul>
<li>OLMoCR-mix로 전처리된 폴더(예: processed_xx_*) 안의 단일 페이지 PDF들을 순회하면서,</li>
<li>각 단일 페이지 PDF를 PNG(Base64) 로 렌더링하고,</li>
<li>(이미지 가로×세로)로 프롬프트를 만들고,</li>
<li>OpenAI Batch API 형식의 chat.completions 요청 JSON 한 줄씩을 JSONL 파일로 누적 저장함</li>
<li>JSONL 파일은 99MB(MAX_FILE_SIZE)를 넘지 않도록 자동으로 롤오버 진행 (파일명: batch_requests_0000.jsonl, ..._0001.jsonl …)</li>
</ul>
<h3 id="buildsilverpy-">buildsilver.py :</h3>
<ul>
<li>무작위 표본 추출(저수지 샘플링)로 S3/로컬의 PDF 경로를 모으고, 각 PDF에서 일부 페이지만 샘플해서 페이지 이미지를 Base64 PNG로 렌더링한 뒤, OpenAI Batch API에 넣을 JSONL 요청을 99MB 단위로 롤오버하며 저장하는 파일</li>
</ul>
<h3 id="clean_olmocrmixpy-">clean_olmocrmix.py :</h3>
<ul>
<li>이 파일은 OLMoCR-mix 데이터셋의 OCR 결과(md 파일) 와 그에 대응하는 PDF 한 페이지 이미지를 함께 활용해서 ChatGPT(구체적으로 gpt-4o 계열) 로 OCR 텍스트를 “정제(clean-up)”하는 파이프라인</li>
</ul>
<h3 id="prepare_loc_transcriptspy-">prepare_loc_transcripts.py :</h3>
<ul>
<li>미국 의회 데이터 수집 → olmOCR 학습용 구조로 정리 </li>
</ul>
<h3 id="prepare_national_archive_transcriptspy-">prepare_national_archive_transcripts.py :</h3>
<ul>
<li>국립문서보관소 NARA 데이터 수집→ olmOCR 학습용 구조로 정리 </li>
</ul>
<h3 id="prepare_olmocrmixpy-">prepare_olmocrmix.py :</h3>
<ul>
<li>허깅페이스<code>allenai/olmOCR-mix</code> 데이터 수집→ olmOCR 학습용 구조로 정리 </li>
</ul>
<h3 id="prepare_workspacepy-">prepare_workspace.py :</h3>
<ul>
<li><code>workspace/results</code> 폴더 안의 <strong>파이프라인 결과(JSONL)</strong>를 페이지 단위의 (MD+단일 PDF) 학습 데이터로 뽑아 파인튜닝용 포맷으로 정리해 주는 변환기</li>
</ul>
<h3 id="process_openai_batch_resultspy-">process_openai_batch_results.py :</h3>
<ul>
<li><strong>OpenAI 배치 응답(JSONL)</strong>을 읽어 원본 PDF를 복사하고, 응답의 구조화 필드로 FrontMatter+본문이 있는 .md를 만들어, 원래 구조를 미러링한 학습·후처리용 산출물(MD+PDF) 폴더를 구성</li>
</ul>
<h3 id="renderpdfpy-">renderpdf.py :</h3>
<ul>
<li>PDF→(해상도 산출)→PNG/WEBP(Base64) 생성과 Base64 PNG의 폭·높이 빠른 추출</li>
</ul>
<h3 id="repackage_olmocrmixpy-">repackage_olmocrmix.py :</h3>
<ul>
<li>로컬의 (MD+PDF) 학습 데이터셋을 업로드하기 좋은 형태로 변환</li>
</ul>
<h3 id="runopenaibatchpy-">runopenaibatch.py :</h3>
<ul>
<li>대량 JSONL 배치 업로드·상태 추적·결과 수집·용량 관리를 한 번에 처리하는 Batch 운영 자동화 파일</li>
</ul>
<hr />
<h2 id="출처">출처</h2>
<ul>
<li><a href="https://github.com/allenai/olmocr">https://github.com/allenai/olmocr</a></li>
</ul>