<h2 id="1-개요">1. 개요</h2>
<h3 id="a-요약">a. 요약</h3>
<ul>
<li><code>Qwen2.5-VL-7B</code> 기반으로 SFT(Supervised Fine Tuning) 학습 진행</li>
<li>LORA 적용하지 않고, 모델 전체 파라미터 업데이트</li>
<li>train 데이터는 단일 페이지 PDF + 해당 마크다운 파일 쌍으로 구성되어 있음</li>
<li>출력은 마크다운 텍스트 구조로 구성됨<h3 id="b-전체적인-학습-파이프라인-그림">b. 전체적인 학습 파이프라인 그림</h3>
<a href="https://mermaid.live/edit#pako:eNp9VG1r21YU_iuH-2HIYDvRi7tWjEIdx3SQklDGCpv6QbFVx9SWgiyt60IgzZRAnYZka7olzC4OddpuGKrGaasx78_so-_Vf9jRW2y5pf5gvdznnPM8zzlHG6RiVDUik1wup-hW3WpoMiw3mssLt4H7dulWBugbjzkeO3VZ7xn4z05Y-x34T56w7oV_5NDuiHU9RQ-ja6a6vgbflBQd8NeyV6MXCmHPd2jvDLiv9XXbamUUEiGC343v8djph7mDpCPgKoZ-r17LP1SbDYTenWCLiI0J0H03IOC4bGcPOHraYf8MMl-tmnPXuZVSOQu3VPN-1Xigg7-zz9p9v-2lUy1gqpt2rVbXa1BWKxrctFfD8Byw7QHrObFSetgB-tdruu_Fp4FmrIaGOB3g_N2e_2hAt4-RDOttTWpoelXRP_JhEtzuA7diGhWtlbajWje1ilU3dFi6PXlb4pEunwf_5Hh8_i_EflH3IOYGmJUe_RlTnPIv9HTvbXyQEhxFzqX0BGmedlJGlQQsLeQnhgOaw86P6ctBRMB12d_HwH7uMiepgx34b_dXhAej82oL6MEJ6z0COtxCAYmPSV8g9ND1T46Sk7jDYWKuqFqVtQyM3w0wf5qZiMzE_KUF02PKJUlevEaBmThz2TAfqGZ1rqhW7gc3sKK2WsD2-v5vj5Pm7x7iM7dkYF9gPHTYthufxGXG7hbr_xJK_n0nNqXtpYlJSEzCbh08RnToEju_wDnxDwa4LIFmnBX2_Cyp-WI09tzAIZRI22dJILf4g9rIzLhy2hl_QBaeS0-7wN35opgAPl0iRWx6oCCXu47NjS5idJE-N7vsfSfc4WXb-miJF1HwtP8zW8PNcEuvYnlqq0N1UQxKywLOG-alzuEnN-sG0obLz0dQd3ihkEgLH0GKMeSPQzr0JkOcoIQItRCjpjc_FjCTL_ovSVHA-NwdD0eXVofIxRnIcBSQixoWQ8okS2pmvUpky7S1LGlqZlMNHslGEKwQa01ragqR8baKH7LA6k2MWVf17wyjmYSZhl1bI_I9tdHCJ3u9qlpaqa5iw5qXb020SzMXDFu3iCwVrophFiJvkB-JzPNivvClNH-NxwN-fp7ns-QhkXOiUMgXBEkSrkj8NZEXN7Pkp7Aun-clXhIKIl4EocCLwub_gGyvCQ"><img alt="" src="https://mermaid.ink/img/pako:eNp9VG1r21YU_iuH-2HIYDvRi7tWjEIdx3SQklDGCpv6QbFVx9SWgiyt60IgzZRAnYZka7olzC4OddpuGKrGaasx78_so-_Vf9jRW2y5pf5gvdznnPM8zzlHG6RiVDUik1wup-hW3WpoMiw3mssLt4H7dulWBugbjzkeO3VZ7xn4z05Y-x34T56w7oV_5NDuiHU9RQ-ja6a6vgbflBQd8NeyV6MXCmHPd2jvDLiv9XXbamUUEiGC343v8djph7mDpCPgKoZ-r17LP1SbDYTenWCLiI0J0H03IOC4bGcPOHraYf8MMl-tmnPXuZVSOQu3VPN-1Xigg7-zz9p9v-2lUy1gqpt2rVbXa1BWKxrctFfD8Byw7QHrObFSetgB-tdruu_Fp4FmrIaGOB3g_N2e_2hAt4-RDOttTWpoelXRP_JhEtzuA7diGhWtlbajWje1ilU3dFi6PXlb4pEunwf_5Hh8_i_EflH3IOYGmJUe_RlTnPIv9HTvbXyQEhxFzqX0BGmedlJGlQQsLeQnhgOaw86P6ctBRMB12d_HwH7uMiepgx34b_dXhAej82oL6MEJ6z0COtxCAYmPSV8g9ND1T46Sk7jDYWKuqFqVtQyM3w0wf5qZiMzE_KUF02PKJUlevEaBmThz2TAfqGZ1rqhW7gc3sKK2WsD2-v5vj5Pm7x7iM7dkYF9gPHTYthufxGXG7hbr_xJK_n0nNqXtpYlJSEzCbh08RnToEju_wDnxDwa4LIFmnBX2_Cyp-WI09tzAIZRI22dJILf4g9rIzLhy2hl_QBaeS0-7wN35opgAPl0iRWx6oCCXu47NjS5idJE-N7vsfSfc4WXb-miJF1HwtP8zW8PNcEuvYnlqq0N1UQxKywLOG-alzuEnN-sG0obLz0dQd3ihkEgLH0GKMeSPQzr0JkOcoIQItRCjpjc_FjCTL_ovSVHA-NwdD0eXVofIxRnIcBSQixoWQ8okS2pmvUpky7S1LGlqZlMNHslGEKwQa01ragqR8baKH7LA6k2MWVf17wyjmYSZhl1bI_I9tdHCJ3u9qlpaqa5iw5qXb020SzMXDFu3iCwVrophFiJvkB-JzPNivvClNH-NxwN-fp7ns-QhkXOiUMgXBEkSrkj8NZEXN7Pkp7Aun-clXhIKIl4EocCLwub_gGyvCQ?type=png" /></a></li>
</ul>
<hr />
<h2 id="2-과정">2. 과정</h2>
<h3 id="a-파인튜닝-목적">a. 파인튜닝 목적</h3>
<ul>
<li>기존의 Qwen2.5VL은 이미지 캡션이나 차트 분석에는 강하지만, 문서 내 텍스트 레이아웃, 표, 구조화 정보에는 약함</li>
<li>따라서 파인튜닝을 통해 문제 해결 진행</li>
</ul>
<h3 id="b-데이터-구조">b. 데이터 구조</h3>
<ul>
<li>단일 페이지 단위의 (PDF이미지, Markdown) 쌍<pre><code class="language-YAML">### 학습 데이터셋 구조
data/
├── page_00001.pdf
├── page_00001.md
├── page_00002.pdf
├── page_00002.md
...

