<h1 id="axis">axis</h1>
<ul>
<li>데이터를 &quot;어느 방향으로 처리할지&quot; 지정하는 핵심 파라미터</li>
<li>데이터를 따라 연산이 적용되는 방향을 지정하는 것</li>
</ul>
<hr />
<h1 id="2차원행렬-기준-정리">2차원(행렬) 기준 정리</h1>
<table>
<thead>
<tr>
<th align="left"><code>axis</code> 값</th>
<th align="left">의미</th>
<th align="left">방향</th>
<th align="left">예시 연산</th>
</tr>
</thead>
<tbody><tr>
<td align="left"><code>axis=0</code></td>
<td align="left"><strong>열(column) 단위 연산</strong></td>
<td align="left"><strong>세로 방향</strong>으로 ↓</td>
<td align="left">각 열의 합계, 평균 등 (행을 따라 계산)</td>
</tr>
<tr>
<td align="left"><code>axis=1</code></td>
<td align="left"><strong>행(row) 단위 연산</strong></td>
<td align="left"><strong>가로 방향</strong>으로 →</td>
<td align="left">각 행의 합계, 평균 등 (열을 따라 계산)</td>
</tr>
</tbody></table>
<hr />
<h1 id="예시로-설명">예시로 설명</h1>
<ul>
<li>```lua
[[1, 2, 3],
[4, 5, 6]]</li>
<li><code>np.sum(arr, axis=0)</code> → 열 단위 연산 (세로 방향 합)<pre><code class="language-csharp">[1+4, 2+5, 3+6] = [5, 7, 9]</code></pre>
</li>
<li><code>np.sum(arr, axis=1)</code> → 행 단위 연산 (가로 방향 합)<pre><code class="language-csharp">[1+2+3, 4+5+6] = [6, 15]</code></pre>
</li>
</ul>
<hr />
<h1 id="1d-3d-이상에서의-axis">1D, 3D 이상에서의 axis</h1>
<table>
<thead>
<tr>
<th align="left">차원</th>
<th align="left">axis=0</th>
<th align="left">axis=1</th>
<th align="left">axis=2</th>
</tr>
</thead>
<tbody><tr>
<td align="left">1D</td>
<td align="left">전체 배열</td>
<td align="left">없음</td>
<td align="left">없음</td>
</tr>
<tr>
<td align="left">2D</td>
<td align="left">행 아래로(열 기준)</td>
<td align="left">열 옆으로(행 기준)</td>
<td align="left">없음</td>
</tr>
<tr>
<td align="left">3D</td>
<td align="left">&quot;층&quot; 단위</td>
<td align="left">행 단위</td>
<td align="left">열 단위</td>
</tr>
</tbody></table>
<hr />
<h1 id="numpy-pandas-둘다-axis-개념-같음">Numpy, pandas 둘다 axis 개념 같음</h1>
<ul>
<li>axis=0: &quot;행 방향으로 계산&quot; = 열 단위 연산</li>
<li>axis=1: &quot;열 방향으로 계산&quot; = 행 단위 연산</li>
</ul>