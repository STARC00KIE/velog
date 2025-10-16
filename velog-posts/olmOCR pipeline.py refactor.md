<table>
<thead>
<tr>
<th>단계</th>
<th>작업</th>
<th>비고</th>
</tr>
</thead>
<tbody><tr>
<td>①</td>
<td>목적 확정 (로컬, 단일 GPU)</td>
<td>서버/비동기 제거</td>
</tr>
<tr>
<td>②</td>
<td>파일 분리 (model, prompt, postprocess)</td>
<td>유지보수성↑</td>
</tr>
<tr>
<td>③</td>
<td>vLLM/Beaker/FastAPI 코드 제거</td>
<td>환경 단순화</td>
</tr>
<tr>
<td>④</td>
<td>모델/프로세서 로딩 함수 구현</td>
<td>torch + transformers</td>
</tr>
<tr>
<td>⑤</td>
<td>PDF → 이미지 변환 유지</td>
<td>render_pdf_to_base64png</td>
</tr>
<tr>
<td>⑥</td>
<td>get_anchor_text 유지</td>
<td>프롬프트 일관성</td>
</tr>
<tr>
<td>⑦</td>
<td>모델 추론 루프 동기화</td>
<td>generate()로 간결화</td>
</tr>
<tr>
<td>⑧</td>
<td>후처리(postprocess) 통합</td>
<td>품질 유지</td>
</tr>
<tr>
<td>⑨</td>
<td>main 함수 정리</td>
<td>단일 실행 포인트</td>
</tr>
<tr>
<td>⑩</td>
<td>CLI 인자/옵션 추가 (선택)</td>
<td>확장성 확보</td>
</tr>
</tbody></table>