</code></pre>
</li>
</ul>
<h3 id="마크다운-포맷-예시">마크다운 포맷 예시</h3>
<hr />
<p>primary_language: en
is_rotation_valid: True
rotation_correction: 0
is_table: False
is_diagram: False</p>
<hr />
<p>Document text goes here...</p>
<p>```</p>
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
<td>배치 구성 시 padding, attention mask 등 처리</td>
</tr>
<tr>
<td><strong>4. Forward Pass</strong></td>
<td>이미지 토큰과 텍스트 토큰 이용하여 loss값 생성</td>
</tr>
<tr>
<td><strong>5. Backward Pass</strong></td>
<td>loss값 기준으로 gradient 값 계산</td>
</tr>
<tr>
<td><strong>6. Optimizer 업데이트</strong></td>
<td>gradient 이용하여 AdamW로 weight 업데이트</td>
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
<hr />
<h2 id="3-grpogenerative-reward-based-policy-optimization-강화학습-알고리즘">3. GRPO(Generative Reward-based Policy Optimization) 강화학습 알고리즘</h2>
<h3 id="a-강화학습-과정">a. 강화학습 과정</h3>
<ol>
<li>기존의 파인튜닝을 진행한 VL 모델을 가져옴</li>
<li>PDF 페이지 이미지와 텍스틀를 모델에 입력하여 결과를 생성함</li>
<li>생성된 여러 결과물을 다양한 <strong>보상 함수(Reward Functions)</strong>를 사용해 평가하고 점수 계산</li>
<li>높은 점수를 받은 결과물과 유사한 결과가 더 잘 나오도록 모델의 가중치 업데이트</li>
</ol>
<h3 id="b-보상-함수-종류">b. 보상 함수 종류</h3>
<ul>
<li>olmocr_bench_reward: <code>JSONL</code>에 정의된 테스트들을 모델 출력 결과랑 비교하여, 통과한 테스트 비율을 보상 점수로 반환함</li>
<li>bench_edit_distance_reward: claude_original 폴더(클로드가 제작한 모델의 학습/평가 시 &quot;정답 텍스트&quot; 참조용 폴더)에 있는 고품질 참조 텍스트와 모델이 생성한 텍스트 간의 <strong>편집 거리(한 문자열을 다른 문자열로 바꾸기 위해 삽입, 삭제, 치환 같은 최소한의 편집 연산 횟수를 계산한 거리)</strong>를 계산</li>
<li>medoid_reward: 모델이 동일한 입력에 대해 여러 개의 결과물을 생성했을 때, 그 결과물들 사이의 일관성을 평가</li>
<li>reward_front_matter: YAML Frontmatter가 올바르게 파싱되는지 확인</li>
<li>reward_element_count: <code>claude_original</code> 참조 텍스트에 포함된 특정 요소<code>HTML &lt;table&gt;, LaTeX</code> 수식 등)의 개수 비교</li>
<li>reward_eos: 모델이 문장 끝을 나타내는 EOS(End-of-Sequence) 토큰을 생성물 마지막에 제대로 포함했는지 확인</li>
</ul>
<hr />
<h2 id="4-데이터-생성">4. 데이터 생성</h2>
<h3 id="a-olmocr-mix-0225">a. olmOCR-mix-0225</h3>
<ul>
<li><p>gpt-4.1과 각 페이지의 디지털 원본 콘텐츠를 보존하는 특수한 프롬프팅 전략을 사용하여 자연스러운 읽기 순서대로 일반 텍스트로 OCR 처리된 약 270,000개의 PDF 페이지로 구성된 데이터 세트</p>
</li>
<li><p>약 240만 개 PDF 문서들을 인터넷 상 공개된 대형 PDF 저장소에서 크롤링하여 확보했으며, 또한 공개 도메인(public-domain) 자료들도 활용</p>
</li>
<li><p>수작업으로 데이터셋 검증(수작업 관련 비율은 찾지 못함)</p>
</li>
<li><p>필터링 및 샘플링 절차</p>
<ul>
<li>언어 필터: 영어 문서 중심이며, 비영어 문서는 제거함</li>
<li>파일 형식, 구조 필터: PDF 내부 구조가 너무 단순하거나 텍스트가 거의 없는 문서, 스팸 키워드 포함 문서, 채워지는 양식(form) 문서 등은 제외됨</li>
<li>페이지 샘플링: 각 PDF에서 무작위로 3페이지 정도를 추출해서 학습용으로 사용</li>
</ul>
</li>
<li><p>데이터셋 수</p>
</li>
</ul>
<table>
<thead>
<tr>
<th align="left">Subset</th>
<th align="left">Train</th>
<th align="left">Eval</th>
<th align="left">Total</th>
</tr>
</thead>
<tbody><tr>
<td align="left">00_documents</td>
<td align="left">231,668</td>
<td align="left">1,122</td>
<td align="left">232,790</td>
</tr>
<tr>
<td align="left">01_books</td>
<td align="left">16,575</td>
<td align="left">899</td>
<td align="left">17,474</td>
</tr>
<tr>
<td align="left">02_loc_transcripts</td>
<td align="left">9,891</td>
<td align="left">98</td>
<td align="left">9,989</td>
</tr>
<tr>
<td align="left">03_national_archives</td>
<td align="left">9,828</td>
<td align="left">169</td>
<td align="left">9,997</td>
</tr>
<tr>
<td align="left">Total</td>
<td align="left">267,962</td>
<td align="left">2,288</td>
<td align="left">270,250</td>
</tr>
</tbody></table>
<ul>
<li>각각의 데이터셋 분할이 어떻게 만들어졌는지 정리</li>
</ul>
<table>
<thead>
<tr>
<th>Split 이름</th>
<th>출처</th>
<th>전사 방식</th>
<th>ChatGPT 역할</th>
</tr>
</thead>
<tbody><tr>
<td><code>00_documents</code></td>
<td>일반 문서</td>
<td>이미지 → 텍스트 직접 전사</td>
<td>고품질 자연언어 전사 생성</td>
</tr>
<tr>
<td><code>01_books</code></td>
<td>책 페이지</td>
<td>이미지 → 텍스트 직접 전사</td>
<td>고품질 자연언어 전사 생성</td>
</tr>
<tr>
<td><code>02_loc_transcripts</code></td>
<td>Library of Congress</td>
<td>기존 전사문 정제</td>
<td>품질 정제 및 노이즈 제거</td>
</tr>
<tr>
<td><code>03_national_archives</code></td>
<td>National Archives</td>
<td>기존 전사문 정제</td>
<td>품질 정제 및 노이즈 제거</td>
</tr>
</tbody></table>
<h3 id="b-데이터셋-생성-파이프라인">b. 데이터셋 생성 파이프라인</h3>
<p><a href="https://mermaid.live/edit#pako:eNqtlW1v2lYUx7_K0a0qgQYE82isKBJPTkhfNGorTRpU1sXcgBVjW8akyUImplApa7JV3aiGNtiyaVs6KZNoskSZlk-EL99h1zYND3sxRQsvwNc-9_f_n3PuwXtI1isECahqYqMGz3IlDdgnXSwh-8shHfw57gyBHvbo6Zvlsrni-5iUYSMnNmAJCppFTI1YkDblmrJNIKPrWw1_CT2HYHClRQ964-6xffp5CzIO7eyadvpAr7r0qg_28DXYv3fHB-2pyujyjHbeOyrLjqcVn2ESA5tE0tW6Lpt1ZSdk7PqXl9yHTlgQPKh99BfQy7593Ibo-Ksew9HT9kRpEjcv5WuaagAMXCUBUCp-oCdv7d_OmPGS5qWfcTMoofHXh_T0EEbDPu2cgG9141kwFuJYii3Is5xGFyeTCEagJ30YHx87Ct2OPbihg2u3Ysz94-yTILMf5MKRONhH70YXHf80z3JTUSuSbhANK1IZW3JN2jT1-lzak6zhI5jZ01DUbWJOn84kkHcTyDgwSG8UgH7Xped_eP5ugB4MWKVbIBYfM9V0AbzASdBiH-7g77mn7n2Lix6-fWn_1Le_8bo_Oh-OLm4mR6sFqwtWznusI24gHbyxjy5Zhdv0h1-nrhpE-1cB5uRXXfnx9x2P1YK1IuvDra7XMPccXh3aP37B7vRH74dTAVklWPvPJNc8lbc92u8A7VyPX10zYMcVLBSfNssNNiDTiobDUkWXm3WiWc4IhTmp7AyNcxmRVF2WLBNrDdlUDO95VNKwpegaViXsTVljTr7gyrOy0r_PJiVqwXqRTQP9-SXMTPBt9T5bWjiQQbLDRGWLVJbYr6IFgGxjdU5l3VMZDsevWVqPimvNalXRqiBimUzb6tCxqjrHZFFjjvbwIdBXv7B5dI6ib3TeZr2A0XWbdt_5vYiGtasSSMOmoqrCA1EUI9lsoGGZ-hYRHmST6Ug4PFkGXygVqyZwobixE5B1VTeFsorlrVlO5p44-Qknz-Xi-eQtJ5VIRtOJO3DED374bH7GT4aPx-J38bN6T5y1e-IU7omzPuHk0nlenHISWT6fEe_AefS_OCjAXolKBQmW2SQBVCdmHTtLtOdolJBVI3VSQgK7rGBzq4RK2j7bY2DtE12vf9hm6s1qDQmbWG2wVdOoYIvkFMxetvXbuyb7JyNmVm9qFhKifCzhUpCwh3aQwPGxUCIV57g4l0hGEvFYLIB2kRCM8lwoFeYjkXgqFeEj4dR-AH3qCnOhCJfgeC6Visb4WCyV3P8H9CsNQg"><img alt="" src="https://mermaid.ink/img/pako:eNqtlW1v2lYUx7_K0a0qgQYE82isKBJPTkhfNGorTRpU1sXcgBVjW8akyUImplApa7JV3aiGNtiyaVs6KZNoskSZlk-EL99h1zYND3sxRQsvwNc-9_f_n3PuwXtI1isECahqYqMGz3IlDdgnXSwh-8shHfw57gyBHvbo6Zvlsrni-5iUYSMnNmAJCppFTI1YkDblmrJNIKPrWw1_CT2HYHClRQ964-6xffp5CzIO7eyadvpAr7r0qg_28DXYv3fHB-2pyujyjHbeOyrLjqcVn2ESA5tE0tW6Lpt1ZSdk7PqXl9yHTlgQPKh99BfQy7593Ibo-Ksew9HT9kRpEjcv5WuaagAMXCUBUCp-oCdv7d_OmPGS5qWfcTMoofHXh_T0EEbDPu2cgG9141kwFuJYii3Is5xGFyeTCEagJ30YHx87Ct2OPbihg2u3Ysz94-yTILMf5MKRONhH70YXHf80z3JTUSuSbhANK1IZW3JN2jT1-lzak6zhI5jZ01DUbWJOn84kkHcTyDgwSG8UgH7Xped_eP5ugB4MWKVbIBYfM9V0AbzASdBiH-7g77mn7n2Lix6-fWn_1Le_8bo_Oh-OLm4mR6sFqwtWznusI24gHbyxjy5Zhdv0h1-nrhpE-1cB5uRXXfnx9x2P1YK1IuvDra7XMPccXh3aP37B7vRH74dTAVklWPvPJNc8lbc92u8A7VyPX10zYMcVLBSfNssNNiDTiobDUkWXm3WiWc4IhTmp7AyNcxmRVF2WLBNrDdlUDO95VNKwpegaViXsTVljTr7gyrOy0r_PJiVqwXqRTQP9-SXMTPBt9T5bWjiQQbLDRGWLVJbYr6IFgGxjdU5l3VMZDsevWVqPimvNalXRqiBimUzb6tCxqjrHZFFjjvbwIdBXv7B5dI6ib3TeZr2A0XWbdt_5vYiGtasSSMOmoqrCA1EUI9lsoGGZ-hYRHmST6Ug4PFkGXygVqyZwobixE5B1VTeFsorlrVlO5p44-Qknz-Xi-eQtJ5VIRtOJO3DED374bH7GT4aPx-J38bN6T5y1e-IU7omzPuHk0nlenHISWT6fEe_AefS_OCjAXolKBQmW2SQBVCdmHTtLtOdolJBVI3VSQgK7rGBzq4RK2j7bY2DtE12vf9hm6s1qDQmbWG2wVdOoYIvkFMxetvXbuyb7JyNmVm9qFhKifCzhUpCwh3aQwPGxUCIV57g4l0hGEvFYLIB2kRCM8lwoFeYjkXgqFeEj4dR-AH3qCnOhCJfgeC6Visb4WCyV3P8H9CsNQg?type=png" /></a></p>
<h3 id="a-olmocrtraindata--폴더-안에-존재하는-python-파일들의-역할">a. olmocr/train/data  폴더 안에 존재하는 python 파일들의 역할</h3>
<h3 id="--데이터-렌더링-유틸">- 데이터 렌더링 유틸</h3>
<h3 id="renderpdfpy-">renderpdf.py :</h3>
<ul>
<li>PDF→(해상도 산출)→PNG/WEBP(Base64) 생성과 Base64 PNG의 폭·높이 빠른 추출</li>
</ul>
<hr />
<h3 id="--batch-요청-생성-유틸">- Batch 요청 생성 유틸</h3>
<h4 id="build_openai_batch_from_olmocrmixpy-">build_openai_batch_from_olmocrmix.py :</h4>
<ul>
<li>OLMoCR-mix 폴더 안의 단일 페이지 PDF들을 순회하면서,</li>
<li>각 단일 페이지 PDF를 PNG(Base64) 로 렌더링하고,</li>
<li>(이미지 가로×세로)로 프롬프트를 만들고,</li>
<li>OpenAI Batch API(대량 작업을 비동기적으로 처리하기 위한 API) 형식의 chat.completions 요청 JSON 한 줄씩을 JSONL 파일로 누적 저장함</li>
<li>JSONL 파일은 99MB(MAX_FILE_SIZE)를 넘지 않도록 자동으로 롤오버 진행 (파일명: batch_requests_0000.jsonl, ..._0001.jsonl …)</li>
</ul>
<h3 id="buildsilverpy-">buildsilver.py :</h3>
<ul>
<li>PDF에서 일부 페이지만 샘플해서 페이지 이미지를 Base64 PNG로 렌더링한 뒤, OpenAI Batch API에 넣을 JSONL 요청을 99MB 단위로 롤오버하며 저장하는 파일</li>
</ul>
<h3 id="runopenaibatchpy-">runopenaibatch.py :</h3>
<ul>
<li>대량 JSONL 배치 업로드·상태 추적·결과 수집·용량 관리를 한 번에 처리하는 Batch 운영 자동화 파일</li>
</ul>
<hr />
<h3 id="--원천-데이터-수집정리">- 원천 데이터 수집,정리</h3>
<h3 id="prepare_loc_transcriptspy-">prepare_loc_transcripts.py :</h3>
<ul>
<li>미국 의회 데이터 수집 → olmOCR 학습용 구조로 정리 <h3 id="prepare_national_archive_transcriptspy-">prepare_national_archive_transcripts.py :</h3>
</li>
<li>국립문서보관소 NARA 데이터 수집→ olmOCR 학습용 구조로 정리 <h3 id="prepare_olmocrmixpy-">prepare_olmocrmix.py :</h3>
</li>
<li>허깅페이스<code>allenai/olmOCR-mix</code> 데이터 수집→ olmOCR 학습용 구조로 정리 <h3 id="prepare_workspacepy-">prepare_workspace.py :</h3>
</li>
<li><code>workspace/results</code> 폴더 안의 <strong>파이프라인 결과(JSONL)</strong>를 페이지 단위의 (MD+단일 PDF) 학습 데이터로 뽑아 파인튜닝용 포맷으로 정리해 주는 변환기</li>
</ul>
<hr />
<h3 id="--결과-후처리-정제-포맷-변환">- 결과 후처리, 정제, 포맷 변환</h3>
<h3 id="process_openai_batch_resultspy-">process_openai_batch_results.py :</h3>
<ul>
<li><strong>OpenAI 배치 응답(JSONL)</strong>을 읽어 원본 PDF를 복사하고, 응답의 구조화 필드로 FrontMatter+본문이 있는 .md를 만들어, 원래 구조를 미러링한 학습·후처리용 산출물(MD+PDF) 폴더를 구성</li>
</ul>
<h3 id="clean_olmocrmixpy-">clean_olmocrmix.py :</h3>
<ul>
<li>OCR 결과(md 파일) 와 그에 대응하는 PDF 한 페이지 이미지를 함께 활용해서 ChatGPT 로 OCR 텍스트를 “정제(clean-up)”하는 파이프라인</li>
</ul>
<h3 id="repackage_olmocrmixpy-">repackage_olmocrmix.py :</h3>
<ul>
<li>로컬의 (MD+PDF) 학습 데이터셋을 업로드하기 좋은 형태로 변환</li>
</ul>
<hr />
<h2 id="5-출처">5. 출처</h2>
<ul>
<li><a href="https://github.com/allenai/olmocr">https://github.com/allenai/olmocr</a></li>
<li><a href="https://huggingface.co/datasets/allenai/olmOCR-mix-1025">https://huggingface.co/datasets/allenai/olmOCR-mix-1025</a></li>
</ul>