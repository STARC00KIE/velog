<h1 id="pre-trained-models-past-present-and-future-논문-요약"><strong>'Pre-trained Models: Past, Present and Future' 논문 요약</strong></h1>
<h2 id="1-introduction-소개"><strong>1. Introduction (소개)</strong></h2>
<p><strong>핵심 개념:</strong> </p>
<ul>
<li>대규모 사전학습 모델(Pre-Trained Models, PTMs)은 <strong>BERT</strong>, <strong>GPT</strong> 등으로 대표되며, 거대한 데이터로 미리 학습되어 다양한 작업에 지식을 제공하는 딥러닝 모델이다. </li>
<li>이들은 <strong>이전에는 어려웠던 NLP 과제들에서 혁신적인 성능 향상</strong>을 이뤄내어, 이제 <strong>AI 분야의 새로운 패러다임</strong>이 되었다.</li>
</ul>
<p><strong>주요 내용:</strong> </p>
<ul>
<li>딥러닝의 성공으로 <strong>CNN, RNN, GNN, 어텐션 네트워크</strong> 등이 다양한 AI 작업에 활용되었으나, <strong>“데이터 갈증”</strong> 문제가 있었다. </li>
<li>모델 파라미터 수가 많아 훈련 데이터가 충분치 않으면 <strong>과적합</strong>되고 일반화 성능이 낮아지는 한계가 있었다. </li>
<li>이를 극복하기 위해 연구자들은 대규모 <strong>데이터셋 구축</strong>(예: ImageNet, GLUE 등)을 시도했지만, 모든 문제에 대해 방대한 레이블 데이터를 수집하기는 <strong>비용 및 시간 면에서 불가능</strong>했다. </li>
<li>이에 따라 <strong>한정된 라벨 데이터로도 강력한 모델을 학습하는 방법</strong>이 주요 연구과제가 되었고, <strong>전이 학습(Transfer Learning)</strong>이 그 해결책의 하나로 떠올랐다.</li>
</ul>
<p><strong>등장한 기술:</strong> </p>
<ul>
<li>전이 학습은 <strong>“미리 학습(pre-training)과 미세조정(fine-tuning)”</strong>의 2단계 학습 틀을 공식화했다 </li>
<li>즉, <strong>소스 작업</strong>(여러 데이터가 풍부한 작업들)에서 <strong>사전학습</strong>하여 지식을 축적한 후, 그 <strong>지식을 대상 작업</strong>에 <strong>미세조정</strong>을 통해 전달함으로써, 적은 데이터로도 높은 성능을 얻는 방식을 제안했다. </li>
<li><strong>ImageNet</strong>에서 사전학습한 CNN들을 다양한 <strong>컴퓨터 비전(CV) 과제</strong>에 활용한 것이 대표적인 예로, 이를 통해 <strong>딥러닝 시대 1차 사전학습 열풍</strong>이 시작되었다.</li>
<li>자연어 처리(NLP) 분야 역시 이러한 가능성을 인지하였고, <strong>대규모 비라벨 텍스트</strong>로부터 지식을 얻기 위해 <strong>자기지도 학습(self-supervised learning)</strong>을 적극 도입했다. </li>
<li>자기지도 학습은 <strong>“문장에서 일부를 가리고 스스로 예측”</strong>하는 식으로, <strong>정답 라벨 없이도</strong> 텍스트 내재적 상관관계를 이용해 학습하는 방법이다. </li>
<li>이를 통해 <strong>거대 규모의 비라벨 말뭉치로부터 언어 지식</strong>을 학습할 수 있게 되었다 (예: 문장에서 단어를 가리고 맞추는 <strong>언어모델 목표</strong>).</li>
</ul>
<p><strong>중요한 전개:</strong> </p>
<ul>
<li>NLP 분야에서는 한때 <strong>Word2Vec, GloVe</strong> 같은 <strong>단어 임베딩</strong> 기법이 널리 쓰여 텍스트의 어휘 의미를 벡터로 표현했지만, <strong>다의어 문제</strong>(polysemy)로 <strong>문맥 반영 한계</strong>가 있었다. </li>
<li>이를 개선하기 위해 <strong>ELMo</strong> 등 RNN 기반 <strong>문맥화 임베딩</strong>이 등장했으나, RNN의 깊이 한계로 성능 향상은 제한적이었다. </li>
<li>2017년 <strong>Transformer</strong>의 도입 으로 딥러닝 모델을 훨씬 깊게 쌓아 학습하는 게 가능해졌고, 2018년에 <strong>GPT(Generative Pre-trained Transformer)</strong>와 <strong>BERT(Bidirectional Encoder Representations from Transformers)</strong>가 등장하면서 <strong>NLP 사전학습 모델의 새 시대</strong>가 열렸다. </li>
<li><strong>GPT</strong>는 <strong>자동회귀 언어모델</strong>(이전 단어들로 다음 단어 예측)로 <strong>텍스트 생성 능력</strong>을 중심으로, <strong>BERT</strong>는 <strong>마스크 언어모델</strong>(문장에서 일부 단어 가리고 예측)로 <strong>텍스트 이해 능력</strong>을 중심으로 설계되었다. </li>
<li>거대한 파라미터(수억~수십억 개)를 가진 이들 모델은 <strong>문맥에 따른 단어 의미 파악, 구문 구조, 사실 지식</strong> 등 <strong>풍부한 언어 지식</strong>을 학습할 수 있었고, 소량의 데이터로 미세조정해도 다양한 NLP 작업에서 사람 수준 또는 그 이상의 성능을 내는 것이 확인되었다. </li>
<li>예컨대 <strong>GLUE 벤치마크</strong> 성능이나 <strong>대화 생성 품질</strong> 등이 <strong>사전학습 사용 전후로 비약적으로 향상됨</strong>을 보여주는 도표들도 있다.</li>
</ul>
<p><strong>섹션 목적:</strong> </p>
<ul>
<li><strong>Introduction</strong>은 <strong>사전학습 모델의 등장 배경과 의의</strong>를 설명한다. </li>
<li><strong>딥러닝 모델의 데이터 의존 문제</strong>를 소개하고, 이를 해결하기 위한 <strong>전이학습의 개념과 역사</strong>를 간략히 짚은 뒤, <strong>NLP에서 자기지도 사전학습의 부상</strong>과 <strong>GPT/BERT의 혁신</strong>을 강조한다. </li>
<li>나아가, <strong>사전학습 모델이 AI 연구의 판도를 바꾸었으며 이제는 모든 AI 작업의 기본 백본(backbone)</strong>으로 자리잡았다는 점을 분명히 한다. </li>
<li>또한 이 논문에서 다룰 내용으로 <strong>사전학습의 역사적 발전</strong>, <strong>최신 연구 동향 네 가지 방향</strong> (아키텍처, 데이터/컨텍스트 활용, 효율성, 해석/이론), 그리고 <strong>열린 문제와 미래 방향</strong>을 미리 제시하여 이후 섹션들의 개요를 알려준다.</li>
</ul>
<hr />
<h2 id="2-background-배경"><strong>2. Background (배경)</strong></h2>
<p><strong>섹션 목적:</strong> </p>
<ul>
<li><strong>Background</strong> 섹션에서는 <strong>사전학습이라는 개념의 기원과 발전</strong>을 다룬다. </li>
<li>이는 <strong>초창기 전이학습과 지도학습 기반 사전학습</strong>부터 <strong>최근 자기지도 학습 기반 사전학습</strong>까지의 흐름을 살펴봄으로써, <strong>현재 PTM이 놓인 자리</strong>를 역사적인 맥락에서 이해하도록 돕는 것이 목표이다.</li>
</ul>
<h3 id="21-transfer-learning-and-supervised-pre-training-전이-학습과-지도-사전학습"><strong>2.1 Transfer Learning and Supervised Pre-Training (전이 학습과 지도 사전학습)</strong></h3>
<p><strong>핵심 개념:</strong> </p>
<ul>
<li><em>전이 학습(Transfer Learning)</em>은 <strong>기존에 배운 지식을 새로운 문제에 활용</strong>하는 학습 기법이다. </li>
<li>이는 <strong>사람이 이전에 배운 것으로 새로운 문제를 빠르게 익히는 능력</strong>에 착안한 것으로, <strong>하나 또는 여러 출발 작업(source tasks)</strong>에서 <strong>지식을 학습(사전학습)</strong>하고, 이를 <strong>목표 작업(target task)</strong>에 <strong>전이(미세조정)</strong>하여 사용한다. </li>
<li><em>지도 사전학습</em>은 전이학습의 초기 형태로, <strong>레이블이 있는 데이터</strong>로 모델을 사전훈련하는 것을 말한다.</li>
</ul>
<p><strong>주요 내용:</strong> </p>
<ul>
<li>전이학습에서는 <strong>출발 작업과 목표 작업의 도메인이나 목표가 달라도</strong> 근본적인 지식이 공유될 수 있다고 가정한다. </li>
<li>효과적인 전이를 위해 여러 <strong>사전학습 방법</strong>들이 고안되었는데, 크게 <strong>특징(feature) 전이</strong>와 <strong>파라미터 전이</strong>의 두 가지로 구분된다. </li>
<li><strong>특징 전이</strong>는 <strong>여러 도메인에서 쓸 수 있는 공통 표현</strong>을 미리 학습하는 것으로, 예를 들어 <strong>단어 임베딩</strong>은 방대한 텍스트에서 학습된 후 다양한 NLP 작업의 입력으로 쓰이며 큰 성능 향상을 주었다. </li>
<li><strong>파라미터 전이</strong>는 <strong>출발 작업과 목표 작업이 모델 파라미터를 공유</strong>할 수 있다는 가정에서 출발하며, 출발 작업들의 데이터를 이용해 <strong>모델 파라미터를 미리 학습</strong>한 뒤 이를 <strong>목표 작업에 미세조정</strong>하는 방식이다. </li>
<li><strong>사전학습된 CNN 모델을 가져와 새로운 비전 과제에 fine-tuning</strong>하는 것이 대표적인 예로, 이는 <strong>ImageNet 데이터셋</strong>으로 학습된 <strong>AlexNet/VGG/ResNet</strong> 등의 가중치를 활용하는 것이다. </li>
<li>실제로 <strong>ResNet-50</strong>같이 ImageNet으로 학습된 모델을 백본으로 사용하면, <strong>이미지 분류, 물체 검출, 분할, 이미지 캡셔닝, VQA</strong> 등 거의 모든 CV 과제에서 성능을 크게 향상시킬 수 있음을 당대 연구들이 입증했다. </li>
<li>이러한 <strong>지도 사전학습의 성공</strong>은 <strong>딥러닝 시대 1세대 사전학습 열풍</strong>으로 이어졌으며, <strong>CV 분야</strong>에서 표준처럼 활용되었다.</li>
</ul>
<p><strong>언급된 모델 및 기여:</strong>  </p>
<ul>
<li><strong>AlexNet (2012)</strong>, <strong>VGG (2015)</strong>, <strong>GoogLeNet (2015)</strong>: 딥러닝 초기부터 제안된 <strong>점점 더 깊어지는 CNN 구조</strong>들로, <strong>층을 깊게 쌓을수록 성능 개선</strong>이 가능함을 보였다. </li>
<li>하지만 너무 깊어지면 <strong>경사 소실/폭발 문제</strong>가 발생하고, 단순 깊이 증가로는 성능이 오히려 하락하는 <strong>포화 현상</strong>도 나타났다.  </li>
<li><strong>ResNet (2016)</strong>: <strong>잔차 연결(residual connection)</strong>과 <strong>배치 정규화</strong> 등을 도입하여 <strong>초딥 신경망 학습의 난제</strong>를 해결한 혁신적 CNN이다. </li>
<li>ResNet 덕분에 수백 층짜리 네트워크도 안정적으로 학습 가능해졌고, 이는 <strong>더 깊은 모델+대규모 데이터</strong>라는 조합을 현실화시켰다. </li>
<li><strong>ImageNet</strong> 같은 대규모 <strong>지도 학습 데이터셋</strong>(수백만 장 이미지, 수천 개 클래스)과 ResNet처럼 <strong>강력한 모델</strong>, 그리고 전이학습 아이디어가 결합하면서, <strong>지도 사전학습 모델의 물결</strong>이 일었다.  </li>
<li><strong>CoVE (2017)</strong>: NLP 분야의 <strong>지도 사전학습</strong> 사례로 언급된다. </li>
<li>이는 <strong>영→한 기계번역</strong>으로 시퀀스 투 시퀀스(seq2seq) 모델을 학습시킨 후, 그 <strong>인코더를 가져와 다양한 NLP 작업에 사용</strong>한 것이다. </li>
<li>비전의 ImageNet처럼 <strong>병렬 코퍼스(기계번역 데이터)</strong>를 이용해 언어 표현을 학습하고, 이를 문장 분류 등 다른 작업에 전이하여 <strong>성능 향상</strong>을 보인 연구로 알려져 있다.</li>
</ul>
<p><strong>섹션 요약:</strong> </p>
<ul>
<li>2.1은 <strong>전이학습의 개념과 초기 실현</strong>을 다루며, <strong>지도 데이터로 사전학습하는 접근</strong>이 어떻게 <strong>CV/NLP에서 성과</strong>를 냈는지 설명한다. </li>
<li>특히 <strong>특징 임베딩 공유(word embedding)</strong>와 <strong>파라미터 공유(CNN 파라미터 전이)</strong>라는 아이디어가 <strong>현재 PTM의 기반</strong>이 되었음을 강조한다. </li>
<li><strong>ELMo</strong>는 <strong>표현(feature) 전이</strong>의 예로, <strong>BERT</strong>는 <strong>파라미터 전이</strong>의 예로 언급되어, 현존 PTM들도 사실 이런 전통 위에서 발전한 것임을 짚었다.</li>
</ul>
<h3 id="22-self-supervised-learning-and-self-supervised-pre-training-자기지도-학습과-자기지도-사전학습"><strong>2.2 Self-Supervised Learning and Self-Supervised Pre-Training (자기지도 학습과 자기지도 사전학습)</strong></h3>
<p><strong>핵심 개념:</strong> </p>
<ul>
<li><em>자기지도 학습(self-supervised learning)</em>은 <strong>레이블 없이 데이터 자체로부터 감독신호를 생성</strong>하여 학습하는 방법이다. </li>
<li>이는 넓게 보면 <em>비지도 학습</em>의 일종이나, <strong>클러스터링/밀도추정 등 기존 비지도학습</strong>과는 달리 <strong>여전히 예측 문제(감독학습 형태)</strong>를 푼다는 차이가 있다. </li>
<li>예를 들어 <strong>언어모델</strong>은 텍스트에서 앞/뒤 문맥으로 단어를 예측하는 <strong>자기지도 목표</strong>로 볼 수 있다. </li>
<li><em>자기지도 사전학습</em>은 이러한 자기지도 방식으로 <strong>대규모 비라벨 데이터를 활용해 모델을 사전학습</strong>하는 것을 뜻한다.</li>
</ul>
<p><strong>필요성:</strong> </p>
<ul>
<li><strong>비지도 데이터 활용</strong>은 NLP에서 특히 중요했다. </li>
<li><strong>이미지 분야</strong>는 ImageNet 등 레이블 데이터가 비교적 풍부했지만, 텍스트에서 <strong>ImageNet 규모의 레이블 말뭉치 구축은 현실적으로 어려웠다</strong>. </li>
<li>문장에 라벨을 달려면 더 복잡하고 주관적인 작업이 많기 때문이다. </li>
<li>따라서 <strong>대규모 **비라벨 말뭉치</strong>를 활용하는 자기지도 사전학습이 NLP 발전의 열쇠**가 되었다</li>
</ul>
<p><strong>주요 내용:</strong> </p>
<ul>
<li>자기지도 학습의 대표 격인 <strong>언어모델링</strong>은, NLP에서 오래전부터 쓰인 <strong>다음 단어 예측</strong> 과제였다. </li>
<li><strong>Word2Vec</strong> (2013)과 <strong>GloVe</strong>(2014)는 대규모 텍스트에서 <strong>단어 주변 단어들을 예측</strong>하거나 <strong>동시출현 통계</strong>를 학습함으로써 <strong>단어를 벡터로 표현</strong>했다. </li>
<li>이 <strong>단어 임베딩</strong>들은 이후 모델들의 <strong>입력으로 투입</strong>되어, 랜덤 초기화 대비 <strong>크게 성능을 끌어올리는 효과</strong>를 보였다. </li>
<li>다만 앞서 언급한 <strong>다의성 문제</strong>로 인해, 문맥에 따라 뜻이 달라지는 단어는 하나의 벡터로 표현하기 어려웠다. </li>
<li>이를 해결하고자 <strong>문맥을 고려한 임베딩</strong>이 등장했는데, <strong>ELMo</strong>(2018) 등이 <strong>문장 단위 RNN</strong>으로 <strong>각 단어의 문맥별 표현</strong>을 얻었다. </li>
<li>이런 모델들은 성능 개선을 보여주었지만, RNN으로는 여전히 <strong>모델 깊이와 파라미터 수에 한계</strong>가 있어서 <strong>충분히 복잡한 언어현상을 담기엔 역부족</strong>이었다.</li>
<li>그러나 <strong>Transformer</strong>(2017)의 출현으로 상황이 바뀌었다. </li>
<li>Transformer는 <strong>병렬화가 용이</strong>하고 <strong>길이가 긴 시퀀스도 깊은 네트워크로 처리</strong>할 수 있어, NLP에서 <strong>훨씬 큰 모델을 학습</strong>하는 길을 열었다. </li>
<li>이를 기반으로 2018년 등장한 <strong>GPT</strong>와 <strong>BERT</strong>는 자기지도 사전학습의 위력을 증명했다. </li>
<li><strong>GPT</strong>는 <strong>Transformer 디코더</strong> 구조를 사용하여 <strong>왼쪽→오른쪽 방향</strong>으로 다음 단어를 예측하도록 학습했고, <strong>BERT</strong>는 <strong>Transformer 인코더</strong> 구조를 사용하여 <strong>문장 내 마스크된 단어를 맞추는 양방향 학습</strong>을 했다. </li>
<li>두 접근 모두 <strong>거대 말뭉치</strong>에서 <strong>레이블 없이</strong> 학습되었지만, 다르게 설계되어 <strong>GPT는 생성 능력</strong>(텍스트 생성, 이야기쓰기 등)에서, <strong>BERT는 이해 능력</strong>(문장 분류, 질의응답 등)에서 강점을 보였다. </li>
<li>특히 <strong>BERT</strong>는 <em>양방향 문맥</em>을 활용하므로 <strong>강력한 언어 이해</strong>가 가능하고, <strong>GPT</strong>는 <em>한 방향 생성</em>이므로 <strong>자연스러운 언어 생성</strong>에 적합하다. </li>
</ul>
<p><strong>사전학습-미세조정 표준화:</strong> </p>
<ul>
<li>이들 Transformer 기반 <strong>PTM들은 수백만~수십억 단어의 코퍼스</strong>에서 학습되고, 이후 <strong>다운스트림 작업에 미세조정</strong>되었는데, <strong>거의 모든 NLP 작업에서 최신 성능</strong>을 갱신하며 곧 <strong>표준 절차</strong>가 되었다.</li>
<li>이후 <strong>XLNet</strong>(2019), <strong>RoBERTa</strong>(2019), <strong>ALBERT</strong>(2019), <strong>T5</strong>(2020), <strong>BART</strong>(2019) 등 수많은 변종과 신모델이 쏟아져 나와 PTM 분야를 풍성하게 만들었다. </li>
<li>한편, <strong>자기지도+Transformer 조합</strong>은 <strong>비전</strong> 쪽에도 아이디어를 주어, <strong>MoCo, SimCLR, ViT</strong> 등 <strong>자기지도 비전모델</strong>이나 <strong>비전-언어 멀티모달 모델</strong>이 나오기 시작했다. </li>
<li>이러한 <strong>최근의 “2차 사전학습 열풍”</strong>은 이전의 <strong>지도학습 기반 1차 열풍</strong>과 구분되며, <strong>사전학습의 중심이 NLP로 이동</strong>했음을 보여준다.</li>
</ul>
<p><strong>언급된 개념/모델:</strong>  </p>
<ul>
<li><strong>Inductive vs Transductive vs Unsupervised Transfer Learning:</strong> 전이학습의 여러 범주로서 소개되었다. 특히 <strong>자기지도 학습</strong>은 <strong>라벨 없는 데이터</strong>를 활용한다는 점에서 <em>self-taught learning</em>이나 <em>unsupervised transfer learning</em>과 관련되지만, <strong>여전히 예측 문제 형식</strong>이라는 점에서 기존 비지도와 다르다고 설명되었다.  </li>
<li><strong>Word2Vec (2013)</strong>, <strong>GloVe (2014)</strong>: 초기 자기지도 사전학습의 예로, <strong>말뭉치로부터 단어벡터를 학습</strong>하여 이후 모델 입력에 활용한 방법. <strong>어휘 수준 통계</strong>를 벡터에 함축하여, <strong>초기 가중치로 사용</strong>하면 모델 성능이 향상됨을 보여주었다.  </li>
<li><strong>ELMo (2018)</strong>: <strong>문맥적 단어 표현</strong>을 제공한 RNN 기반 모델. <em>Representation Transfer</em>의 예로 소개되며, <strong>시퀀스 수준의 PTM</strong>의 효시로 언급되었다.  </li>
<li><strong>Transformer (2017)</strong>: <em>배경 섹션에서 상세 설명은 아니지만</em>, 이후 섹션의 주제로 이어지며 <strong>딥 NLP 모델의 길을 연 아키텍처</strong>로 강조되었다. Transformer 덕분에 <strong>GPT, BERT</strong> 같은 <strong>딥한 자기지도 PTM</strong>이 가능해졌음을 언급했다.</li>
</ul>
<p><strong>요약:</strong> </p>
<ul>
<li>2.2는 <strong>“왜 자기지도 사전학습이 대두되었는가”</strong>를 보여준다. </li>
<li><strong>레이블 부족 문제</strong>를 근본적으로 해결하기 위해, <strong>방대한 비라벨 데이터의 활용이 불가피</strong>했고, 이에 적합한 접근으로 <strong>자기지도 학습</strong>이 채택되었다. </li>
<li>그리고 <strong>단어 임베딩 → 문맥 임베딩 → Transformer 기반 PTM</strong>으로 이어지는 발전을 통해, <strong>NLP의 사전학습 2세대</strong>가 도래했음을 정리한다. </li>
<li>마지막으로, 이후 논문의 초점이 <strong>“최신 PTM = Transformer 기반의 언어모델”</strong>에 맞춰질 것임을 밝힌다. (즉, 이후 ‘PTM’이라 하면 <strong>대부분 프리트레인 언어모델이나 멀티모달 모델</strong>을 가리키며, 전통적 의미의 지도 사전학습 모델은 범위 밖으로 한다는 언급).</li>
</ul>
<hr />
<h2 id="3-transformer-and-representative-ptms-트랜스포머와-대표적인-사전학습-모델"><strong>3. Transformer and Representative PTMs (트랜스포머와 대표적인 사전학습 모델)</strong></h2>
<p><strong>섹션 목적:</strong> </p>
<ul>
<li>이 섹션은 <strong>최근 PTM의 기반이 된 핵심 요소</strong>들을 다룬다. </li>
<li>우선 <strong>Transformer 아키텍처</strong> 자체를 소개하여 PTM의 <strong>기술적 토대</strong>를 설명하고, 이어서 <strong>PTM 시대를 연 두 개의 이정표 모델, GPT와 BERT</strong>를 살펴본다. </li>
<li>마지막으로 <strong>GPT/BERT 이후 등장한 여러 PTM들</strong>을 간략히 훑어 <strong>현황</strong>을 정리한다. </li>
<li>이를 통해 독자는 <strong>PTM들의 기술적 뿌리와 계보</strong>를 이해할 수 있다.</li>
</ul>
<h3 id="31-transformer-트랜스포머-구조"><strong>3.1 Transformer (트랜스포머 구조)</strong></h3>
<p><strong>핵심 개념:</strong> </p>
<ul>
<li><em>Transformer</em>는 <strong>RNN 없이 어텐션 메커니즘에 기반한 시퀀스 모델</strong>이다.</li>
<li><strong>인코더-디코더</strong> 구성으로 이루어지며, <strong>병렬 연산에 최적화</strong>되어 긴 입력도 효율적으로 처리한다. </li>
<li><strong>멀티-헤드 자기어텐션(multi-head self-attention)</strong>과 <strong>포지션별 피드포워드 층(position-wise FFN)</strong>으로 이루어진 <strong>반복 블록</strong>을 깊게 쌓아, <strong>멀리 떨어진 토큰 간의 의존성</strong>도 효과적으로 포착한다. </li>
<li>Residual 연결과 Layer Normalization 등을 통해 <strong>아주 깊은 층 수</strong>도 안정적으로 학습할 수 있다.</li>
</ul>
<p><strong>구조 및 특징:</strong>  </p>
<ul>
<li><strong>인코더 &amp; 디코더:</strong> Transformer는 <strong>인코더-디코더 구조</strong>로, 인코더는 입력 시퀀스를 받아 <strong>내재 표현</strong>으로 변환하고, 디코더는 이를 참조하여 <strong>출력 시퀀스</strong>를 생성한다. 각 인코더 블록은 <strong>자기어텐션 + FFN</strong>으로, 각 디코더 블록은 <strong>자기어텐션 + 인코더-디코더 어텐션(cross-attention) + FFN</strong>으로 구성된다.  </li>
<li><strong>자기어텐션(Self-Attention):</strong> 시퀀스 내 <strong>각 단어 간 관계를 가중합</strong>으로 표현한다. 입력을 Query, Key, Value 벡터들로 변환해 <strong>Query-Key 유사도</strong>를 구하고, 그 가중치로 Value들을 가중 합산하여 <strong>문맥이 반영된 표현</strong>을 산출한다. 자기어텐션을 통해 <strong>문장 내 전 단어 쌍의 상호작용</strong>을 한 층에서 고려할 수 있어, <strong>긴 거리 의존성</strong>도 효과적으로 처리한다.  </li>
<li><strong>멀티-헤드 어텐션:</strong> 단일 어텐션이 <strong>하나의 관계 패턴</strong>만 학습하는 데 반해, <em>멀티-헤드</em>는 여러 집합의 Query/Key/Value로 <strong>여러 독립적 어텐션</strong>을 수행한 뒤 그 결과를 결합한다. 이로써 <strong>다양한 하위공간에서의 관계</strong>를 병렬로 학습하여 모델의 <strong>표현력</strong>을 높인다.  </li>
<li><strong>포지션별 FFN:</strong> 어텐션 출력 각각에 <strong>개별적으로 2층의 피드포워드 신경망</strong>(일반적으로 ReLU 포함)을 적용하는 층이다. 이는 <strong>어텐션으로 섞인 정보</strong>에 <strong>비선형 변환</strong>을 주어, <strong>복잡한 특징 조합</strong>을 가능케 한다.  </li>
<li><strong>마스킹 및 변형:</strong> 디코더에서는 미래 단어를 보지 않도록 <strong>마스킹 된 자기어텐션</strong>을 사용한다 (즉, <em>masked self-attention</em>). 이는 <strong>오토레그레시브 생성</strong>에 필수적이다. 또한 디코더는 <strong>인코더 출력과의 크로스어텐션</strong>으로 <strong>입력 시퀀스 컨텍스트</strong>를 활용한다.  </li>
<li><strong>Residual &amp; Normalization:</strong> 각 층 출력에 입력을 더해주는 <strong>잔차 연결</strong>과 <strong>LayerNorm</strong>을 통해 <strong>그래디언트 소실 완화 및 안정적 학습</strong>이 가능해진다.</li>
</ul>
<p><strong>기술적 기여:</strong> </p>
<ul>
<li>Tansformer의 <strong>가장 큰 공헌</strong>은 <strong>RNN의 순차적 제약을 탈피</strong>하여, <strong>병렬화로 막대한 텍스트를 학습할 수 있게 한 점</strong>이다. </li>
<li>RNN은 시간단계별 처리로 <strong>병렬화가 어려웠던 반면</strong>, Transformer의 self-attention은 <strong>문장 내 모든 단어를 동시에 처리</strong>하므로 <strong>GPU/TPU의 성능을 최대한 활용</strong>할 수 있었다. </li>
<li>또한, <strong>긴 문맥</strong>을 처리하면서도 <strong>계층적(멀티헤드)</strong>으로 정보를 추출할 수 있어 <strong>언어의 복잡한 구조</strong>를 잘 포착한다. </li>
<li><em>이 섹션에서는 수식과 함께 어텐션이 작동하는 원리까지 상세히 설명하지만</em>, 요약하자면 <strong>Transformer는 PTM 혁명의 토대가 된 범용 시퀀스 모델 아키텍처</strong>라는 것이다. </li>
<li>결과적으로 <strong>이후 모든 PTM</strong> (GPT류, BERT류)이 <strong>Transformer 구조를 백본으로 채택</strong>하고 있다.</li>
</ul>
<p><strong>섹션 연결:</strong> </p>
<ul>
<li>Transformer 설명 후, 논문은 <strong>“Transformer와 자기지도 학습의 결합이 PTM 성공의 열쇠”</strong>였다고 강조하며, <strong>GPT와 BERT</strong>라는 두 램프마크 모델을 소개하겠다고 예고한다.</li>
</ul>
<h3 id="32-gpt"><strong>3.2 GPT</strong></h3>
<p><strong>모델 개요:</strong> </p>
<ul>
<li><strong>GPT (Generative Pre-Trained Transformer)</strong>는 <strong>Transformer 디코더</strong> 구조를 기반으로 한 최초의 대규모 NLP 사전학습 모델이다. </li>
<li>2018년 OpenAI에서 제안되었으며, <strong>사전학습 단계에서는 언어 생성(자동회귀 언어모델)</strong>을, <strong>미세조정 단계에서는 분류 등</strong>을 수행하는 <strong>이중 단계</strong>의 전이학습을 채택했다. </li>
<li><strong>GPT는 현대적 Transformer 구조와 자기지도 언어모델 목표를 최초로 결합</strong>한 모델로 평가된다.</li>
</ul>
<p><strong>사전학습 기법:</strong> </p>
<ul>
<li><strong>오토레그레시브(순차 생성) 언어 모델링</strong>을 사용한다. </li>
<li>즉, 대규모 텍스트 코퍼스에서 <strong>각 단어의 이전 단어들로 다음 단어를 예측</strong>하도록 학습한다 . </li>
<li>Transformer 디코더는 마스크된 self-attention을 통해 <strong>왼쪽 문맥만 참고</strong>하면서 다음 단어의 확률 분포를 출력한다. </li>
<li>이 작업을 <strong>전체 말뭉치에 걸쳐</strong> 수행하여, <strong>언어 생성에 최적화된 내재 표현</strong>을 얻게 된다. </li>
</ul>
<p><strong>미세조정:</strong> </p>
<ul>
<li>GPT 논문에서는 학습된 모델을 다양한 <strong>NLP 이해 태스크</strong>(텍스트 분류, NLI, QA 등)에 적용하기 위해 <strong>소량의 해당 태스크 데이터로 추가 학습</strong>시켰다. </li>
<li>이때 GPT의 <strong>출력층</strong>을 작업에 맞게 조정하여 <strong>지도 학습</strong>을 했다. </li>
<li>GPT의 특이한 점은, <strong>사전학습은 생성 목표지만 미세조정은 디스크리미네이티브(분류) 목표</strong>를 썼다는 것이다. </li>
<li>이러한 <strong>“생성적 사전학습 + 판별적 미세조정”</strong> 조합은 이후 전이학습의 표준 중 하나가 되었다.</li>
</ul>
<p><strong>성과:</strong> </p>
<ul>
<li>GPT는 발표 당시 <strong>광범위한 NLP 과제에서 높은 성능</strong>을 시현했다. </li>
<li>특히 놀라웠던 점은, <strong>태스크별 구조 수정 없이</strong> 같은 모델이 문서분류, 질의응답, 추론 등 여러 작업을 모두 잘 해냈다는 것이다. </li>
<li>이는 <strong>하나의 사전학습된 언어모델이 다방면의 언어 능력을 습득</strong>함을 보여주었다. </li>
<li>GPT의 성공으로 <strong>“언어모델로 사전학습 후 미세조정”</strong>이라는 <strong>NLP 전이 학습 패러다임</strong>이 널리 받아들여졌다.</li>
</ul>
<p><strong>제한 및 발전:</strong> </p>
<ul>
<li>GPT-1에 이어, 더 많은 데이터와 파라미터로 <strong>GPT-2 (2019)</strong>, <strong>GPT-3 (2020)</strong>가 연이어 등장하며 <strong>언어 생성 능력의 극한</strong>을 보여줬다. </li>
<li>특히 <strong>GPT-2</strong>는 <strong>인터넷 웹 텍스트 80GB</strong>로 학습되어 <strong>놀랍도록 그럴듯한 긴 텍스트 생성</strong> 능력을 보였고, <strong>GPT-3</strong>는 <strong>1750억 파라미터</strong>로 확장되어 <strong>일반 상식, 간단한 추론, few-shot 러닝</strong> 등 새로운 능력을 보여주었다. </li>
<li>GPT-3는 <strong>질문에 몇 개 예시(Q&amp;A 쌍)</strong>만 주면 <strong>추가 학습 없이</strong> 답할 수 있어 (<em>few-shot learning</em>), 모델의 <strong>잠재지식과 범용성</strong>을 극대화한 사례로 언급된다. </li>
<li>GPT 시리즈의 등장은 “<strong>모델이 거대해질수록 언어모델 하나만으로도 거의 모든 언어 작업에 대응 가능</strong>”한 가능성을 보여주었다.</li>
</ul>
<p><strong>요약:</strong> </p>
<ul>
<li>GPT는 <strong>Transformer 기반 사전학습 언어모델의 효용을 입증한 첫 사례</strong>로, <strong>텍스트 생성</strong>과 <strong>전이학습의 효과</strong>를 강조한다. </li>
<li>GPT의 성공은 이후 <strong>BERT (인코더형 모델)</strong>의 등장과 더불어, NLP에서 <strong>사전학습 사용이 표준</strong>이 되는 데 큰 기여를 했다.</li>
</ul>
<h3 id="33-bert"><strong>3.3 BERT</strong></h3>
<p><strong>모델 개요:</strong> </p>
<ul>
<li><strong>BERT (Bidirectional Encoder Representations from Transformers)</strong>는 2018년 말 Google에서 발표한 <strong>양방향 Transformer 인코더 기반의 사전학습 모델</strong>이다. </li>
<li>GPT와 쌍벽을 이루는 PTM의 대표주자로, <strong>“양방향 문맥”</strong>을 활용하는 새 목표를 도입하여 <strong>자연어 이해(NLU)</strong> 성능을 크게 끌어올렸다.</li>
</ul>
<p><strong>사전학습 기법:</strong> </p>
<ul>
<li>BERT는 두 가지 자기지도 목표를 사용했다. </li>
<li>첫째, <strong>마스크드 언어 모델(Masked Language Model, MLM)</strong>: 입력 문장에서 <strong>15% 단어를 [MASK] 토큰으로 가리고</strong>, 모델이 이 <strong>가려진 단어들을 맞추도록</strong> 학습한다. </li>
<li>이를 통해 <strong>양쪽 문맥</strong>(왼쪽+오른쪽)을 모두 참고하여 각 단어의 의미를 추론하게 된다. </li>
<li>둘째, <strong>Next Sentence Prediction (NSP)</strong>: 문장 A 다음에 문장 B가 이어지는지 여부를 맞추는 이진 분류 작업이다. </li>
<li>이는 <strong>문장 간 관계</strong>(문맥 연결성)를 학습시키기 위한 것으로, 학습 시 문장쌍의 50%는 실제 이어진 순서로, 50%는 무작위 짝으로 구성하여 모델이 구분하게 했다. (다만 NSP의 유용성은 이후 논문에서 의문이 제기되기도 했다.)</li>
</ul>
<p><strong>구조:</strong> </p>
<ul>
<li>BERT는 <strong>Transformer 인코더 12층(BERT-base) 혹은 24층(BERT-large)</strong>로 구성된다. </li>
<li>입력으로 <strong>WordPiece 토큰 시퀀스</strong>를 받으며, 문장 구분을 위해 <strong>[SEP] 토큰</strong>, 문장 시작에 <strong>[CLS] 토큰</strong>을 넣는다. </li>
<li>[CLS] 토큰의 최종 은닉표현은 <strong>NSP 분류에 사용</strong>되었고, 또한 <strong>다운스트림 작업에서 문장 표현</strong>으로 활용되었다. </li>
<li>각 가려진 [MASK] 위치의 출력은 해당 단어의 어휘분포로 소프트맥스 되어 <strong>MLM 손실</strong>을 계산한다.</li>
</ul>
<p><strong>성과:</strong> </p>
<ul>
<li>BERT는 발표 당시 <strong>GLUE 벤치마크, SQuAD 질의응답</strong> 등 다수의 언어이해 태스크에서 최고 성적을 기록하며 NLP 커뮤니티에 큰 충격을 주었다. </li>
<li><strong>양방향 문맥 학습의 위력</strong>을 처음으로 증명하여, 이전 단방향 모델들 (예: GPT)이 놓치던 <strong>어순에 상관없는 상호관계</strong>까지 포착할 수 있음을 보여주었다. </li>
<li><strong>폭넓은 언어 현상</strong> – 어휘 의미, 구문 구조, 어휘상식 – 을 BERT가 <strong>깊은 층에 내재화</strong>하고 있음이 후속 연구들에서 밝혀졌다. </li>
<li>또한 BERT의 등장은 <strong>사전학습-미세조정</strong> 방식이 <strong>산업계 표준</strong>으로 자리잡는 계기가 되었고, 이후 <strong>수많은 변형 모델들</strong>이 등장하는 촉매가 되었다.</li>
</ul>
<p><strong>기술 기여:</strong> </p>
<ul>
<li>BERT의 가장 큰 공헌은 <strong>“양방향 사전학습”</strong>이라는 새 패러다임을 연 것이다. </li>
<li>GPT류의 단방향 모델과 달리, BERT는 <strong>문맥 양쪽을 동시에 고려</strong>함으로써 <strong>정밀한 언어 이해</strong>를 가능케 했다. </li>
<li>이는 번역, 추론 등 <strong>입력 전체를 봐야 하는 작업에 특히 효과적</strong>이었다. </li>
<li>또한 <strong>사전학습 태스크 설계의 중요성</strong>을 부각시켰다. (나중에 NSP의 효과 논란이 있었지만, MLM+NSP 조합이 초기 BERT 성공에 사용된 것은 사실이다.) </li>
<li>BERT는 <strong>파인튜닝의 용이성</strong>도 장점인데, 하나의 사전학습된 인코더를 가져와 출력만 바꾸어 <strong>다양한 태스크</strong>에 쉽게 적용할 수 있었다. </li>
<li>결국 BERT 이후, <strong>“PTM = BERT 기반”</strong>이라는 인식이 생길 정도로 많은 후속 연구들이 이 구조를 사용하거나 개선하였다.</li>
</ul>
<p><strong>후속 영향:</strong> </p>
<ul>
<li>BERT 이후 <strong>RoBERTa</strong>는 <strong>NSP를 제거</strong>하고 <strong>더 긴 학습과 더 많은 데이터</strong>로 성능을 높였고, <strong>ALBERT</strong>는 <strong>매개변수 공유와 임베딩 분해</strong>로 모델 크기를 줄이며 <strong>SOP</strong>라는 변형된 문장순서 예측을 도입했다. </li>
<li>이들은 <strong>BERT의 약점 보완</strong>이나 <strong>효율 개선</strong>을 통해 더욱 효과적인 PTM을 탐색한 예들이다.(예: RoBERTa는 <strong>NSP 무용론</strong>을 제기했고, ALBERT는 <strong>파라미터 감소</strong>로 <strong>경량 PTM</strong>의 가능성을 보여줌). </li>
<li>이러한 <strong>BERT 파생 연구들</strong>은 Section 4에서 더 다루어진다.</li>
</ul>
<h3 id="34-after-gpt-and-bert-gpt와-bert-이후"><strong>3.4 After GPT and BERT (GPT와 BERT 이후)</strong></h3>
<p><strong>개요:</strong> 이 부분에서는 <strong>GPT와 BERT 이후 최근 몇 년간 등장한 대표적 PTM들</strong>과 <strong>연구 방향</strong>을 간략히 정리한다. <strong>그림 9</strong>를 통해 <strong>최근 PTM 계보와 범주</strong>를 보여주고 있는데, 주요 내용은 다음과 같다.</p>
<ul>
<li><p><strong>BERT 개선 모델들:</strong> 앞서 언급한 <strong>RoBERTa</strong>(2019) – <em>더 많은 데이터와 튜닝으로 BERT 성능 향상, NSP 제거</em> –  와 <strong>ALBERT</strong>(2019) – <em>파라미터 절감 (임베딩 행렬 분해, 모든 층 가중치 공유), 새로운 SOP 태스크 도입</em> – 가 대표적이다. </p>
</li>
<li><p>이들은 <strong>BERT 구조는 유지하면서 학습방법이나 매개변수를 변경</strong>하여 효율/성능을 높인 사례다. </p>
</li>
<li><p>RoBERTa는 <strong>더 큰 배치와 동적 마스킹</strong> 등 <em>학습 세부 설정의 중요성</em>을 부각했고, ALBERT는 <strong>모델 경량화</strong>에 대한 통찰을 주었다 (매개변수 공유에도 성능이 유지되는 것은 <strong>PTM이 상당히 과다매개변수화</strong>되어 있음을 시사).</p>
</li>
<li><p><strong>기타 아키텍처/목표의 PTM들:</strong> -<strong>XLNet</strong>(2019)은 <em>GPT(자동회귀)와 BERT(양방향)의 장점을 결합</em>하려는 시도로, <strong>Permutation Language Model</strong>이라는 새 목표를 도입했다. </p>
</li>
<li><p><strong>UniLM</strong>(2019)은 <em>하나의 Transformer 안에서 단방향, 양방향, seq2seq 어텐션 마스크를 바꿔가며</em> <strong>여러 LM 목적을 함께 학습</strong>시켰다. </p>
</li>
<li><p><strong>MASS</strong>(2019)와 <strong>BART</strong>(2019)는 <em>Seq2Seq (인코더-디코더) 구조</em>로 <strong>텍스트 생성 작업들</strong>(요약, 번역 등)에 특화되게 사전학습했다 (MASS: 문장 일부를 마스크하고 나머지로 복원; BART: 노이즈 추가-&gt;원문 복원).</p>
</li>
<li><p><strong>SpanBERT</strong>(2020)는 <em>연속된 단어 구간을 마스킹</em>하는 MLM 변형으로 <strong>스팬 단위 예측</strong>을 도입했다. </p>
</li>
<li><p><strong>ELECTRA</strong>(2020)는 <em>생성기-판별기 방식</em>으로 <strong>MLM 대신 “가짜 단어 판별”</strong>(RTD: Replaced Token Detection) 태스크를 사용하여 <strong>학습 효율을 크게 높였다</strong>. </p>
</li>
<li><p>이처럼 <strong>새로운 사전학습 목표나 아키텍처 변화</strong>를 탐구한 연구들이 속속 등장했다.</p>
</li>
<li><p><strong>멀티소스 데이터 활용 PTM들:</strong> </p>
</li>
<li><p>한편, <strong>다국어(multilingual) PTM</strong>이나 <strong>멀티모달 PTM</strong>도 이 시기 많이 연구되었다. </p>
</li>
<li><p>이는 이후 Section 5에서 자세히 다루며, 여러 언어를 한 모델에 담거나, <strong>이미지+텍스트</strong> 등 <strong>다중 모달 입력을 함께 이해</strong>하는 모델 (예: ViLBERT, LXMERT 등)들이 소개된다.</p>
</li>
<li><p><strong>모델 규모 확장:</strong> </p>
</li>
<li><p>TM 성능의 한 축은 <strong>모델/데이터 규모</strong>인데, 연구자들은 <strong>수십억~조 단위 파라미터 모델</strong>에 도전하고 있다. </p>
</li>
<li><p><strong>GPT-3</strong>(2020)은 175B 파라미터로 유명하고, <strong>Switch Transformer</strong>(2021)는 <strong>Mixture-of-Experts</strong>로 <strong>경우에 따라 다른 부분만 활성화하여 효율적으로 1조+ 매개변수</strong>를 운용했다. </p>
</li>
<li><p><strong>거대 모델 학습을 위한 분산 학습 기법</strong>들도 함께 발전했다 (예: <strong>Megatron-LM</strong>, <strong>Deepspeed</strong> 등). </p>
</li>
<li><p>이러한 내용은 Section 6에서 <strong>효율성</strong> 맥락에서 다뤄진다.</p>
</li>
</ul>
<p><strong>정리:</strong> </p>
<ul>
<li>GPT/BERT 이후 PTM 분야는 <strong>다양한 방향의 발전</strong>이 이루어졌다. </li>
<li><strong>모델 구조 연구(통합 모델, 인지 영감 모델)</strong>는 Section 4에서, <strong>풍부한 데이터 활용(멀티링구얼, 멀티모달, 지식통합)</strong>은 Section 5에서, <strong>학습 효율화(시스템 최적화, 경량화)</strong>는 Section 6에서, <strong>모델 해석과 이론</strong>은 Section 7에서 각각 심도 있게 다루어질 것이다. </li>
<li>이 부분은 그 <strong>전반적인 로드맵</strong>을 제시하며, 독자가 <strong>PTM 분야의 지형과 흐름</strong>을 개략적으로 알 수 있게 한다.</li>
</ul>
<hr />
<h2 id="4-designing-effective-architectures-효과적인-아키텍처-설계"><strong>4. Designing Effective Architectures (효과적인 아키텍처 설계)</strong></h2>
<p><strong>섹션 목적:</strong> </p>
<ul>
<li>이 섹션은 <strong>BERT 이후 제안된 새로운 모델 아키텍처들</strong>을 살펴본다. </li>
<li><strong>Transformer 기반 PTM의 성공</strong>이 다양한 <strong>건축적 개선 시도</strong>를 촉발했는데, 저자들은 이를 <strong>두 가지 큰 동기</strong>로 분류한다: 
① <strong>다양한 언어 과제를 하나의 통합 모델로 아우르려는 시도</strong>와 
② <strong>인간 인지과학에 영감을 받은 아키텍처 개선 시도</strong>. 그리고 
③ 기존 BERT를 <strong>세부적으로 변형/최적화한 기타 연구들</strong>도 간략히 소개한다. 이 섹션을 통해 <strong>“더 나은 PTM 구조란 무엇인가”</strong>에 대한 최신 아이디어들을 정리한다.</li>
</ul>
<h3 id="41-unified-sequence-modeling-통합-시퀀스-모델링"><strong>4.1 Unified Sequence Modeling (통합 시퀀스 모델링)</strong></h3>
<p><strong>문제 제기:</strong> </p>
<ul>
<li>NLP에는 <strong>언어 이해(NLU)</strong>와 <strong>언어 생성(NLG)</strong>, 그리고 <strong>기계번역처럼 입력-&gt;출력으로 생성하는 과제</strong> 등이 있다. </li>
<li>전통적으로 <strong>GPT 계열(디코더)</strong>은 생성에, <strong>BERT 계열(인코더)</strong>은 이해에 강점이 있어서 용도가 구분되었다. </li>
<li>그러나 <strong>실제로 이해와 생성은 밀접히 연관</strong>되어 있고, <strong>이해 없는 생성, 생성 없는 이해는 불완전</strong>하다. </li>
<li>또한 많은 작업은 <strong>입력-&gt;출력 형태</strong>로 볼 수도 있고 <strong>판단 문제</strong>로 볼 수도 있어 경계가 모호하다. </li>
<li>연구 결과 <strong>GPT 같은 생성 모델도 충분한 미세조정으로 이해 작업에서 BERT에 필적하거나 더 나은 성능을 낼 수 있음</strong>이 보이며, <strong>이해와 생성의 구분이 인위적</strong>이라는 인식이 퍼졌다.</li>
</ul>
<p><strong>주요 아이디어:</strong> </p>
<ul>
<li><p>이러한 관찰에서 출발한 연구들은 <strong>“하나의 사전학습 모델로 이해와 생성 작업을 모두 잘 해내자”</strong>는 목표를 갖는다. </p>
</li>
<li><p><strong>통합 언어 모델링</strong> 방향의 대표적인 접근들은 다음과 같다:</p>
</li>
<li><p><strong>XLNet (2019):</strong> <em>Permuted Language Model</em>을 제안하여 <strong>BERT의 양방향성 + GPT의 autoregressive 예측</strong>을 결합했다.</p>
</li>
<li><p>BERT의 [MASK]는 사전학습 시 쓰이지만 실제 fine-tuning 입력엔 없다는 <em>미스매치</em> 문제가 있는데, XLNet은 <strong>입력 순서를 무작위 순열로 뒤섞고 autoregressive LM</strong>을 적용함으로써 <strong>[MASK] 토큰 없이도 양방향 문맥 학습</strong>을 구현했다. </p>
</li>
<li><p>이를 통해 <strong>이해와 생성 모두에 강한 언어모델</strong>을 지향했다. </p>
</li>
<li><p>후속으로 <strong>MPNet (2020)</strong>은 XLNet의 단점을 보완하여, 사전학습 시 모델이 <strong>문장 길이를 모르는 문제</strong>를 해결하는 등의 개선을 했다.</p>
</li>
<li><p><strong>UniLM (2019):</strong> <em>Unified Language Model</em>. <strong>한 Transformer 안에서 마스크 패턴만 바꿔가며</strong>, <strong>왼쪽→오른쪽 LM, 양방향 LM, 시퀀스-투-시퀀스 LM</strong>을 모두 학습시켰다. 예컨대 <strong>어텐션 마스크</strong>를 조정하여 <strong>때로는 GPT처럼, 때로는 BERT처럼, 때로는 번역기처럼</strong> 작동하도록 훈련한 것이다. </p>
</li>
<li><p>이렇게 멀티태스크 학습된 <strong>UniLM</strong>은 특히 <strong>질의응답 생성, 요약</strong> 등 생성 문제에서 좋은 성능을 보였다.</p>
</li>
<li><p><strong>GLM (2021):</strong> <em>General Language Model</em>. <strong>BERT의 [MASK] 개수를 미리 알려줘야 하는 문제</strong>를 해결하고 보다 <strong>우아하게 양방향+자동회귀 통합</strong>을 달성했다. </p>
</li>
<li><p>GLM은 <strong>임의 길이 스팬 마스크</strong>를 하고, 마스크 위치를 <strong>오토레그레시브하게 채워넣도록</strong> 훈련한다. </p>
</li>
<li><p>대신 마스크된 스팬 길이 정보를 잃지 않기 위해 <strong>2D 위치 인코딩</strong>을 도입했다. </p>
</li>
<li><p>그 결과 GLM은 <strong>NLU, 조건부 생성, 비조건부 생성</strong> 모든 영역에서 <strong>동시 SOTA</strong>를 최초로 달성하여, <em>“단일 모델 만으로 전 분야 최고 성능”</em>의 가능성을 보여주었다.</p>
</li>
</ul>
<p><strong>기술적 의의:</strong> </p>
<ul>
<li>통합 모델링 연구들은 <strong>“한 가지 프레임워크로 언어이해+생성 통합”</strong>을 시도함으로써, <strong>미래의 범용 언어 모델</strong>에 한 걸음 다가갔다. </li>
<li>이러한 모델들은 <strong>BERT류와 GPT류의 장점을 모두 취하려는 노력</strong>으로 볼 수 있다. </li>
<li>다만 실제 응용에서 <strong>단일 모델을 훈련하는 비용</strong>이 커지므로, 완전한 통합이 현실적으로 항상 최선은 아닐 수 있다. </li>
<li>그럼에도 불구하고 GLM같은 성과는 <strong>PTM의 만능화</strong>에 대한 희망을 주며, 이후 <strong>Prompt 튜닝</strong> 등 <strong>하나의 거대 LM으로 모든 작업 다루기</strong> 방향과 맥을 같이 한다. (Prompt 튜닝은 Section 8.1에서 다룸.)</li>
</ul>
<h3 id="42-cognitive-inspired-architectures-인지과학-영감을-받은-아키텍처"><strong>4.2 Cognitive-Inspired Architectures (인지과학 영감을 받은 아키텍처)</strong></h3>
<p><strong>배경:</strong> </p>
<ul>
<li>현재의 Transformer 기반 PTM들은 대체로 <strong>인간 인지 체계와는 거리가 있는 구조</strong>이다. </li>
<li><strong>어텐션 메커니즘</strong>은 <strong>사람의 주의(attention)</strong>에서 아이디어를 얻었다고 하나, 이는 인간 인지의 <em>일부분</em>일 뿐이다. </li>
<li>인간처럼 <strong>논리적 추론, 장기 기억, 작업기억</strong> 등을 수행하는 능력은 현 PTM에 부족하다. </li>
<li>이 부분에서는 <strong>인지과학의 고차원 개념들을 모델에 반영하려는 시도들</strong>을 소개한다.</li>
</ul>
<p><strong>핵심 방향:</strong> </p>
<ul>
<li><p>인간 인지 체계의 중요한 요소로 <strong>작업기억(working memory)</strong>과 <strong>장기기억(long-term memory)</strong>, <strong>논리/계획적 추론</strong> 등이 거론된다. </p>
</li>
<li><p>Transformer에는 <strong>입력 길이 제한(일반적으로 512 토큰)</strong>이 있어 <strong>긴 문서나 다단계 추론</strong>에 한계가 있으며, <strong>어텐션의 계산량이 쿼드릭(O(n^2))</strong>이라 효율도 떨어진다. </p>
</li>
<li><p>또한 Transformer는 <strong>모든 단어간 상호작용을 한 단계에서 계산</strong>하므로, 인간처럼 <strong>단계적으로 사고를 전개</strong>하지는 않는다. </p>
</li>
<li><p>이를 개선하기 위한 연구들이 진행 중이다:</p>
</li>
<li><p><strong>Maintainable Working Memory:</strong> </p>
</li>
<li><p><em>작동 기억 장치</em>. 인간은 <strong>한 번에 모든 정보를 처리하지 않고</strong>, <strong>작업기억</strong>에 중요 정보를 저장해 가며 사고한다. </p>
</li>
<li><p>Transformer에도 <strong>긴 입력 처리를 위한 “메모리”</strong> 개념을 넣으려는 시도가 있었다. </p>
</li>
<li><p><strong>Transformer-XL (2019)</strong>은 <strong>Segment-level Recurrence</strong>와 <strong>상대적 위치 인코딩</strong>을 도입하여, <strong>이전 시퀀스의 숨은 상태를 메모리로 활용</strong>함으로써 긴 문맥을 이어서 처리했다. </p>
</li>
<li><p>이는 RNN식으로 <strong>순환적 컨텍스트</strong>를 추가한 방식이지만, <strong>암묵적</strong>으로만 working memory를 구현했다. </p>
</li>
<li><p>더 나아가 <strong>CogQA (2019)</strong>는 <strong>multi-hop 질의응답</strong>에서 <strong>명시적 인지 그래프(cognitive graph)</strong>를 유지하는 방식을 제안했다.</p>
</li>
<li><p>여기서는 <strong>시스템1</strong>으로 PTM을, <strong>시스템2</strong>로 GNN을 사용하여, 문서 간 연결 관계를 그래프로 쌓아가며 추론했다. </p>
</li>
<li><p><strong>CogLTX (2020)</strong>는 CogQA를 확장하여, <strong>긴 문서 이해를 위해</strong> <em>MemRecall</em>이라는 모듈로 <strong>유지할 문장</strong>을 선택해 working memory에 넣고, 그 외부 메모리를 활용하여 답을 구했다. </p>
</li>
<li><p>요컨대, 이러한 연구들은 <strong>Transformer에 “잊지 않고 기억하며 읽기” 기능</strong>을 부여하려고 한 것이다.</p>
</li>
<li><p><strong>Sustainable Long-Term Memory:</strong> <em>지속적 장기기억</em>. <strong>GPT-3의 사례</strong>에서 보듯, 대규모 PTM은 <strong>사실 지식(factual knowledge)을 어느 정도 암기</strong>하고 있다. </p>
</li>
<li><p>하지만 그 <strong>기억 용량</strong>은 제한적이며, <strong>명시적이지 않아</strong> 필요한 지식을 바로 참조하기 어렵다. </p>
</li>
<li><p>이를 보완하기 위해 <strong>외부 지식베이스나 메모리</strong>를 접목하는 연구가 이루어졌다. </p>
</li>
<li><p><strong>REALM (2020)</strong>은 <strong>위키피디아 전 문장을 임베딩</strong>해 저장해두고, <strong>사전학습 중에 관련 문장을 검색하여 컨텍스트로 제공</strong>하는 방식을 썼다. </p>
</li>
<li><p>이는 일종의 <strong>“retriever + BERT”</strong> 구조로, PTM이 <strong>외부 텍스트 메모리</strong>를 참고하도록 했다. </p>
</li>
<li><p><strong>RAG (2020)</strong>는 이 아이디어를 생성 모델(GPT류)에 적용하여, <strong>추출형 QA보다 나은 생성형 QA</strong>를 구현했다. </p>
</li>
<li><p>다른 접근으로, <strong>K-BERT, ERNIE</strong> 등은 <strong>지식 그래프의 개체 및 관계 임베딩</strong>을 모델에 통합하여, <strong>내부에 지식을 주입</strong>하기도 했다. 또한 <strong>Lample(2019)</strong>의 연구에서는 <strong>Transformer의 FFN 층을 대형 Key-Value 메모리로 교체</strong>하여 <strong>FFN이 메모리 역할을 한다는 점</strong>을 시사했다. </p>
</li>
<li><p>이러한 결과는 <strong>“Transformer 내부 MLP도 일종의 지식 저장소”</strong>임을 암시한다. 그러나 간접적인 저장보다, <strong>명시적 메모리</strong>가 더 확장성 있다고 보고, <strong>외부 장기기억을 모델에 결합</strong>하려는 시도가 지속되고 있다. </p>
</li>
<li><p>예를 들어 <strong>Verga(2020), Févry(2020)</strong> 등은 <strong>지식 그래프의 엔티티를 임베딩으로 미리 학습해</strong> 두고, <strong>모델 인코딩 중 해당 엔티티 토큰을 그 임베딩으로 대체</strong>하여 지식을 삽입했다. </p>
</li>
<li><p><strong>Dhingra(2020), Sun(2021)</strong> 등은 <strong>아예 모델 안에 “가상 지식 메모리”를 만들고 differentiable한 방식으로 추론</strong>하도록 훈련했다. </p>
</li>
<li><p>이처럼 <strong>PTM + 지식메모리</strong> 접근들은 <strong>오픈도메인 QA</strong> 등에서 좋은 성능을 내고 있으며, <strong>모델이 스스로 필요 지식을 찾아쓰는 방향</strong>으로 발전 중이다.</p>
</li>
</ul>
<p><strong>기타 인지적 측면:</strong> </p>
<ul>
<li>인간 인지는 <strong>논리적 추론, 의식적 계획</strong> 등의 측면도 있다. </li>
<li><strong>“신뢰할 수 있고 통제 가능한 추론”</strong>은 아직 PTM에 부족하며, 이를 위해 <strong>모델이 스스로 추론 단계를 그래프로 구성하고 진행</strong>하도록 하는 연구가 필요하다고 저자들은 말한다.</li>
<li><em>InversePrompting</em>(2021) 같은 방법은 <strong>생성 과정을 제어</strong>하는 기술로 소개되는데, 이는 특정 주제 유지 등 <strong>고수준 제어</strong>를 가능하게 하여 복잡한 생성 문제에 기여할 수 있다.</li>
</ul>
<p><strong>요약:</strong> </p>
<ul>
<li><p>인지 영감 아키텍처는 <strong>PTM를 보다 “생각하는 기계”답게 만들려는 노력</strong>이다. </p>
</li>
<li><p><strong>Working Memory 연구</strong>는 <strong>긴 문서/다단계 추론</strong>에서 성능 개선을, <strong>Long-term Memory 연구</strong>는 <strong>대량 지식 활용과 보강</strong>을 꾀한다. </p>
</li>
<li><p>아직 완전한 해법은 없지만, <strong>인지적 모듈 도입</strong>은 PTM의 <strong>이해도와 신뢰성 향상</strong>에 중요한 방향으로 간주된다.</p>
<h3 id="43-more-variants-of-existing-ptms-기존-ptm의-다양한-변형"><strong>4.3 More Variants of Existing PTMs (기존 PTM의 다양한 변형)</strong></h3>
</li>
<li><p><em>개요:*</em> </p>
</li>
<li><p>이 부분에서는 <strong>특정 PTM (주로 BERT)의 세부적인 변형 연구들</strong>을 다룬다. </p>
</li>
<li><p>완전히 새로운 아키텍처보다는, <strong>기존 모델의 일부 구성요소나 학습방법을 바꿔 성능을 향상</strong>시키는 접근들이다. </p>
</li>
<li><p><strong>대부분 자연어 이해 작업 성능을 높이는 목표</strong>를 갖고 있다.</p>
</li>
<li><p><strong>마스킹 전략 개선:</strong> </p>
</li>
<li><p>BERT의 MLM은 <strong>낱단어(mask 토큰 하나) 마스킹</strong>을 한다. </p>
</li>
<li><p>이를 확장하여 <strong>연속 단어 구간(span)을 한꺼번에 마스킹</strong>하면 더 어려운 예측이 되어 언어 이해가 좋아진다는 연구가 <strong>SpanBERT (2020)</strong>에서 나왔다. </p>
</li>
<li><p>SpanBERT는 마스크된 스팬의 양 끝 단어를 단서로 스팬 전체를 맞추는 <em>Span Boundary Objective</em>를 추가하여, <strong>구문구조와 어휘 연속성 이해</strong>를 향상시켰다. </p>
</li>
<li><p><strong>ERNIE (Baidu, 2019)</strong>는 여기에 <strong>“개체(entity) 단위 마스킹”</strong>을 도입하여, <strong>사전적/백과사전적 지식</strong> 학습 효과를 냈다. </p>
</li>
<li><p><strong>Whole Word Masking</strong> 기법도 제안되어, WordPiece 조각이 아니라 <strong>완전한 단어 단위로 마스킹</strong>함으로써 <strong>더 일관된 의미추론</strong>을 가능케 했다. </p>
</li>
<li><p>이처럼 <strong>마스킹을 통한 데이터 증강</strong> 아이디어들은 BERT 성능을 높이는 데 기여했다.</p>
</li>
<li><p><strong>학습 목표 변형:</strong> </p>
</li>
<li><p><strong>ELECTRA (2020)</strong>는 앞서 설명한 대로 <strong>토큰 생성 대신 판별</strong>하는 새로운 목표(RTD)를 도입했다. </p>
</li>
<li><p>작은 생성기가 일부 단어를 가짜로 바꾸고, 큰 모델이 <strong>각 단어가 원본인지 아닌지 판단</strong>하는 방식으로 학습한다. </p>
</li>
<li><p>이 방식은 <strong>모든 단어에서 학습신호</strong>를 얻기 때문에 매우 효율적이며, 같은 성능에 도달하기까지 필요한 <strong>사전학습 단계 수를 크게 단축</strong>시켰다. </p>
</li>
<li><p>실제로 ELECTRA는 <strong>GPU 비용을 줄이면서도 BERT에 근접한 성능</strong>을 내어 많은 응용에서 채택되었다.</p>
</li>
<li><p><strong>기타 변형:</strong> </p>
</li>
<li><p>BERT 구조에서 <strong>특정 모듈의 역할 분석</strong>과 <strong>경량화</strong>도 활발했다. </p>
</li>
<li><p>예를 들어, <strong>레이어 축소/확장 실험</strong>으로 <strong>과적합 완화</strong>나 <strong>성능 향상</strong>을 꾀하는 연구들이 있었다. </p>
</li>
<li><p>한 연구는 <strong>훈련 시 임의로 일부 Transformer 레이어를 드롭(drop) 시켜</strong> 얕은 모델을 만들고, 추론 시 일부만 사용하여 속도를 높이기도 했다. </p>
</li>
<li><p>또 <strong>어텐션 헤드 중요도 분석</strong>을 통해 <strong>많은 헤드를 제거해도 성능이 유지됨</strong>을 보인 연구들은 <strong>모델 경량화</strong>나 <strong>희소화</strong>에 영향을 주었다. </p>
</li>
<li><p><strong>ALBERT</strong>도 일종의 변형으로, <strong>매우 적은 파라미터로도 BERT와 동등 성능</strong>을 내며 <strong>과다매개변수 현상</strong>을 지적했다.</p>
</li>
</ul>
<p><strong>요약:</strong> </p>
<ul>
<li>4.3에서는 <strong>“BERT 더 잘 쓰기”</strong>에 해당하는 다수의 엔지니어링 아이디어들을 살펴봤다. </li>
<li><strong>데이터 증강 측면</strong>(마스킹 변형)과 <strong>목표함수 측면</strong>(RTD 등)이 주요한데, 이는 <strong>더 적은 데이터/자원으로 더 나은 언어표현 학습</strong>을 가능케 했다. </li>
<li>이러한 세부 개선 연구들은 합쳐져서 <strong>현시점 최고 성능 PTM의 구현</strong>에 활용되고 있으며, 예컨대 <strong>RoBERTa</strong>는 마스킹/학습세팅 개선, <strong>ELECTRA</strong>는 목표 개선, <strong>SpanBERT/ERNIE</strong>는 마스킹 개선 등 여러 아이디어를 통합해 사용한다. </li>
<li>결국 PTM 분야는 <strong>혁신적 새 구조 개발</strong>과 더불어 <strong>기존 기법의 미세조정과 최적화</strong>라는 두 축으로 발전하고 있음을 알 수 있다.</li>
</ul>
<hr />
<h2 id="5-utilizing-multi-source-data-다중-소스-데이터-활용"><strong>5. Utilizing Multi-Source Data (다중 소스 데이터 활용)</strong></h2>
<p><strong>섹션 목적:</strong> </p>
<ul>
<li>이 섹션에서는 <strong>“더 풍부한 데이터 자원 활용”</strong>을 통한 PTM 발전을 다룬다. </li>
<li>지금까지 PTM들은 주로 <strong>대규모 일반 도메인 텍스트</strong>(주로 영어)에 집중되었지만, 세상에는 <strong>다양한 언어</strong>와 <strong>텍스트 외 정보(이미지, 소리, 지식 그래프 등)</strong>가 존재한다. </li>
<li>이러한 <strong>이질적인 데이터 소스들을 PTM에 통합</strong>하려는 연구가 제5장의 주제이다. </li>
<li>이를 위해 <strong>다중언어 학습</strong>, <strong>멀티모달 학습</strong>, <strong>외부 지식 결합</strong> 세 가지 부문으로 나누어 소개한다.</li>
</ul>
<h3 id="51-multilingual-pre-training-다국어-사전학습"><strong>5.1 Multilingual Pre-Training (다국어 사전학습)</strong></h3>
<p><strong>필요성:</strong> </p>
<ul>
<li>현존 PTM 대다수는 <strong>영어 데이터</strong>로 학습되었다. </li>
<li>하지만 <strong>세계는 다국어 환경</strong>이며, <strong>언어별로 거대 모델을 따로 만드는 것은 비효율적</strong>이다. </li>
<li>다행히 서로 다른 언어라도 <strong>표현하는 의미는 공통적</strong>이므로 (즉, <strong>의미는 기호 체계와 독립적</strong>이라는 가정), <strong>하나의 모델이 여러 언어의 의미를 동시에 학습</strong>할 수 있으리라 기대된다. </li>
<li>실제로 연구를 해보면, <strong>여러 언어 데이터를 함께 학습한 단일 모델이 각 언어별 개별 모델보다 성능이 좋을 수 있음</strong>이 관찰되었다. </li>
<li>따라서 <strong>다국어 PTM</strong>은 <strong>비용 면에서도 성능 면에서도 매력적 대안</strong>이다.</li>
</ul>
<p><strong>초기 연구:</strong> </p>
<ul>
<li>BERT 등장 전에도 <strong>다국어 표현 학습</strong>이 시도되었다. </li>
<li>대표적으로 <strong>멀티링구얼 번역 모델</strong>을 들 수 있는데, 하나의 RNN seq2seq 모델을 <strong>여러 언어쌍 번역</strong>에 공동으로 훈련하여 <strong>다국어 잠재표현</strong>을 얻는 식이었다. </li>
<li>또 다른 접근은 <strong>언어 불변적 표현</strong>을 강제하는 것으로, 예를 들어 <strong>언어 고유 표현 vs 언어 공통 표현을 분리</strong>하거나, <strong>WGAN으로 언어간 분포 차이를 줄이는</strong> 등 방법이 제안됐다.</li>
<li>그러나 이들 모델은 <strong>특정 작업</strong>(번역 등)에 종속되어 있어, 배운 다국어 지식을 다른 과제에 일반화하진 못했다. </li>
<li>즉, <strong>작업 간 전이가 안 되어</strong> 언어마다 새로운 모델을 또 학습해야 했고, 이는 <strong>대량 라벨 필요</strong> 문제를 여전히 남겼다.</li>
</ul>
<p><strong>멀티링구얼 PTM의 등장:</strong> </p>
<ul>
<li><p><strong>BERT 멀티링구얼 모델</strong>이 등장하면서 <strong>“일반 목적 다국어 표현을 사전학습 후 활용”</strong>하는 방식이 현실화되었다. </p>
</li>
<li><p><strong>Multilingual BERT (mBERT)</strong>는 <strong>위키백과 104개 언어</strong>의 문서들을 합쳐 <strong>MLM(마스크 언어모델)으로 사전학습</strong>했다. </p>
</li>
<li><p>특별히 평행말뭉치(번역쌍) 없이, <strong>비병렬 코퍼스만으로</strong> 학습했음에도, <strong>mBERT는 zero-shot으로도 언어 간 지식을 공유</strong>함이 실험으로 확인되었다. </p>
</li>
<li><p>예컨대 영어로 훈련된 모델이 (같은 구조의) mBERT를 사용하면, <strong>라벨 없는 다른 언어 테스트에서도 상당히 성능이 나오는</strong> 식이다. </p>
</li>
<li><p>이는 <strong>동일 Transformer 안에 여러 언어의 표현이 함께 학습되면, 자연스럽게 언어간 보편적 표현공간이 형성</strong>된다는 것을 보여준다.</p>
</li>
<li><p>이후 <strong>XLM-R (XLM-RoBERTa, 2020)</strong>가 등장하여, <strong>더 큰 다국어 코퍼스(CC-100, 100개 언어)</strong>로 <strong>더 오래 MLM 사전학습</strong>함으로써 mBERT를 능가하는 성능을 보였다. </p>
</li>
<li><p>특히 <strong>저자원 언어</strong>의 경우, <strong>대량의 웹크롤 말뭉치 사용</strong>이 큰 향상을 가져와, <strong>데이터 규모가 중요</strong>함을 확인시켰다.</p>
</li>
</ul>
<p><strong>평행 데이터 활용:</strong> </p>
<ul>
<li><p>한계로 지적된 점은, <strong>mBERT나 XLM-R은 병렬 말뭉치를 직접 활용하지 못한다</strong>는 것이다. </p>
</li>
<li><p>그러나 번역 등 작업에서는 <strong>언어간 1대1 매핑 데이터(병렬코퍼스)</strong>가 매우 중요하며, 이를 통해 <strong>언어간 표현 정렬</strong>을 직접 학습시킬 수 있다. </p>
</li>
<li><p>이를 위해 <strong>XLM (2019)</strong>은 <strong>Translation Language Modeling (TLM)</strong>이라는 태스크를 도입했다. </p>
</li>
<li><p><strong>TLM</strong>은 <strong>의미상 대응되는 이중언어 문장 쌍을 붙여 하나의 입력으로 만들고, MLM 방식으로 단어를 가려 예측</strong>하게 한다. </p>
</li>
<li><p>모델은 <strong>한 언어에 가린 단어를 다른 언어 문맥까지 활용해 맞추어야 하므로</strong>, 자연스럽게 <strong>양언어 표현이 같은 공간으로 정렬</strong>된다. </p>
</li>
<li><p>TLM을 적용한 XLM 모델은 <strong>병렬 데이터의 힘</strong>을 보여주었고, 이후 다국어 PTM에 <strong>대부분 도입</strong>되었다.</p>
</li>
<li><p>이밖에 <strong>Unicoder (2019)</strong>는 <strong>병렬 코퍼스를 활용한 두 가지 추가 과제</strong>를 제안했다: </p>
</li>
</ul>
<ol>
<li><strong>교차 lingual 단어 복원 (CLWR)</strong> – 소스 문장 임베딩을 주면 타겟 문장 임베딩으로 복원하게 하여 <strong>단어 수준 정렬</strong>을 학습, </li>
<li><strong>교차 lingual 패러프레이즈 분류 (CLPC)</strong> – 번역 쌍이면 positive, 아니면 negative로 분류하여 <strong>문장 수준 정렬</strong>을 학습. </li>
</ol>
<ul>
<li>이로써 병렬 데이터에서 <strong>단어/문장 alignment</strong>를 효과적으로 익혔다. </li>
<li><strong>ALM (2020)</strong>은 <strong>병렬문장을 교차로 섞은 code-switch 문장</strong>을 자동 생성하여 MLM을 수행함으로써, <strong>문장 일부를 타언어로 바꿔가며도 문맥을 이해</strong>하도록 했다. </li>
<li><strong>InfoXLM (2020)</strong>은 <strong>정보 이론적 관점</strong>에서 MMLM과 TLM을 분석하고, <strong>대조학습(contrastive learning)</strong>을 도입해 <strong>맞는 번역쌍 vs 틀린 쌍</strong>을 구분하도록 학습했다. </li>
<li><strong>HICTL (2021)</strong>은 한 발 더 나아가 <strong>대조학습으로 문장+단어 수준 모두에서 다국어 정렬</strong>을 배우게 했다. </li>
<li><strong>ERNIE-M (2020)</strong>은 <strong>역번역(back-translation)</strong> 기법으로 병렬 데이터를 증폭시키고, <strong>생성된 문장 쌍으로 BTMLM (역번역 MLM)</strong>을 수행하여 성능을 높였다. </li>
<li>이처럼 다양한 시도들이 <strong>병렬 코퍼스의 적극적 활용</strong>으로 이어졌고, 결과적으로 <strong>언어 간 의미공간 통합</strong>을 크게 개선했다.</li>
</ul>
<p><strong>생성형 다국어 PTM:</strong> </p>
<ul>
<li><p>지금까지는 주로 <strong>문장 이해/분류용 인코더</strong> 모델을 다뤘다면, <strong>번역, 요약</strong> 등 <strong>생성 작업용 다국어 PTM</strong>도 개발되었다. </p>
</li>
<li><p>일반적으로 <strong>Transformer 인코더+디코더 구조</strong>를 쓰는데, <strong>MASS (2019)</strong>는 <em>마스크된 시퀀스 to 시퀀스</em> 사전학습을 제안했다. </p>
</li>
<li><p>한 문장에서 <strong>연속된 토큰 스팬을 마스킹하여 인코더 입력으로 주고</strong>, <strong>그 마스크된 부분을 디코더가 autoregressive 생성</strong>하도록 학습한다. </p>
</li>
<li><p>이는 <strong>비지도 번역</strong>과 유사한 설정이다. </p>
</li>
<li><p><strong>Denoising Auto-Encoder (DAE)</strong>는 BART에서 활용된 것으로, <strong>문장에 노이즈 (스팬 마스킹+순서 뒤섞기)를 주어 망가뜨리고 원문을 복원</strong>하도록 학습한다. </p>
</li>
<li><p><strong>mBART (2020)</strong>는 이 DAE를 <strong>다국어에 확장</strong>하여, 인코더 입력과 디코더 출력에 <strong>언어 아이디 토큰</strong>을 붙여 여러 언어를 한 모델로 학습했다. </p>
</li>
<li><p>이를 통해 <strong>다국어 인코딩/디코딩</strong>이 가능해져, 하나의 모델이 다중 언어로 요약 생성 등을 할 수 있게 되었다.</p>
</li>
<li><p>하지만 mBART에도 <strong>한계</strong>가 있었다: 학습 시 항상 <strong>인코더 언어 = 디코더 언어</strong>였기 때문에, 모델이 <strong>언어 아이디 토큰을 무시하고 입력 언어로 출력하는 경향</strong>이 남았다. </p>
</li>
<li><p>즉, 진정한 <strong>언어 변환</strong>(예: 영-&gt;불 번역)은 학습되지 않은 것. </p>
</li>
<li><p>이를 개선한 것이 <strong>XNLG (2020)</strong>로, <strong>Cross-lingual Auto-Encoding (XAE)</strong> 태스크를 도입했다. </p>
</li>
<li><p>XAE에서는 <strong>인코더 입력과 디코더 출력 언어가 다르게</strong> 주어져, <strong>사전학습부터 실제 번역과 유사한</strong> 설정으로 학습되었다. </p>
</li>
<li><p>또한 XNLG는 <strong>2단계 학습</strong>을 사용했는데, <strong>먼저 인코더는 MLM/TLM으로 학습</strong>하고, <strong>그 후 인코더 고정한 채 디코더를 DAE+XAE로 학습</strong>했다. </p>
</li>
<li><p>이렇게 하면 <strong>인코더/디코더 모두 잘 사전학습</strong>되고, <strong>MLM 사전학습과 autoregressive 미세조정 간 차이</strong>도 줄어든다. </p>
</li>
<li><p>XNLG는 결과적으로 <strong>다국어 입력-&gt;출력 생성</strong>에 강점을 보여, <strong>질의 생성, 요약</strong> 등의 과제에서 다국어 능력을 입증했다.</p>
</li>
</ul>
<p><strong>요약:</strong> </p>
<ul>
<li>다국어 사전학습은 <strong>“하나의 거대 모델로 다수 언어 처리”</strong>라는 비전을 향해 가고 있다. </li>
<li><strong>비병렬 코퍼스</strong>만으로도 어느 정도 가능함이 mBERT로 확인되었고, <strong>병렬 데이터와 새로운 태스크들</strong>(TLM 등) 도입으로 <strong>언어 간 지식 공유 효율이 극대화</strong>되었다. </li>
<li>아직도 <strong>저자원 언어</strong> 문제나 <strong>사전학습 언어에 없는 언어 추가의 어려움</strong> 등이 남아있지만 (Section 8.2에서 다룸), 멀티링구얼 PTM은 다언어 환경에서 <strong>라벨 부족 문제를 완화하고 언어 장벽을 낮추는 핵심 기술</strong>로 떠오르고 있다.</li>
</ul>
<h3 id="52-multimodal-pre-training-멀티모달-사전학습"><strong>5.2 Multimodal Pre-Training (멀티모달 사전학습)</strong></h3>
<p><strong>개요:</strong> </p>
<ul>
<li>인간은 <strong>시각, 청각, 언어</strong> 등 <strong>여러 감각모달리티</strong>를 통합하여 세상을 이해한다. </li>
<li>이에 따라, AI 모델도 <strong>텍스트+이미지, 텍스트+음성, 비디오+자막</strong> 등 <strong>다중 모달 입력</strong>을 동시에 다루는 능력이 요구된다. </li>
<li>최근 PTM의 발전은 <strong>멀티모달 AI 연구에도 큰 자극</strong>을 주어, <strong>비전-언어 결합 PTM</strong> 등이 다수 등장했다. </li>
<li>이 절에서는 <strong>Vision &amp; Language (V&amp;L)</strong> 분야를 중심으로, <strong>이미지-텍스트</strong>, <strong>비디오-텍스트</strong> PTM들의 동향을 살펴본다.</li>
</ul>
<p><strong>도전 과제:</strong> </p>
<ul>
<li><p>멀티모달 학습에서 가장 큰 어려움은 <strong>이질적인 두 정보 (예: 픽셀 vs 단어) 간의 정합(alignment)</strong>이다. </p>
</li>
<li><p>즉, <strong>이미지의 시각적 개념</strong>과 <strong>텍스트의 언어 표현</strong>을 <strong>공통된 의미 공간</strong>에서 연결짓는 것이 핵심 문제다. 이를 위해 모델 구조는 크게 두 가지로 나뉜다:</p>
</li>
<li><p><strong>Two-Stream Architecture:</strong> 이미지와 텍스트를 <strong>각기 별도의 경로</strong>(신경망)로 처리한 후, <strong>후반부에 융합</strong>한다. 예를 들어 <strong>ViLBERT (2019)</strong>는 <strong>이미지 영역(region) 특징</strong>과 <strong>단어 임베딩</strong>을 <strong>두 개의 Transformer 흐름</strong>으로 각각 인코딩하고, 중간에 <strong>공동 어텐션 층</strong>을 두어 상호작용시켰다. <strong>LXMERT (2019)</strong>는 <strong>초반에는 별개 인코더</strong>로 처리하다가, 후반에 <strong>크로스-모달 Transformer 인코더</strong>로 결합하는 방식을 취했다. 두-스트림은 <strong>각 모달 특화 처리</strong>를 하면서 <strong>후기에 만난다</strong>는 점이 특징이다.</p>
</li>
<li><p><strong>Single-Stream Architecture:</strong> 이미지와 텍스트 입력을 <strong>초반부터 하나의 시퀀스</strong>로 취급하여 <strong>단일 Transformer</strong>에 넣는 방식이다. <strong>VisualBERT (2019)</strong>, <strong>Unicoder-VL (2020)</strong>, <strong>B2T2 (2019)</strong> 등이 이런 구조인데, <strong>이미지 특징(예: object detection으로 얻은 Region feature)</strong>과 <strong>텍스트 임베딩</strong>을 <strong>순차로 나열</strong>하여 Transformer에 입력한다. 이 경우 <strong>어텐션 레이어가 자동으로 모달 간 연관을 학습</strong>한다. </p>
</li>
</ul>
<p><strong>어느 쪽이 우세한가:</strong> 초기엔 두-스트림과 싱글-스트림 중 <strong>어느 구조가 더 나은지 합의가 없었다</strong>. </p>
<ul>
<li>두-스트림은 모달별 전문화를 살릴 수 있고, 싱글-스트림은 간결하고 모든 상호작용을 하나의 Transformer에서 처리한다. </li>
<li>최근 경향은 <strong>모델 단순성과 파라미터 효율 측면에서 싱글-스트림이 많이 쓰이는 추세</strong>이다. </li>
<li>대규모 데이터에 대해서는 <strong>단일 Transformer로도 충분히 모달 결합 표현 학습</strong>이 가능해, 구현이 간편한 쪽으로 기우는 분위기다.</li>
</ul>
<p><strong>데이터 자원:</strong> 멀티모달 PTM 학습에는 <strong>대량의 이미지-텍스트 쌍</strong> 데이터가 필요하다. 주로 <strong>웹 크롤링 캡션 데이터</strong>(예: <strong>Conceptual Captions</strong>, <strong>SBU Captions</strong>)나, <strong>MS-COCO, Flickr30k</strong> 같은 <strong>캡션 달린 이미지 데이터셋</strong>들이 활용된다. </p>
<ul>
<li>또한 <strong>VQA(시각질의응답), GQA, Visual Genome</strong> 등 <strong>이미지-질문-텍스트 삼중 데이터</strong>도 사용된다. </li>
<li><strong>UNITER (2020)</strong>는 <strong>COCO, VG 등 5.6백만 이미지-텍스트 쌍을 통합</strong>하여 학습한 싱글-스트림 모델로, <strong>풍부한 데이터로 학습하면 성능이 크게 향상됨</strong>을 보였다. </li>
<li><strong>ImageBERT (2020)</strong>는 <strong>10백만 쌍</strong>으로 더 키워 <strong>이미지-텍스트 검색</strong> 성능을 높였다. </li>
<li>이처럼 <strong>데이터 규모 증대</strong>는 <strong>V&amp;L grounding</strong>(이미지-텍스트 맞추기) 능력을 향상시켰다. </li>
<li>한편, <strong>텍스트만 있는 일반 말뭉치</strong>를 추가로 사용하면, <strong>긴 복잡한 문장 이해</strong> 향상에 도움이 된다는 결과도 (<strong>VL-BERT</strong>, 2020) 있다. </li>
<li>그리고 <strong>Lu et al.(2020)</strong>은 아예 <strong>모든 V&amp;L 작업 데이터</strong>를 합쳐 <strong>멀티태스크 학습</strong>을 해보기도 했다. </li>
<li>이는 <strong>특화된 태스크 데이터가 PTM 성능에 주는 영향</strong>을 분석하려는 시도였다.</li>
</ul>
<p><strong>사전학습 태스크:</strong> 멀티모달 PTM들은 <strong>자체적 사전학습 과제</strong>를 설계하여 <strong>시각-언어 결합 표현</strong>을 학습한다. 대표적인 사전학습 목표들은</p>
<ul>
<li><p><strong>Masked Language Modeling (MLM):</strong> 캡션 문장을 일부 마스킹하고 <strong>이미지와 문맥</strong>을 활용해 가려진 단어를 예측한다. 이는 <strong>텍스트 이해</strong>에 이미지가 주는 도움을 주입한다.  </p>
</li>
<li><p><strong>Sentence-Image Alignment (SIA):</strong> <strong>이미지와 캡션이 짝이 맞는지</strong> (올바른 설명 vs 다른 이미지 설명) 이진 분류한다 . 모델이 <strong>이미지-텍스트 매칭</strong> 여부를 판단하도록 하여, 둘 사이 <strong>전반적 대응관계</strong>를 학습한다.  </p>
</li>
<li><p><strong>Masked Region Classification (MRC):</strong> 이미지에서 <strong>일부 객체 영역의 특징</strong>을 가리고, 그 <strong>영역의 객체 카테고리</strong>를 맞추게 한다. 이는 <strong>시각적 내용 이해</strong>를 도우며, <strong>비전 측의 MLM</strong>으로 볼 수 있다.  </p>
</li>
<li><p><strong>Masked Region Feature Regression (MRFR):</strong> 마스크한 객체 영역의 <strong>원래 특징 벡터 값</strong> 자체를 예측하도록 회귀한다. 이는 <strong>더 엄밀히 픽셀 수준 정보를 복원</strong>하는 훈련으로, 정교한 시각 정보 활용을 촉진한다.  </p>
</li>
<li><p><strong>종속 태스크 활용:</strong> </p>
</li>
<li><p>어떤 모델들은 사전학습 중에 <strong>다운스트림 태스크를 함께</strong> 풀게 하기도 했다. </p>
</li>
<li><p>예를 들어 <strong>LXMERT</strong>는 <strong>VQA(비주얼 QA)</strong>를 이미 사전학습 태스크로 포함시켰고, <strong>Unified VLP (Lu et al., 2020)</strong>는 <strong>모든 해당 분야 작업들을 멀티태스크 학습</strong>시켰다. </p>
</li>
<li><p>이는 <strong>학습 시에 곧바로 멀티태스크 피드백</strong>을 줘서, 모델이 <strong>태스크 특화 신호</strong>도 어느정도 흡수하게 한다.</p>
</li>
<li><p><strong>세부 정렬 목표:</strong> </p>
</li>
<li><p><strong>UNITER (2019)</strong>는 <strong>Optimal Transport</strong> 알고리즘을 이용해, <strong>이미지 영역과 단어 사이의 1:1 대응</strong>을 찾아내고 <strong>그 매칭 거리까지 최소화</strong>하는 <em>Word-Region Alignment</em> 태스크를 추가했다. </p>
</li>
<li><p>이를 통해 <strong>텍스트의 특정 단어가 이미지의 어느 영역에 대응하는지</strong> 미세하게 학습했다.  </p>
</li>
<li><p><strong>객체 태그 활용 (Oscar, 2020):</strong> 대부분 모델은 <strong>이미지→오브젝트 검출기→Region feature</strong>의 간접 경로로 학습하는데, <strong>Oscar</strong>는 <strong>검출된 객체 태그(라벨)</strong>를 <strong>텍스트 토큰 시퀀스에 추가</strong>하여, <strong>이미지-텍스트 사이에 명시적 연결 고리</strong>를 넣었다. </p>
</li>
<li><p>그리고 <strong>이미지+태그+캡션이 잘 맞는지</strong> 판단하는 새로운 사전학습 과제를 도입했다. </p>
</li>
<li><p>이 접근은 <strong>이미지와 언어 사이에 공통 Anchor(객체명)</strong>를 두어, 모델이 <strong>수월하게 양자 연결</strong>을 학습하도록 돕는다. </p>
</li>
<li><p>Oscar는 이로 인해 V&amp;L 이해와 생성 거의 모든 벤치마크에서 <strong>SOTA를 달성</strong>했다.</p>
</li>
<li><p><strong>생성 목적:</strong> </p>
</li>
<li><p>이해뿐 아니라 <strong>이미지→텍스트 생성</strong>을 염두에 둔 사전학습도 있다. </p>
</li>
<li><p><strong>VLP (2019)</strong>와 <strong>X-GPT (2020)</strong> 등은 <strong>seq2seq MLM</strong>을 사전학습에 사용했다. </p>
</li>
<li><p>이는 <strong>이미지를 인코더 입력, 캡션을 디코더 출력</strong>으로 두고, 디코더 측 텍스트를 부분 마스킹해서 채우도록 한 것이다. </p>
</li>
<li><p>이렇게 하면 <strong>이미지 캡셔닝</strong>처럼 <strong>이미지-&gt;텍스트 생성</strong> 능력이 길러진다.</p>
</li>
<li><p><strong>단순 대규모 대조학습:</strong> </p>
</li>
<li><p>위 복잡한 과제들과 대조적으로, <strong>CLIP (2021)</strong>와 <strong>WenLan (2021)</strong>은 <strong>아주 간단한 방법</strong>으로 거대한 이미지-텍스트 데이터(수억 쌍)를 학습했다. </p>
</li>
<li><p><strong>이미지 전체 임베딩</strong>과 <strong>문장 전체 임베딩</strong>을 뽑아 <strong>이미지-텍스트 맞추기(검색) 목표</strong> 하나만으로 학습한 것이다. </p>
</li>
<li><p>이 <strong>대조학습(contrastive learning)</strong> 방식은 충분한 데이터만 있으면 강력하여, CLIP의 경우 <strong>4억 쌍 웹 이미지-캡션</strong>으로 학습하여 <strong>광범위한 이미지 분류/검색에서 뛰어난 성능</strong>을 보였다. </p>
</li>
<li><p>이는 <strong>간단한 목표+막대한 데이터</strong>의 힘을 입증한 사례로, 실제 CLIP은 <strong>새로운 이미지 인식 패러다임</strong>으로 각광받고 있다.</p>
</li>
</ul>
<p><strong>응용 확장:</strong> </p>
<ul>
<li>멀티모달 PTM들은 <strong>이해와 생성 작업 모두</strong>에 적용된다. </li>
<li><strong>이미지-텍스트 검색, VQA, 캡셔닝</strong> 등은 잘 연구되었고, 최근에는 <strong>텍스트→이미지 생성</strong>까지 PTM가 진출했다. </li>
<li><strong>DALL-E (2021)</strong>는 <strong>Transformer로 텍스트 설명으로부터 이미지를 생성</strong>하는 혁신적 모델로, <strong>“아보카도 모양의 안락의자”</strong>같은 복합 개념 이미지를 그려내는 <strong>창의적 합성</strong> 능력을 보여주었다. </li>
<li><strong>CogView (2021)</strong>는 여기에 <strong>샌드위치 Transformer 구조와 희소 어텐션</strong> 등으로 <strong>안정성과 해상도</strong>를 높여, <strong>이미지 생성 품질(FID)</strong>에서 DALLE를 능가하기도 했다. </li>
<li>이러한 텍스트-이미지 생성 PTM들은 <strong>멀티모달 PTM의 응용 저변을 한층 확대</strong>했다.</li>
</ul>
<p><strong>다른 모달:</strong> </p>
<ul>
<li>이미지-텍스트 외에, <strong>비디오-텍스트</strong> PTM도 연구되고 있다. </li>
<li>비디오는 시간축이 있어 <strong>시계열 모달 융합과 방대한 프레임 처리</strong>가 과제다. </li>
<li>효율을 위해 <strong>동영상의 자막/오디오</strong>를 부분 활용하거나, <strong>프레임 일부만 샘플링</strong>하는 등 기법이 필요하다. </li>
<li><strong>청각(음성) &amp; 텍스트</strong>의 결합은 주로 <strong>음성→텍스트</strong>(STT) 파이프라인으로 처리되어 왔지만, <strong>멀티모달 멀티링구얼</strong> 맥락에서 <strong>음성 직접 포함</strong>에 대한 논의도 있다. </li>
<li>예를 들어 <strong>영어 음성→중국어 자막/음성</strong>을 한 PTM으로 할 수 있을까 등이 미래 연구 방향으로 제시된다다.</li>
</ul>
<p><strong>요약:</strong> </p>
<ul>
<li>멀티모달 사전학습은 <strong>“언어+α”</strong>로 AI 모델의 인지 범위를 넓히고 있다. </li>
<li><strong>시각-언어 PTM</strong>들은 구조 설계, 데이터 증강, 목표함수 설계 등 다양한 측면에서 발전해왔으며, 결과적으로 <strong>이미지 이해-설명, QA, 합성</strong> 등에서 성과를 내고 있다. </li>
<li>아직 <strong>진짜 실용적인 킬러 앱</strong>이 뭐냐는 질문은 남아있지만, <strong>인간처럼 모달 통합</strong>을 지향하는 이 흐름은 <strong>멀티모달 AI의 큰 줄기</strong>가 되고 있다.</li>
</ul>
<h3 id="53-knowledge-enhanced-pre-training-지식-강화-사전학습"><strong>5.3 Knowledge-Enhanced Pre-Training (지식 강화 사전학습)</strong></h3>
<p><strong>동기:</strong> </p>
<ul>
<li>PTM은 대규모 코퍼스로 학습되어 <strong>통계적 언어 패턴과 상식</strong>을 많이 내재하지만, <strong>정형화된 지식</strong> (예: 지식 그래프의 사실(triplet)들)이나 <strong>특정 도메인 전문지식</strong>에 대해서는 한계가 있을 수 있다. </li>
<li>인간이 구축한 <strong>지식(</strong>KB, 온톨로지, 주석 데이터 등<strong>)</strong>은 <strong>모델에게 좋은 선행 정보(prior)</strong>가 될 수 있다.</li>
<li>따라서 <strong>외부 지식을 PTM에 결합</strong>하여 <strong>언어이해의 질</strong>을 높이려는 연구가 진행 중이다.</li>
</ul>
<p><strong>범주:</strong> </p>
<ul>
<li><p>외부 지식은 <strong>구조적 지식(knowledge graphs 등)</strong>과 <strong>비구조 지식(도메인 텍스트, 태스크 레이블)</strong>으로 나눌 수 있다. 각각에 대한 시도가 있다:</p>
</li>
<li><p><strong>구조화 지식 통합:</strong> 전통적인 <strong>지식 그래프(KG)</strong>는 <strong>엔티티(개체)와 관계</strong>로 구성된다. </p>
</li>
<li><p>PTM에 이를 넣는 한 방법은 <strong>KG의 엔티티/관계 임베딩을 미리 학습해 모델에 삽입</strong>하거나, <strong>텍스트에 등장하는 엔티티에 해당 임베딩을 매핑</strong>하여 함께 처리하는 것이다. </p>
</li>
<li><p>예컨대 <strong>KnowBERT (2019)</strong>는 mention이 검출되면 <strong>별도 Knowledge Encoder</strong>로 해당 개체의 KG 임베딩을 불러와 BERT에 통합했다. </p>
</li>
<li><p><strong>ERNIE (Tsinghua, 2019)</strong>는 <strong>학습 중에 개체 링크 정보를 활용해 같은 개체는 같은 임베딩으로 강제</strong>하는 등 <strong>텍스트-지식 정합 학습</strong>을 했다. </p>
</li>
<li><p>이러한 방식은 <strong>텍스트와 KG사이 align</strong> 오류 등의 어려움이 있지만, 효과가 있었다. </p>
</li>
<li><p><strong>Wang et al.(2021)</strong>은 한걸음 더 나아가, <strong>Wikidata 개체의 텍스트 설명과 KG 임베딩을 함께 학습</strong>하여 <strong>지식이 녹아든 언어표현</strong>을 얻었다. </p>
</li>
<li><p>또한 일부 연구는 <strong>KG의 경로 또는 아예 서브그래프 자체를 시퀀스로 표현</strong>하여 텍스트와 함께 Transformer에 넣기도 했다. </p>
</li>
<li><p>반대로, 아예 <strong>KG 삼중항들을 단순 문장처럼 변환해</strong> PTM이 스스로 학습하게 하는 접근도 있다. </p>
</li>
<li><p>이렇게 하면 <strong>모델이 알아서 KG패턴을 학습</strong>하지만, 너무 많은 양을 다 집어넣긴 어렵다. 특이한 시도로 <strong>OAG-BERT (2021)</strong>는 <strong>거대한 학술 지식그래프(OAG)</strong>의 <strong>0.7B 개체와 2B 관계</strong>를 통합했다. </p>
</li>
<li><p>이는 DB 규모의 지식을 PTM에 넣은 극단적 케이스로, <strong>PTM이 광범위한 전문지식까지 흡수</strong>할 잠재력을 보여준다.</p>
</li>
<li><p><strong>비구조 지식 통합:</strong> </p>
</li>
<li><p>구조화되지 않은 지식은 <strong>특정 도메인 코퍼스</strong>나 <strong>태스크별 추가 정보</strong> 등을 의미한다. </p>
</li>
<li><p><strong>BioBERT, SciBERT</strong>처럼 <strong>일반 PTM을 해당 도메인 텍스트로 추가 사전학습</strong>하면 도메인 지식이 증강된다. </p>
</li>
<li><p><strong>Gururangan(2020)</strong>은 이런 <strong>도메인 적응 사전학습</strong>의 효과를 체계적으로 분석했다. </p>
</li>
<li><p>또한 <strong>다운스트림 태스크에 존재하는 레이블</strong>(예: 감성분석의 “긍/부정” 태그)이 있다면, <strong>사전학습에 이 정보를 이용</strong>할 수도 있다. </p>
</li>
<li><p><strong>Ke et al.(2020)</strong>은 <strong>태스크 데이터에 인접한 형태소 정보, 개체 주석</strong> 등을 활용해 <strong>특정 태스크 표현 학습</strong>을 향상시켰다. </p>
</li>
<li><p>다만 이러한 <strong>지식도 결국 모델 파라미터 속에 암묵 저장</strong>되는 것이므로, 해석이 어렵다는 점은 동일하다. </p>
</li>
<li><p>이를 보완하기 위해 <strong>Retrieval-Augmented</strong> 방법이 등장했는데 (앞서 REALM 등 언급), <strong>fine-tuning 시에라도 모델이 외부 지식베이스를 참조</strong>하도록 하여 <strong>직접 지식 추출 근거를 보여주게</strong> 한다. </p>
</li>
<li><p>또 다른 아이디어로, <strong>Adapter 모듈</strong>을 각 지식소스별로 따로 훈련해 <strong>“이 출력은 어느 지식에서 온 것”</strong>인지 구분하려는 시도도 있다.</p>
</li>
</ul>
<p><strong>요약:</strong> </p>
<ul>
<li><strong>지식 강화 PTM</strong>은 <strong>순수 텍스트 통계 이상의 배경지식</strong>을 모델에 심는 방향이다. </li>
<li><strong>구조적 지식</strong>은 명확하지만 다루기 복잡하고, <strong>비구조 지식</strong>은 간편하지만 노이즈나 한계가 있다. </li>
<li>현재까지는 <strong>도메인 특화 PTM</strong>들이 큰 성과를 내고 (예: BioBERT가 바이오 분야 SOTA), <strong>지식그래프 결합</strong>은 점진적 개선 단계에 있다. </li>
<li><em>논문에서는 이 분야 세부를 짧게 다루고 넘어가지만, 이후 8.5, 8.6에서 “modeledge” 개념과 “지식 많은 PTM”에 대한 심화 논의가 전개된다.</em></li>
</ul>
<hr />
<h2 id="6-improving-computational-efficiency-컴퓨팅-효율-향상"><strong>6. Improving Computational Efficiency (컴퓨팅 효율 향상)</strong></h2>
<p><strong>섹션 목적:</strong> </p>
<ul>
<li>사전학습 모델의 <strong>막대한 연산량과 모델 크기</strong>는 실용화에 큰 장애가 된다. </li>
<li>Section 6에서는 <strong>PTM의 훈련 및 추론 효율을 높이기 위한 다양한 노력</strong>을 소개한다. </li>
<li><strong>시스템 차원의 최적화</strong>부터 <strong>학습 알고리즘 개선</strong>, <strong>모델 자체 압축</strong>까지 여러 계층의 기법을 다룬다. </li>
</ul>
<h3 id="61-system-level-optimization-시스템-수준-최적화"><strong>6.1 System-Level Optimization (시스템 수준 최적화)</strong></h3>
<p><strong>개요:</strong> </p>
<ul>
<li><strong>모델을 바꾸지 않고</strong> 하드웨어 및 분산 학습 측면에서 <strong>연산/메모리 효율</strong>을 높이는 방법들이다. </li>
<li>이는 <strong>모델 불문</strong> 적용 가능하며, 현재 거대 PTM 훈련에 <strong>광범위하게 활용</strong>되고 있다. </li>
<li>크게 <strong>단일 디바이스 최적화</strong>와 <strong>멀티 디바이스 분산 학습 최적화</strong>로 나눌 수 있다.</li>
</ul>
<p><strong>(a) 단일 장비 최적화:</strong>  </p>
<ul>
<li><p><strong>Mixed Precision Training (혼합 정밀도):</strong> 일반적으로 딥러닝 프레임워크는 <strong>FP32 부동소수점</strong>으로 연산하지만, 많은 경우 <strong>FP16(half precision)</strong>으로 바꾸면 <strong>메모리 점유와 연산 시간을 절반으로 줄일 수 있다</strong>. </p>
</li>
<li><p>다만 FP16은 <strong>정밀도 부족이나 overflow</strong> 문제로 학습 불안정이 생길 수 있다. </p>
</li>
<li><p>이를 해결한 것이 <strong>혼합 정밀도 기법</strong>으로, <strong>일부 중요한 가중치는 FP32로 유지</strong>하고, <strong>Loss Scaling</strong> 등을 통해 underflow를 방지한다. </p>
</li>
<li><p>NVIDIA의 Apex 등 구현으로 현재 PTM 훈련에 혼합정밀도가 표준처럼 쓰이며, <strong>메모리/시간을 상당히 절약</strong>한다. (주의: 모델 초기화가 나쁘면 여전히 불안정 가능성이 있어, <strong>향후 더 안전한 방법 연구</strong>가 필요하다).</p>
</li>
<li><p><strong>Gradient Checkpointing:</strong> </p>
</li>
<li><p>Transformer같이 깊은 모델에서는 <strong>역전파 시 각 레이어의 중간 활성값</strong>(forward activations)을 저장해두어야 하는데, 이들이 <strong>가중치보다 훨씬 많은 메모리</strong>를 차지한다. </p>
</li>
<li><p><em>Gradient Checkpointing</em>은 <strong>일부 레이어의 활성값만 저장</strong>하고 나머지는 저장 안 했다가, 역전파 때 <strong>다시 forward 연산으로 재계산</strong>하는 기법이다. </p>
</li>
<li><p><strong>계산량은 늘지만 메모리 사용이 감소</strong>하여, 한정된 GPU 메모리로 더 큰 모델/배치를 처리할 수 있게 해준다.</p>
</li>
<li><p><strong>CPU-GPU Offloading:</strong> PTM 훈련 중 <strong>GPU 메모리에 모델 파라미터+활성값 모두 올리기 벅찰 때</strong>, <strong>일부를 속도는 느리지만 용량 큰 CPU 메모리로 옮겨두는</strong> 방법이 있다. </p>
</li>
<li><p><strong>ZeRO-Offload (2021)</strong> 등이 여기에 해당하며, GPU 계산과 CPU↔GPU 전송을 <strong>비동기 중첩</strong>시켜 성능을 최적화한다. </p>
</li>
<li><p>이렇게 하면 <strong>저가 GPU 여러 장과 CPU 메모리로도</strong> 초거대 모델을 훈련 가능하여, 비용 접근성을 높인다.</p>
</li>
</ul>
<p><strong>(b) 다중 장비(Distributed) 최적화:</strong>  </p>
<ul>
<li><p><strong>Data Parallelism (데이터 병렬화):</strong> 가장 </p>
</li>
<li><p>전통적인 분산 기법으로, <strong>큰 배치를 여러 GPU에 나눠</strong> 동시에 forward/backprop 후, <strong>그래디언트를 All-reduce로 모아 업데이트</strong>하는 방식이다. </p>
</li>
<li><p>구현이 간단하고 <strong>적은 통신으로 선형 가속</strong>을 기대할 수 있어, <strong>모델 파라미터 수가 비교적 적을 때</strong> 주로 사용된다. </p>
</li>
<li><p>하지만 PTM처럼 <strong>모델이 거대해지면</strong>, <strong>각 GPU에 모델 사본</strong>을 올릴 수 없거나, 올려도 <strong>최적화 상태(optimizer states) 메모리</strong>가 문제가 된다. </p>
</li>
<li><p><strong>Model Parallelism (모델 병렬화):</strong> </p>
</li>
<li><p><strong>모델 자체를 쪼개어 여러 디바이스에 걸쳐 올리는 방법</strong>이다. </p>
</li>
<li><p>예를 들어, <strong>Transformer의 헤드들을 나누거나, FFN 중간차원 분할</strong> 등으로 GPU들에 나눠 계산한다. </p>
</li>
<li><p><strong>Megatron-LM (2019)</strong>은 self-attention과 FFN의 행렬 연산을 분할해 여러 GPU에 나눴고, <strong>Mesh-TensorFlow (2018)</strong>는 사용자가 <strong>텐서 차원별 분할</strong>을 지정할 수 있게 했다. </p>
</li>
<li><p>모델 병렬화는 <strong>한 GPU에 다 안들어가는 거대 모델</strong>을 다룰 수 있게 하지만, <strong>레이어 간 통신</strong>(forward/backprop 시 reduce-scatter, all-gather 등)이 필요해 <strong>통신 병목</strong>이 생길 수 있다. </p>
</li>
<li><p>일반적으로 <strong>가능하면 데이터 병렬을 쓰고</strong>, <strong>모델이 너무 클 때 모델 병렬을 추가 적용</strong>하는 식으로 혼합 사용한다.</p>
</li>
<li><p><strong>Optimizer State Sharding (ZeRO):</strong> 데이터 병렬 시 <strong>각 GPU마다 모델+optimizer 상태 복제</strong>로 인한 메모리 낭비를 해결하기 위해, <strong>각 노드가 파라미터와 옵티마 상태의 일부만 가지고 있는</strong> 방법이 고안되었다. </p>
</li>
<li><p><strong>ZeRO (2020)</strong>는 <strong>각 GPU가 전체 optimizer state의 1/N만 보유</strong>하도록 하고, 업데이트 단계에서 모아준다. </p>
</li>
<li><p>이렇게 하면 <strong>병렬 GPU 수가 곧 메모리 이득 배수</strong>가 되어, <strong>수십억~조개 파라미터 모델도 메모리 내 학습</strong>이 가능해졌다. (DeepSpeed 라이브러리에 구현되어 널리 활용됨.)</p>
</li>
<li><p><strong>Pipeline Parallelism:</strong> </p>
</li>
<li><p>또 하나의 모델 병렬화 방법으로, <strong>모델의 층들을 여러 GPU에 직렬로 배치</strong>하는 것이다. </p>
</li>
<li><p>1<del>N층 GPU0, N+1</del>끝층 GPU1 이런 식으로 나누고, <strong>한 미니배치도 여러 마이크로배치로 쪼개</strong> 파이프라인 흐르듯 처리한다. </p>
</li>
<li><p><strong>GPipe (2019)</strong>가 이 기법을 정립했고, 이후 <strong>TeraPipe (2021)</strong>는 Transformer를 <strong>토큰 단위 pipeline 병렬화</strong>하여 <strong>더 세밀하게 분할</strong>하기도 했다. </p>
</li>
<li><p>파이프라인 병렬은 <strong>stage 간 활성값만 통신</strong>하면 되므로 <strong>통신 오버헤드가 상대적으로 작고</strong> 메모리 균형 잡기가 쉽다. </p>
</li>
<li><p>다만 <strong>pipeline bubble</strong>(파이프라인이 채워지기 전후의 유휴 시간) 이슈와, <strong>매 batch마다 stage간 sync 필요</strong> 등이 단점이다.</p>
</li>
</ul>
<p><strong>(c) 프레임워크 및 도구:</strong> </p>
<ul>
<li>이러한 복잡한 분산 전략을 수동으로 구현하는 것은 어려우므로, <strong>Mesh-TensorFlow, GShard, Megatron-LM, DeepSpeed, OneFlow, MindSpore, FlexFlow</strong> 등 많은 툴킷들이 나왔다. </li>
<li>예컨대 <strong>OneFlow</strong>는 사용자가 <strong>SBP(signature)</strong>만 설정하면 <strong>병렬화 정책</strong>을 추론해준다. </li>
<li><strong>GShard</strong>는 <strong>몇 개 텐서에 샤딩 annotation</strong>만 하면 나머지 텐서의 shard 방법을 전파시켜 준다. </li>
<li><strong>FlexFlow</strong>는 자동 탐색으로 최적 병렬 스케줄을 찾아내는 접근도 취한다. </li>
<li>이러한 <strong>고급 분산 학습 프레임워크</strong>들은 앞으로 <strong>병렬 전략의 자동화</strong>를 통해, 사용자가 모델 개발에만 집중할 수 있도록 발전할 것이다.</li>
</ul>
<p><strong>요약:</strong> </p>
<ul>
<li>시스템 차원의 최적화 기법들은 <strong>PTM 훈련의 실제적 토대</strong>라 할 수 있다. </li>
<li><strong>혼합정밀, 체크포인팅</strong> 등은 거의 기본으로 쓰이고, <strong>분산 학습</strong>은 거대 PTM에 필수다. </li>
<li>데이터/모델/파이프라인 병렬 및 그 혼합 전략은 <strong>하드웨어 구성과 모델 구조에 따라</strong> 최적 조합이 다르며, 이를 <strong>자동 최적화하는 소프트웨어의 중요성</strong>도 커지고 있다. </li>
<li>이 방향의 발전은 <strong>“더 큰 모델을 더 저렴하게”</strong> 가능케 하여, PTM 연구 가속 및 접근성 향상에 기여하고 있다.</li>
</ul>
<h3 id="62-efficient-pre-training-효율적인-사전학습"><strong>6.2 Efficient Pre-Training (효율적인 사전학습)</strong></h3>
<p><strong>동기:</strong> </p>
<ul>
<li>앞서 시스템 최적화는 <strong>하드웨어 활용 최적화</strong>였다. </li>
<li>6.2에서는 <strong>학습 알고리즘 자체를 개선</strong>하여 <strong>더 적은 데이터/시간으로 같은 성능</strong>을 내는 연구를 다룬다. </li>
<li>이는 <strong>사전학습 과제 설계</strong>부터 <strong>학습 일정(schedule)</strong>, <strong>모델 학습 방식</strong> 등 여러 측면을 포함한다.</li>
</ul>
<p><strong>Efficient Training Methods:</strong>  </p>
<ul>
<li><p><strong>학습 목표 개선:</strong> 일반적 MLM은 <strong>한 샘플에서 15% 토큰만 예측</strong>하므로 <strong>정보 활용률이 낮다</strong>. </p>
</li>
<li><p>앞서 <strong>ELECTRA</strong>는 <strong>모든 토큰에 대해 진짜/가짜 판별</strong>을 하게 하여 이 효율 문제를 해결했다. </p>
</li>
<li><p>그 결과 훨씬 <strong>적은 스텝으로 동일 성능</strong>에 도달하는 효과가 있었다. </p>
</li>
<li><p>또, MLM의 <strong>랜덤 마스킹</strong>은 <strong>난이도 편차</strong>가 커서, 어떤 마스크는 쉽게 맞추고 어떤 건 어렵다. 이로 인해 학습이 <strong>비효율적</strong>일 수 있다. </p>
</li>
<li><p>이를 개선하려 <strong>중요한 토큰을 더 자주 마스킹</strong>하거나, <strong>gradient 기반으로 예측 어려운 토큰 위주 마스킹</strong>하는 기법이 연구되었다. </p>
</li>
<li><p>이러한 <em>난이도 조절 마스킹</em>은 <strong>모델이 더 유용한 학습 신호에 집중</strong>하게 해준다.</p>
</li>
<li><p><strong>학습 동역학 개선:</strong> </p>
</li>
<li><p><strong>대형 PTM은 보통 매우 큰 배치</strong>로 학습하는데, <strong>배치를 무턱대고 키우면 학습이 불안정</strong>해질 수 있다. </p>
</li>
<li><p>그래서 <strong>학습 초기에 learning rate를 선형 증가(warmup)</strong>시키는 전략이 도입되어 표준으로 자리잡았다. </p>
</li>
<li><p>이로써 큰 배치에서도 수렴이 원활해졌다. </p>
</li>
<li><p>또한 PTM은 <strong>동일 구조의 층을 여러 개 쌓은 형태</strong>인데, 전통적 방법은 <strong>모든 층을 같은 속도로 같이 학습</strong>시킨다. </p>
</li>
<li><p>그런데 연구자들은 <strong>Transformer의 여러 층이 유사한 어텐션 패턴을 학습</strong>한다는 점에 주목하여, <strong>얕은 모델을 먼저 학습한 뒤 복제해서 심층화</strong>하는 방법을 시도했다. </p>
</li>
<li><p>이는 <strong>학습 난이도를 계단식으로 높이는</strong> 효과를 줘 빠른 수렴을 보였다. </p>
</li>
<li><p>또한 <strong>훈련 중 일부 층을 임의로 drop</strong>하여 <strong>backprop 부하를 줄이고</strong> (LayerDrop 기법) <strong>효과는 유지</strong>하는 방법도 제안되었다. </p>
</li>
<li><p>마지막으로, <strong>You et al.(2017, 2020)</strong>은 <strong>층마다 다른 학습률</strong>을 쓰는 <em>Layer-wise Adaptive LR (LAMB 옵티마)</em>를 개발하여, <strong>배치 크기가 클 때 각 층에 맞는 학습 속도</strong>를 적용함으로써 <strong>수렴 향상</strong>을 보였다. 이는 BERT 대용량 배치 학습 등에 활용되었다.</p>
</li>
</ul>
<p><strong>Efficient Model Architectures:</strong>  </p>
<ul>
<li><strong>어텐션 최적화 (선형/희소 어텐션):</strong> Transformer의 <strong>어텐션은 시퀀스 길이에 제곱적으로 느리고 메모리 많이 차지</strong>해서 긴 입력에 비효율적이다. </li>
<li>이를 개선해 <strong>복잡도를 선형으로 만들려는</strong> 연구가 많았다. <strong>Linformer, Performer 등</strong>은 <strong>어텐션 가중치를 저랭크 근사</strong>하는 커널을 사용해 이론적으로 O(n)으로 줄였다. </li>
<li><strong>Sparse Transformer (2019)</strong>는 <strong>각 토큰이 일부 위치(국소 이웃 등)만 attend</strong>하도록 <strong>어텐션 행렬을 스파스화</strong>했고, <strong>Longformer, BigBird 등(2020)</strong>은 <strong>글로벌 토큰+로컬 윈도우 어텐션</strong>을 조합하여 <strong>일부 토큰만 전체와 연결</strong>되게 했다. </li>
<li>또한 <strong>Routing Transformer (2020)</strong>는 <strong>학습된 해시로 유사 토큰끼리 군집</strong>시키는 어텐션을 제안했다. </li>
<li>이런 방법들은 <strong>입력 길이가 수천-만 단위</strong>로 길 때 효과적이며, GPT-3 등도 일부 sparse attention 아이디어를 사용했다.</li>
<li><strong>Mixture-of-Experts (MoE) 구조:</strong> <strong>모델 용량을 늘리면서 연산량은 덜 증가</strong>시키는 방법으로, <strong>MoE</strong>가 재조명되었다. </li>
<li><strong>Shazeer et al.(2017)</strong>이 MoE 레이어를 제안했는데, 이는 <strong>여러 개 sub-network (expert) 중 일부만 입력마다 활성화</strong>하는 구조다. </li>
<li><strong>Switch Transformer (2021)</strong>는 이를 PTM에 적용하여, <strong>각 Transformer 층에 여러 FFN Expert를 두고 토큰마다 한 Expert만 실행</strong>하도록 했다. </li>
<li>이러면 <strong>모델 파라미터 총합</strong>은 엄청 커져도 <strong>실제 계산은 일부 expert만</strong> 하므로 <strong>기본 모델과 비슷한 속도</strong>를 유지한다. </li>
<li>실험상 <strong>MoE 기반 모델은 동일 자원 내 학습 시 일반 모델보다 빨리 수렴</strong>하는 경향이 확인되었다. </li>
<li>이는 <strong>효과적 모델 용량 증가</strong> 덕분으로, 거대 모델의 <strong>희소 활성화</strong>가 향후 중요한 효율 연구 방향임을 시사한다. (이미 <strong>Deepspeed</strong> 등에서 MoE 지원이 추가되었고, <strong>Amazon의 Tutel(2021)</strong> 같은 MoE 툴킷도 공개되었다.)</li>
</ul>
<p><strong>요약:</strong> </p>
<ul>
<li>효율적 사전학습 방안들은 <strong>“동일 모델/데이터로 더 빨리 학습 또는 동일 시간/메모리로 더 큰 모델 학습”</strong>을 가능케 한다. </li>
<li>학습목표 개선(ELECTRA 등)은 <strong>시료효율</strong>을 높였고, 대용량 학습의 <strong>안정성 기법(warmup, LAMB)</strong>은 <strong>수렴 시간</strong>을 줄였다. </li>
<li>또한 <strong>구조적 변화(희소 어텐션, MoE)</strong>는 <strong>모델 자체의 연산 부담</strong>을 줄여 <strong>긴 입력</strong>이나 <strong>초대형 모델</strong>을 실용화하는 데 기여했다. </li>
<li>이러한 기법 덕분에 현재 연구자들은 <strong>과거보다 적은 비용으로 더 강력한 PTM</strong>을 탐구할 수 있게 되었다.</li>
</ul>
<h3 id="63-model-compression-모델-압축"><strong>6.3 Model Compression (모델 압축)</strong></h3>
<p><strong>필요성:</strong> </p>
<ul>
<li>사전학습 모델은 크면 클수록 강력하지만, <strong>실제 배포/서비스에는 경량화가 필수</strong>이다. </li>
<li>모바일이나 임베디드 환경, 또는 서버에서도 지연을 줄이려면 <strong>추론 시간을 단축</strong>해야 한다. </li>
<li>Model Compression은 <strong>훈련된 큰 모델을 작은 모델로 변환</strong>하여 <strong>추론 효율</strong>을 높이는 기법들을 일컫는다.</li>
</ul>
<p><strong>방식들:</strong>  </p>
<ul>
<li><p><strong>Parameter Sharing (파라미터 공유):</strong> <strong>모델 내 중복 파라미터를 줄이는</strong> 기법이다. </p>
</li>
<li><p><strong>ALBERT</strong>가 대표적 사례로, <strong>임베딩 행렬을 분해(차원 축소)</strong>하고 <strong>모든 Transformer 레이어 가중치를 공유</strong>함으로써 <strong>BERT-base 대비 매개변수 1/10 수준</strong>으로 줄였다. </p>
</li>
<li><p>그럼에도 성능은 비슷하거나 오히려 향상되었는데, 이는 <strong>PTM가 과적절히 파라미터가 많다(over-parameterized)</strong>는 점을 드러낸다. </p>
</li>
<li><p>파라미터 공유는 <strong>모델 크기 자체를 줄이는</strong> 방법이지만, 레이어 수는 같으므로 <strong>추론 속도 개선 효과는 제한적</strong>일 수 있다. (ALBERT는 오히려 레이어 공유로 <strong>fine-tune시 속도 저하</strong>를 겪었다고 한다.</p>
</li>
<li><p><strong>Model Pruning (모델 가지치기):</strong> <strong>큰 모델의 일부 weight나 구조를 잘라내는</strong> 기법이다 </p>
</li>
<li><p><strong>가중치 프루닝</strong>은 NN 가지치기의 전통으로, <strong>값이 작은 가중치들을 0으로 만들어 희소화</strong>하고, 하드웨어 최적화를 통해 속도를 높인다. </p>
</li>
<li><p>BERT에도 적용되어, <strong>전체 파라미터 30~40% 제거해도 성능 거의 유지</strong>됨이 관찰되었다. </p>
</li>
<li><p><strong>Attention Head Pruning</strong> 연구도 있어서, <strong>많은 self-attention 헤드들 중 일부만 남기고 없애도 성능 저하 미미</strong>함이 밝혀졌다. </p>
</li>
<li><p>예컨대 <strong>Voita(2019)</strong>는 중요하지 않은 헤드 대부분을 제거했고, <strong>Michel(2019)</strong>도 비슷한 결론을 냈다. </p>
</li>
<li><p>이 결과는 <strong>PTM 내 다수의 헤드와 파라미터가冗長</strong>임을 시사하며, <strong>희소 구조 모델</strong>에 대한 이론적 뒷받침도 된다. </p>
</li>
<li><p>또 <strong>Layer Pruning</strong>도 시도되었다 – <strong>Fan(2019)</strong>은 훈련 중 레이어를 드롭하여 <strong>얕은 모델로 distillation</strong>하거나, <strong>LayerDrop</strong>처럼 추론 시 일부 층 생략으로 속도를 높이는 방법도 있다.</p>
</li>
<li><p>전반적으로 pruning은 <strong>성능↔속도/크기 간 트레이드오프</strong>를 조절할 수 있는 유용한 도구로 쓰인다.</p>
</li>
<li><p><strong>Knowledge Distillation (지식 증류):</strong> </p>
</li>
<li><p>가장 널리 쓰이는 PTM 압축법이다. <strong>큰 “교사” 모델의 행동</strong>을 <strong>작은 “학생” 모델</strong>이 모방하게 하여 학습시키는 것 이렇게 하면 <strong>교사의 지식(modeledge)을 학생으로 전달</strong>하여, <strong>학생 단독 학습 때보다 성능 향상</strong>을 이끌 수 있다. </p>
</li>
<li><p><strong>DistilBERT (2019)</strong>, <strong>TinyBERT (2019)</strong>, <strong>BERT-PKD (2019)</strong>, <strong>MiniLM (2020)</strong> 등이 대표적이다. </p>
</li>
<li><p>이들은 각기 다른 증류 손실을 쓰는데, <strong>교사의 출력 확률분포</strong>(soft target)을 맞추거나, <strong>은닉 상태/어텐션 행렬</strong>을 맞추는 등 방법이 있다. </p>
</li>
<li><p>증류의 장점은 <strong>모델 구조를 학생에 맞게 자유 설계 가능</strong>하고 (예: DistilBERT는 BERT의 절반 레이어), <strong>추론시엔 학생만 쓰이므로 속도가 빨라진다</strong>는 것이다. </p>
</li>
<li><p>실제 DistilBERT는 BERT보다 2배 빠르고 성능은 97% 수준이라, 실용에 많이 활용된다. </p>
</li>
<li><p>다만 <strong>증류를 제대로 하려면 교사 모델의 사전학습에 쓰인 데이터</strong>를 학생이 어느 정도 봐야 하는데, <strong>이 코퍼스는 공개되지 않는 경우</strong>가 많아 문제다. </p>
</li>
<li><p>또한 <strong>교사 모델을 전체 코퍼스에 infer</strong>하는 비용도 크다. 
= 이러한 어려움에도, 현재 PTM 경량화에서 증류는 매우 활발한 연구 분야다.</p>
</li>
<li><p><strong>Model Quantization (양자화):</strong> 이는 <strong>실수 파라미터를 낮은 비트 정밀도로 표현</strong>하여 모델 크기를 줄이고 CPU등에서 빠르게 하는 기술이다. </p>
</li>
<li><p>이미 CNN 분야에서 8-bit, 4-bit 양자화 등이 많이 연구되었다. </p>
</li>
<li><p>PTM쪽도 <strong>Q8BERT (2019)</strong>가 <strong>8비트 양자화로 BERT를 4배 압축</strong>하면서도 성능 저하를 억제함을 보였다. </p>
</li>
<li><p><strong>1~2비트 (binary/ternary) 양자화</strong>는 정보손실이 커서 직접 하긴 어렵지만, <strong>Q-BERT (2020)</strong>는 <strong>Hessian spectral 분석으로 가중치별 다른 비트폭 할당</strong>(민감한 가중치는 4bit, 덜 민감한 건 2bit 등)하는 방식으로 <strong>초저비트 양자화</strong>를 달성했다. </p>
</li>
<li><p><strong>TernaryBERT (2020)</strong>는 <strong>증류와 양자화를 결합</strong>하여, <strong>3값 양자화 학생모델이 full-precision 교사를 모방</strong>하게 훈련함으로써 성능 저하를 최소화했다. </p>
</li>
<li><p>이렇게 <strong>1-3bit 극단 양자화</strong>도 연구되지만, <strong>특수 하드웨어 필요</strong> 등 실용 장벽도 있다.</p>
</li>
<li><p>반면, <strong>8bit 양자화</strong>는 비교적 안전하며 TPU 등에서도 지원되어, <strong>트랜스포머 추론 가속</strong>에 실사용되고 있다.</p>
</li>
</ul>
<p><strong>요약:</strong> </p>
<ul>
<li>모델 압축 기법들은 <strong>큰 PTM의 추론 비용을 낮춰 실전 배치</strong>를 용이하게 한다. 
= <strong>지식 증류</strong>는 <strong>성능 보존율이 높고 범용적</strong>이어서 가장 인기 있으며, <strong>프루닝/공유</strong>는 <strong>구조 효율화</strong>에, <strong>양자화</strong>는 <strong>메모리/장치 효율화</strong>에 기여한다. </li>
<li>실제 응용에서는 이 방법들을 조합하기도 한다 (예: DistilBERT+양자화). </li>
<li>이러한 노력으로 이제 <strong>스마트폰에서도 BERT 기반 기능</strong>을 어느 정도 돌릴 수 있게 되었고, <strong>서버 추론 비용</strong>도 절감되고 있다. </li>
<li>즉, <strong>압축 기법은 PTM의 대중화와 산업적 활용을 가능케 한 필수 기술</strong>이라 할 수 있다.</li>
</ul>
<h2 id="7-interpretation-and-theoretical-analysis-이해-가능성-및-이론적-분석"><strong>7. Interpretation and Theoretical Analysis (이해 가능성 및 이론적 분석)</strong></h2>
<p><strong>섹션 목적:</strong> </p>
<ul>
<li>PTM가 강력하지만 <strong>“왜 이렇게 동작하는가?”</strong>, <strong>“무엇을 학습했는가?”</strong>에 대한 과학적 이해는 부족한 편이다. </li>
<li>Section 7에서는 PTM의 <strong>내부 행동과 특성</strong>을 밝혀내려는 연구들과, <strong>PTM의 성공을 이론적으로 설명</strong>하려는 시도를 다룬다. </li>
<li>특히 <strong>PTM이 담고 있는 지식의 종류</strong>, <strong>강건성 문제</strong>, <strong>모델 구조의 희소성</strong>, <strong>사전학습의 이론</strong> 네 가지 주제로 나누어 본다.</li>
</ul>
<h3 id="71-knowledge-of-ptms-ptm이-담고-있는-지식"><strong>7.1 Knowledge of PTMs (PTM이 담고 있는 지식)</strong></h3>
<p><strong>배경:</strong> </p>
<ul>
<li>사전학습을 거친 PTM은 대량의 텍스트로부터 <strong>암묵적인 “지식”</strong>을 습득한다. 이 지식을 크게 <strong>언어학적 지식(linguistic knowledge)</strong>과 <strong>세계 지식(world knowledge)</strong>으로 구분할 수 있다.</li>
<li>전자는 <strong>문법, 어휘, 구문 등 언어 구조 정보</strong>, 후자는 <strong>상식, 사실, 개념적 지식</strong>을 의미한다.</li>
</ul>
<p><strong>(A) 언어학적 지식:</strong> </p>
<ul>
<li>PTM의 <strong>언어적 이해력</strong>은 많이 연구되었다. </li>
<li>기존 얕은 모델 (CNN/RNN) 대비, PTM는 <strong>층이 많고 파라미터가 방대</strong>하여 <strong>풍부한 언어 패턴</strong>을 학습할 수 있다. </li>
<li>이를 분석하는 주된 방법론은:  </li>
<li><strong>표현 프러빙(Prob)</strong>: PTM의 파라미터는 고정하고, <strong>특정 언어현상을 판별하는 얕은 분류기를 은닉표현 위에 학습</strong>시켜 성능을 본다. </li>
<li>예: PTM의 단어 벡터로 품사분류나 구문성 판단을 해보는 것. 성능이 높다면 그 정보가 PTM 표현에 함축되었다고 볼 수 있다. 이 방법은 <strong>태스크마다 새 분류기만 붙이면 되어 편리</strong>하고 널리 사용되었다.  </li>
<li><strong>표현 분석(Representation Analysis)</strong>: PTM의 은닉 벡터들 간 <strong>유사도/거리 등을 계산</strong>해, <strong>단어들 사이의 관계</strong>를 살펴본다. </li>
<li>예컨대 코사인 유사도로 군집화해 보면 <strong>의미장별로 단어가 모인다</strong>거나, 문장 벡터 간 <strong>의미적 거리</strong>가 나타나는 식으로 <strong>학습된 언어공간의 구조</strong>를 파악할 수 있다.  </li>
<li><strong>어텐션 분석:</strong> PTM의 <strong>어텐션 가중치 행렬</strong>을 조사하여, <strong>특정 헤드가 어떤 패턴에 집중하는지</strong> 본다. </li>
<li>자주 발견되는 것은 <strong>대명사→명사</strong>, <strong>수식어→명사</strong>, <strong>구문 트리의 부모-자식 관계</strong> 등이다. 어텐션 행렬 시각화로 <strong>계층적 문법구조</strong>를 포착한 경우도 보고되었다.  </li>
<li><strong>생성 분석:</strong> PTM (특히 언어모델)의 <strong>문장 확률 할당</strong>을 이용해, <strong>문법적으로 맞는 문장 vs 틀린 문장</strong>의 확률 차이를 비교한다. </li>
<li>이를 통해 모델이 <strong>특정 문법 현상을 알고 있는지</strong> 간접 측정한다. 예: 단/복수 동사 일치가 틀린 문장을 낮은 확률로 예측하면, 그 제약을 안다고 추론.</li>
</ul>
<p>많은 연구가 이러한 기법으로 BERT 등의 지식을 분석했다. 주요 결과를 보면:  </p>
<ul>
<li>PTM은 <strong>형태소, 품사, 구문 범주, 의존구문 등 언어학적 특성을 상당히 잘 캡처</strong>하고 있다. </li>
<li>예를 들어 <strong>이전 RNN 기반 LSTM보다 BERT의 은닉표현이 구문 트리 구조를 더 잘 반영</strong>한다는 결과가 있다.  </li>
<li><strong>엘모, BERT 등의 층별 역할</strong>: 보통 <strong>하위층은 형태/통사 정보</strong>, <strong>상위층은 의미/추론 정보</strong>를 많이 담는 경향이 발견되었다.  </li>
<li><strong>Schijndel(2019)</strong>은 <strong>훈련 말뭉치 증가에 따른 언어모델 성능</strong>을 관찰하여, <strong>인간수준 문법 획득엔 비현실적으로 큰 데이터가 필요</strong>함을 지적했다. </li>
<li>즉 현 PTM도 <strong>완벽한 문법 지식</strong>엔 한계가 있다는 점.</li>
</ul>
<p><strong>(B) 세계 지식:</strong> </p>
<ul>
<li><p>PTM이 학습하는 <strong>상식 및 사실 지식</strong>도 관심대상이다.  </p>
</li>
<li><p><strong>Common sense (상식):</strong> </p>
</li>
<li><p><strong>Ettinger(2020)</strong>는 <strong>심리언어학적 테스트</strong> 문장을 BERT에 제시해 보았다. </p>
</li>
<li><p>그 결과 <strong>쉬운 상식 패턴</strong>(예: 범주 공유나 역할 역전)은 잘 처리하지만, <strong>복잡한 추론이나 문맥 상식</strong>에는 실패했다고 보고했다. </p>
</li>
<li><p>또 <strong>Davison(2019)</strong>은 <strong>“X is Y” 관계 문장을 마스킹해 PTM으로 상식 추출</strong>을 시도했는데, <strong>지도학습 없이도 기존 supervised 상식모델에 필적</strong>하는 성능을 보였다. </p>
</li>
<li><p>이는 PTM 속에 <strong>상당한 상식이 자발적으로 내재</strong>함을 시사한다. </p>
</li>
<li><p><strong>Da &amp; Kasai(2019)</strong>도 여러 probing 태스크로 <strong>PTM 임베딩 공간에 상식 feature가 표현</strong>됨을 확인했다. </p>
</li>
<li><p>하지만 <strong>Forbes(2019)</strong>는 PTM이 <strong>상식적 속성들 간 미묘한 관계</strong> (예: 휘발유-불꽃 -&gt; 위험) <strong>는 잘 모델링 못한다</strong>고 지적했다.</p>
</li>
<li><p>즉, <strong>개별 상식은 알지만 연결된 추론은 미흡</strong>하다는 것이다.</p>
</li>
<li><p>**Factual knowledge (사실/외부 지식):</p>
</li>
<li><p>** <strong>Petroni et al.(2019)</strong>는 <strong>LAMA</strong>라는 작업으로, 예를 들어 “[MASK]는 프랑스의 수도이다.” 같은 <strong>빈칸 문장을 채워 사실상식을 묻는</strong> 실험을 했다. </p>
</li>
<li><p>BERT 등 PTM은 <strong>일반 QA 시스템을 능가하는 정확도로 정답</strong>(“파리”)을 채워내어 큰 화제가 되었다. </p>
</li>
<li><p>이는 <strong>PTM이 대형 코퍼스에서 상당한 사실을 암기</strong>했음을 보였다. </p>
</li>
<li><p>그러나 이 방법은 <strong>질문 문장 phrasing에 민감</strong>하여, <strong>질문을 어떻게 쓰느냐에 따라 성능 편차</strong>가 컸다. </p>
</li>
<li><p>그래서 <strong>LPAQA (Jiang 2020)</strong>는 <strong>탐색과 패러프레이즈 기법으로 더 나은 질문 문장 (프롬프트)</strong>을 자동으로 찾아 성능을 높였다. </p>
</li>
<li><p><strong>AutoPrompt (Shin 2020)</strong>는 아예 <strong>그런 프롬프트를 구성하는 단어들을 그래디언트로 최적화</strong>하기도 했다. </p>
</li>
<li><p><strong>P-tuning (Liu 2021)</strong>은 아예 <strong>프롬프트를 연속 벡터(soft prompt)</strong>로 두고 학습하여, LAMA에서 <strong>정답정확성을 64%</strong>까지 끌어올렸다. </p>
</li>
<li><p>또한 <strong>Roberts(2020)</strong>는 <strong>PTM을 open-domain QA 데이터로 추가 파인튜닝</strong>하면 <strong>지식회상 정확도가 더 올라감</strong>을 보였다. </p>
</li>
<li><p>그러나 <strong>Pörner(2020)</strong>는 PTM의 지식응답이 <strong>편향적 패턴 학습</strong>일 수 있음을 지적했다. (예: “Mario”라는 이름을 물으면 이탈리아인으로 답하는 식 – 학습 데이터의 통계적 상식일 뿐 정확한 사실은 아닐 수 있다.)</p>
</li>
<li><p><strong>기타:</strong> </p>
</li>
<li><p><strong>수치 연산/개념</strong>에 대한 연구로, <strong>Wallace(2019)</strong>는 <strong>수 포함 문장 평가</strong>에서 ELMo (캐릭터 기반)가 BERT보다 <strong>숫자 개념 정확도</strong>가 높다고 보고했다. </p>
</li>
<li><p>BERT의 subword가 숫자 표현에 취약함을 지적한 것이다. <strong>Wang(2020)</strong>는 <strong>Transformer의 FFN 가중치 행렬을 분석</strong>하여, <strong>그 안에 특정 관계(동의어, 반의어 등)가 인코딩됨</strong>을 발견하고 이를 이용해 <strong>지식그래프 추출</strong>을 시도했다.</p>
</li>
</ul>
<p><strong>요약:</strong> </p>
<ul>
<li>PTM은 <strong>언어 자체에 대한 깊은 이해</strong>와 <strong>상당한 상식/사실 지식</strong>을 내부에 품고 있음을 다양한 방법으로 검증했다. </li>
<li><strong>물론 인간처럼 완벽하진 않고</strong> 편향/한계도 있지만, <strong>이러한 암묵 지식(modeledge)의 양은 상당</strong>하다. </li>
<li>이를 <strong>더 잘 끌어내어 활용하는</strong> 것이 prompt튜닝 등으로 발전 중이며 (섹션 8.1, 8.5 관련), 한편으로는 <strong>어떤 지식을 얼마나 배우는지 밝히는 연구</strong>도 지속될 것이다.</li>
</ul>
<h3 id="72-robustness-of-ptms-ptm의-강건성"><strong>7.2 Robustness of PTMs (PTM의 강건성)</strong></h3>
<p><strong>문제:</strong> </p>
<ul>
<li>PTM는 많은 경우 <strong>입력에 작은 교란이 가해져도 출력이 크게 흔들리는 “취약성”</strong>을 보인다. </li>
<li>특히 <strong>적대적 예제(adversarial example)</strong>, 즉 <strong>의미는 유지되나 약간 변형된 입력</strong>에 모델이 오답을 내는 현상이 보고되었다. </li>
<li>예: 문장의 <strong>단어 하나를 동의어로 바꾸기</strong>만 해도 분류가 뒤바뀌는 식이다. </li>
<li>BERT류도 예외가 아니어서, <strong>동의어 치환 공격</strong>에 쉽게 속는다는 연구들이 있다. </li>
<li>또한 <strong>무관한 “형식적” 단어 추가</strong> (예: “끝.” 같은 의미없는 단어 붙이기)로 답을 틀리게 유도할 수도 있다.</li>
</ul>
<p><strong>공격과 취약점 파악:</strong> </p>
<ul>
<li>현재 적대적 공격은 <strong>모델 출력 점수, 그래디언트</strong> 등을 이용해 자동 생성된다. </li>
<li>다만 <strong>자연스러운 공격문장</strong>을 생성하는 것이 어려워, <strong>사람이 관여하는 human-in-the-loop 방식</strong>도 쓰인다.</li>
<li>Wallace(2019)는 사람과 협력해 <strong>GPT-2를 속이는 문장</strong>들을 만들기도 했다. </li>
<li><strong>Nie(2020)</strong>는 사람으로 하여금 AI가 틀릴 질문을 만들게 하여, 기존 QA모델의 편향을 까발렸다. </li>
<li>이러한 <strong>강화된 적대적 예제들</strong>은 PTM들의 <strong>취약점을 더 분명히 드러냈다</strong>. </li>
<li>종합하면, <strong>PTM의 강건성 문제</strong>는 실서비스 시 <strong>보안 이슈</strong>로 떠오르고 있으며, <strong>해결이 시급한 열린 문제</strong>다.</li>
</ul>
<p><strong>대처:</strong> </p>
<ul>
<li>연구자들은 <strong>적대적 훈련(adv. training)</strong>, <strong>데이터 증강</strong> 등으로 대응을 시도한다. </li>
<li>예를 들어 <strong>알아차린 공격 패턴</strong>(예: “해리포터”-&gt;“해 리포터” 띄어쓰기 공격 등)을 <strong>훈련 데이터에 반영</strong>하여 견고성을 높인다. </li>
<li>섹션 8.1의 Reliability 부분에서도, <strong>적대적 방어 기법</strong>들이 소개된다. </li>
<li><strong>Li et al.(2020), Zhang et al.(2021)</strong> 등이 PTM에 대한 다양한 공격/방어를 연구했다. </li>
<li>전반적으로, <strong>PTM 신뢰성 향상</strong>은 <strong>모델을 실제 제품에 투입하기 위해 반드시 풀어야 할 과제</strong>로 인식되고 있다.</li>
</ul>
<h3 id="73-structural-sparsity-of-ptms-ptm의-구조적-희소성"><strong>7.3 Structural Sparsity of PTMs (PTM의 구조적 희소성)</strong></h3>
<p><strong>현상:</strong> </p>
<ul>
<li>BERT 이후 대부분 PTM은 <strong>Transformer 구조</strong>를 사용하며, 이들은 <strong>상당히 과다매개변수화</strong>되어 있음을 시사하는 연구가 많다. </li>
<li>예를 들어, <strong>동일 층 내 여러 어텐션 헤드들이 유사한 역할을 중복 수행</strong>하는 경우가 많다. </li>
<li><strong>Clark(2019)</strong>는 BERT의 많은 헤드들이 비슷한 attention 패턴을 학습한다고 밝혔고, <strong>Kovaleva(2019)</strong>는 <strong>BERT 각 헤드의 행동을 정성/정량 분석</strong>하여 <strong>몇 가지 유형으로 분류 가능</strong>함을 보였다. </li>
<li>즉, <strong>헤드마다 완전히 고유한 역할은 아니며 중복</strong>된다.</li>
<li>또, 앞서 <strong>프루닝</strong>에서 보았듯, <strong>70% 정도 헤드를 제거해도</strong> MT, 요약 등의 성능이 유지되었고 오히려 개선되기도 했다. </li>
<li><strong>가중치 가지치기</strong>에서도 <strong>30~40% prun</strong>에 성능 저하가 거의 없었다. </li>
<li><strong>Prasanna(2020)</strong>는 <strong>Lottery Ticket Hypothesis</strong> (초기 가중치 일부만 남겨도 최종성능 유지)도 BERT에 적용됨을 보였다. </li>
<li>한편 흥미롭게도, <strong>Kao(2020)</strong>는 BERT를 <strong>레이어 임베딩을 복제해 2배 깊게 만들어도</strong> fine-tuning 성능이 향상됨을 발견했다. </li>
<li>이는 <strong>남는 파라미터(여유용량)가 학습에 도움</strong>을 줄 수도 있음을 의미한다.</li>
</ul>
<p><strong>의미:</strong> </p>
<ul>
<li>이러한 결과들은 <strong>현재 PTM에 불필요하거나 교환 가능한 매개변수가 많다</strong>는 뜻이다. 이는 두 가지 해석으로 이어진다:  </li>
</ul>
<ol>
<li><strong>효율 개선 여지:</strong> 중요하지 않은 부분을 제거/공유하여 <strong>모델을 경량화</strong>할 수 있다 (이미 DistilBERT, ALBERT 등에서 실현).  </li>
<li><strong>성능 향상 잠재:</strong> 남는 용량을 <strong>더 고차원 패턴 학습</strong>에 활용하도록 <strong>새 제약/목표</strong>를 주면, <strong>학습 효율이나 결과</strong>를 높일 수 있다. (예: SpanBERT나 ERNIE가 마스크 방식 바꿔 같은 파라미터로 성능 향상). Kovaleva 등은 <strong>“모든 헤드들이 몇 패턴 반복이면, 추가 패턴 학습 여지가 있다”</strong>고 보기도 했다.</li>
</ol>
<p><strong>연구 방향:</strong> </p>
<ul>
<li>희소성 연구는 <strong>“얼마나 줄여도 되는가”</strong>와 <strong>“줄인 모델로 얼마까지 성능 낼 수 있는가”</strong>를 다룬다. </li>
<li>현재 <strong>Movement Pruning, Gradual Pruning</strong> 등으로 <strong>fine-tune 중 가지치기</strong> 최적화가 연구되고, <strong>동적 희소화</strong> (훈련 중 비효율 연결 제거) 같은 아이디어도 있다. </li>
<li>근본적으로는, <strong>PTM의 over-parameterization을 정량화하는 이론</strong>도 필요한데, 딥러닝 일반에서 난제이기 때문에 진행형이다.</li>
</ul>
<h3 id="74-theoretical-analysis-of-ptms-ptm의-이론적-분석"><strong>7.4 Theoretical Analysis of PTMs (PTM의 이론적 분석)</strong></h3>
<p><strong>현황:</strong> </p>
<ul>
<li>PTM의 성공을 <strong>이론으로 뒷받침</strong>하려는 시도들이 나타나고 있다. </li>
<li>이는 딥러닝 전반의 일반 문제이기도 하다.</li>
</ul>
<p><strong>기존 가설:</strong> </p>
<ul>
<li><strong>Erhan et al.(2010)</strong>는 초창기 전이학습(층별 사전학습)이 <strong>(1) 최적화 이점: 더 나은 초기화로 global minima에 가깝게 감, (2) 정규화 이점: train error는 비슷해도 test error가 낮아짐</strong> 두 효과를 제안했고, <strong>실험적으로 정규화 효과 쪽</strong>임을 보였다. </li>
<li>즉, 사전학습된 네트워크가 초기화인 경우 <strong>일반화 성능이 향상</strong>되며, 이는 <strong>라벨 없는 데이터로 일종의 regularization</strong>을 건 효과라는 것이다. </li>
<li>실제 PTM들도 <strong>같은 구조 랜덤초기화 모델 대비 test 성능이 우월</strong>하므로, <strong>“사전학습 = 우수한 규제”</strong> 가설은 여전히 유효하다.</li>
</ul>
<p><strong>대조학습 이론:</strong> </p>
<ul>
<li><strong>Saunshi et al.(2019)</strong>는 <strong>대조적 표현학습</strong>(언어모델 등 포함)을 수학적으로 해석하려 했다. </li>
<li>이들은 <strong>“잠재 클래스(latent class)”</strong> 개념을 도입했는데, 예컨대 모든 문장을 <strong>내재 의미 기준 여러 숨은 클래스</strong>로 나눈다고 가정한다. </li>
<li>언어모델에서는 <strong>컨텍스트+타겟 단어</strong>가 같은 latent class (같은 의미 맥락)에 속하고, 무작위 단어는 다른 class라고 볼 수 있다. </li>
<li>그러면 <strong>대조학습의 loss</strong> (유사한 pair는 가깝게, 무작위 pair는 멀게) 가 <strong>다운스트림 태스크 loss의 상한선 역할</strong>을 함을 증명했다. 이는 <strong>사전학습 loss가 줄면 downstream loss도 줄 것</strong>을 보이는 결과다. </li>
<li>즉, <strong>사전학습 목표 최적화가 곧 전이 성능 향상</strong>으로 이어진다는 일종의 보장이다. </li>
<li>물론 이건 이상적인 가정(모든 downstream 클래스가 latent class의 조합)에 기반하지만, <strong>pretext와 downstream의 연관을 이론화</strong>한 의미있는 첫걸음이다.</li>
</ul>
<p><strong>일반화 및 Robustness 이론:</strong> </p>
<ul>
<li>딥러닝 일반에서 <strong>고전 통계학으로는 딥네트의 generalization 설명이 힘듦</strong>이 잘 알려져 있다. </li>
<li>PTM에서도, <strong>“왜 이리 큰 모델이 과적합 안되고 잘 되는가”</strong>는 열린 문제다. </li>
<li><strong>Saunshi(2019)</strong>의 시도 외에는 아직 뚜렷한 이론이 없다. </li>
<li>특히 <strong>사전학습이 미세조정 일반화에 정확히 어떻게 기여하는지</strong> (데이터 효율, regularization) 등의 분석이 필요하다.</li>
<li>Robustness 측면에선, <strong>Schmidt(2018)</strong>가 <strong>적대적 강건성에는 훨씬 많은 샘플 수요</strong>를 보인 바 있는데, <strong>대형 PTM이 이를 완화할 수 있는가</strong>도 흥미로운 질문이다. </li>
<li>PTM를 <strong>“추가 데이터 공급원(extra data)으로 간주</strong>해 downstream robust 학습에 쓰면 효과가 있는지, 혹은 <strong>PTM 자체 robust하게 만드는 방법</strong>은 무엇인지 등이 연구될 것이다.</li>
</ul>
<p><strong>요약:</strong> </p>
<ul>
<li>이론 연구는 아직 초기지만, <strong>사전학습-파인튜닝의 성공을 수학적으로 이해하려는 움직임</strong>이 있다. </li>
<li>이는 <strong>PTM에 내재한 일반화, 불확실성, 강건성</strong>을 해명하여 <strong>더 신뢰할 수 있는 모델</strong> 개발에 도움을 줄 것이다. </li>
<li>특히 <strong>Bayesian 딥러닝</strong>의 발전으로 <strong>예측의 불확실성 추정</strong>이 가능해지고 있어 (예: <strong>확률적 PTM</strong>, <strong>Ensemble</strong> 등), <strong>PTM의 over-confidence 문제</strong>를 다루는 방향도 강조된다. </li>
<li>전반적으로, <strong>PTM에 대한 이론은 딥러닝 이론의 최전선 과제</strong>로서 앞으로 더 많은 진전이 기대된다.</li>
</ul>
<hr />
<h2 id="8-future-directions-향후-연구-방향"><strong>8. Future Directions (향후 연구 방향)</strong></h2>
<p><strong>섹션 목적:</strong> 지금까지 <strong>PTM의 과거와 현재</strong>를 다뤘다면, 이 섹션은 <strong>미래에 주목할 연구 주제와 열린 문제</strong>를 논한다.</p>
<ul>
<li>논문에서 제시한 <strong>7개 방향</strong>은 앞선 내용들과 대응되며, 각 방향에서 <strong>현재 한계와 도전과제</strong>를 짚는다.</li>
</ul>
<h3 id="81-architectures-and-pre-training-methods-아키텍처-및-사전학습-기법"><strong>8.1 Architectures and Pre-Training Methods (아키텍처 및 사전학습 기법)</strong></h3>
<p><strong>새로운 아키텍처 탐색:</strong> </p>
<ul>
<li><strong>Transformer가 효과적</strong>임은 입증되었지만, <strong>단점</strong>도 있다. </li>
<li><strong>복잡도 문제</strong>로 입력을 512 tokens 정도로 제한하는데, <strong>장문 맥락</strong> 처리엔 부족하다. </li>
<li>따라서 <strong>더 효율적인 모델 구조</strong>가 필요하며, 한편 <strong>자동 신경망 아키텍처 검색(NAS)</strong>도 복잡한 설계에 도움될 수 있다. </li>
<li>또한 <strong>모델 대형화 추세</strong>에서, 학습은 가능하더라도 <strong>추론시의 실용성</strong> 문제가 있다. </li>
<li><strong>저용량 디바이스나 실시간 응답 응용</strong>에서는 <strong>PTM 효율 개선</strong>이 필수이므로, <strong>미래 설계 시 경량화도 고려</strong>해야 한다. </li>
<li>더 나아가, <strong>다운스트림 작업마다 선호 구조</strong>가 조금씩 다르기에 (예: NLU엔 인코더, NLG엔 디코더가 적합), <strong>태스크 특화 PTM 구조</strong>도 검토할 부분이다.</li>
</ul>
<p><strong>새로운 사전학습 과제:</strong> </p>
<ul>
<li><strong>보다 범용적인 PTM</strong>을 만들려면 <strong>더 어려운 pretext task, 더 깊은 모델, 더 거대한 말뭉치</strong>가 필요해 보인다. </li>
<li>하지만 이는 <strong>막대한 비용</strong>을 수반하므로 현실적이지 않다. </li>
<li>따라서 <strong>주어진 자원 내에서 더 효율적인 자기지도 학습법</strong>이 연구되어야 한다. </li>
<li><strong>ELECTRA</strong>처럼 <strong>효율 높은 사전학습 목표</strong>는 한 예이며, 앞으로도 <strong>하드웨어/소프트웨어에 맞는 효과적인 pretext 설계</strong>가 중요하다. </li>
<li>또한 <strong>분산학습, 혼합정밀 등</strong> 기법을 잘 결합하여 <strong>훈련 효율</strong>을 극대화해야 한다. </li>
<li>궁극적으로는, <strong>적은 비용으로도 범용 언어지식을 터득하는 pretext</strong>를 찾는 것이 이상적일 것이다.</li>
</ul>
<p><strong>미세조정의 진화 (Beyond Fine-tuning):</strong> </p>
<ul>
<li>현재는 <strong>다운스트림마다 모델 전체를 fine-tune</strong>하는데, 이는 <strong>태스크 수만큼 모델 복사</strong>가 필요해 <strong>비효율적</strong>이다.</li>
<li><strong>미래 방향</strong>으로, <strong>PTM 본체는 고정</strong>해두고 <strong>작은 모듈만 추가 학습</strong>하여 여러 작업을 커버하려는 움직임이 있다. </li>
<li>예를 들어 <strong>Adapter</strong>를 각 태스크마다 몇 개 층만 붙여 학습하면, <strong>PTM 하나로 다태스크</strong>를 처리할 수 있다. </li>
<li>또 하나 큰 흐름은 <strong>Prompt Tuning (프롬프트 기반 모델 활용)</strong>이다. </li>
<li>이는 <strong>GPT-3가 few-shot으로 작업 수행</strong>을 보여준 후 각광받는데, <strong>프롬프트</strong>란 <strong>모델 입력에 특정 형식으로 태스크를 기술하는 텍스트</strong>이다. 이</li>
<li>를 <strong>사람이 설계하거나 (discrete prompt)</strong>, <strong>연속벡터로 학습하거나 (continuous prompt)</strong>, 또는 <strong>생성/탐색</strong>할 수도 있다. </li>
<li><strong>프롬프트를 잘 주면</strong> 모델이 <strong>별도 파인튜닝 없이</strong>도 그 작업을 수행하거나, 또는 <strong>아주 소량의 파라미터만 미세조정</strong>해서 성능을 끌어올릴 수 있다. </li>
<li>이러한 <strong>prompt tuning</strong>은 <strong>사전학습-다운스트림 간 갭을 줄여</strong> 더 나은 성능을 내고, <strong>거대 PTM 전체를 다시 학습하지 않아도 되어</strong> 효율적이다. </li>
<li>이미 <strong>GPT-3, T5</strong> 등에서 효과가 검증되었고, <strong>P-tuning v2</strong>처럼 아예 <strong>vision+text unified prompt</strong> 등 확장이 나오고 있다. </li>
<li><strong>결론적으로</strong>, 프롬프트 기반 방법은 <strong>PTM의 내재 지식</strong>(linguistic &amp; world knowledge)을 <strong>최소 비용으로 자극하여</strong> 활용하는 유망한 방향이다.</li>
</ul>
<p><strong>모델 신뢰성과 해석성:</strong> </p>
<ul>
<li>PTM가 강력해져 많이 쓰일수록, <strong>그 동작의 신뢰성(reliability)</strong>이 중요해진다. </li>
<li>특히 <strong>적대적 공격</strong> 연구는 <strong>PTM의 취약점</strong>을 드러내 주며, 이에 대응하는 <strong>방어 학습</strong>도 발전하고 있다. </li>
<li>Robust PTM를 만들려는 노력은 계속될 것이며, 더불어 <strong>PTM 내부를 투명하게 해석</strong>하려는 시도 (어텐션 시각화, 교란 감수성 맵, attribution 기법 등)도 지속될 것이다. </li>
<li><strong>궁극적으로 PTM의 작동원리를 잘 이해</strong>하게 되면, <strong>더 나은 사용법과 개선 방향</strong>을 찾는 데 큰 도움이 될 것이다.</li>
</ul>
<h3 id="82-multilingual-and-multimodal-pre-training-다국어-및-멀티모달-사전학습"><strong>8.2 Multilingual and Multimodal Pre-Training (다국어 및 멀티모달 사전학습)</strong></h3>
<p><strong>멀티모달 더 확장:</strong> </p>
<ul>
<li>지금까지 PTM 멀티모달은 <strong>주로 이미지+텍스트</strong>에 국한되었는데, <strong>비디오+텍스트, 오디오 등</strong> 모달도 포함하는 방향이 있다. </li>
<li><strong>비디오</strong>는 거대하고 시간축이 있어 어려운 도전이며, <strong>오디오</strong>(음성)도 시계열 특성이 있다. </li>
<li><strong>효율적 자기지도 학습</strong> 기법 (예: 특정 프레임만 샘플링, 변조 등)을 개발해 <strong>비디오-텍스트 사전학습</strong>을 현실화하는 것이 필요하다. </li>
<li>음성의 경우, 궁극적으론 <strong>&quot;음성→텍스트→음성&quot;</strong>까지 한 모델에서 다루는 걸 생각해볼 수 있다. </li>
<li>현재는 <strong>음성-텍스트-음성</strong> 변환에 3개 모듈 (ASR, 번역, TTS)이 필요한데, <strong>멀티모달+멀티링구얼 PTM</strong>으로 <strong>곧바로 음성간 번역</strong> 같은 것을 할 수 있지 않을까 전망한다. </li>
<li>이를 위해 <strong>새 프레임워크</strong>와 <strong>모듈 통합</strong> 연구가 필요할 것이다.</li>
</ul>
<p><strong>해석과 융합 이해:</strong> </p>
<ul>
<li>멀티모달 PTM의 성능 향상은 empirically 보여졌지만, <strong>왜 결합하면 좋은지에 대한 통찰</strong>은 부족하다. </li>
<li>혹시 <strong>한 모달을 배우는 데 다른 모달이 방해가 되진 않는지</strong> 등 부작용도 점검해야 한다. </li>
<li>예를 들어, <strong>멀티모달로 학습하면 각 모달 단독 성능은 저하?</strong> 여부 같은 것이다.</li>
<li>향후 <strong>딥러닝 시각화 툴</strong> 등을 활용해, <strong>모달간 상호작용을 분석</strong>하는 연구도 필요하다.</li>
</ul>
<p><strong>진짜 응용 발굴:</strong> </p>
<ul>
<li>멀티모달 사전학습은 V&amp;L 벤치마크에서 성과를 냈지만, <strong>현실 제품에서 활용은 제한적</strong>이다. </li>
<li>그 이유는 많은 경우 <strong>단일 모달 특화 시스템들이 워낙 강력</strong>하고, <strong>멀티모달 PTM는 비용이 커서</strong> 굳이 안 쓰게 되기 때문이다. </li>
<li>예컨대 OCR+NLP, 또는 간단한 데이터 증강 등으로 해결될 문제에 굳이 거대 멀티모달 모델 쓰지 않는다는 말이다. </li>
<li>그러므로 <strong>산업계와 협력해 멀티모달 PTM의 진정한 킬러앱을 발굴</strong>하는 것이 과제다. </li>
<li>예를 들어 <strong>자율주행</strong>에서 언어+비전 융합 추론이나, <strong>의료</strong>에서 영상+텍스트 종합분석 등 도전 영역이 있을 것이다.</li>
</ul>
<p><strong>다국어 적응력:</strong> </p>
<ul>
<li>현재 멀티링구얼 PTM는 <strong>학습 시 본 언어만 처리 가능</strong>하다. </li>
<li><strong>새로운 언어를 나중에 추가</strong>하려면 처음부터 다시 학습해야 한다. </li>
<li>향후엔 <strong>유연하게 언어를 확장</strong>할 수 있는 프레임워크 (모듈 추가 등) 연구가 필요하다. 또한, 전술했듯 <strong>음성 등 다른 모달과 언어 결합</strong> 이슈도 있다. </li>
<li>미래에는 <strong>예를 들어 영어 음성 → 중국어 자막</strong>을 한 PTM로 바로 생성하는 것을 상상할 수 있다. </li>
<li>이를 위해 <strong>텍스트와 음성을 모두 다루는 다국어 멀티모달 PTM</strong>이 필요하며, 이는 현재 기술로는 난도가 높지만 <strong>장기적 도전과제</strong>로 거론된다.</li>
</ul>
<h3 id="83-computational-efficiency-컴퓨팅-효율"><strong>8.3 Computational Efficiency (컴퓨팅 효율)</strong></h3>
<p><strong>추세:</strong> </p>
<ul>
<li>딥러닝 모델이 <strong>갈수록 복잡해지고 대형화</strong>되어 (예: BERT-large, GPT-3 등) 기존 프레임워크나 HW로 감당하기 어려워지고 있다. </li>
<li>따라서 <strong>효율화 요구</strong>는 계속 증가한다.</li>
</ul>
<p><strong>프레임워크 혁신:</strong> </p>
<ul>
<li>TensorFlow, PyTorch 등은 개발 시 지금같은 <strong>모델/파이프라인 병렬 요구를 예측 못했</strong>기에, 현재 <strong>대형 PTM 학습에 최적화되어 있지 않다</strong>. </li>
<li>앞으로 <strong>분산 학습을 더 잘 지원하는 새로운 프레임워크</strong>가 필요하다. </li>
<li>특히 <strong>장비간 데이터 이동</strong>(통신)이 병목이므로, 이를 <strong>자동 최적화</strong>하는 것이 중요하다. </li>
<li>이상적으로 <strong>병렬화 전략 (데이터/모델/파이프라인)을 모델/하드웨어 조건에 맞게 자동 결정</strong>해주는 시스템이 요구된다. </li>
<li>아직은 사용자가 구조와 통신 대역폭을 고려해 손으로 조합해야 하기에, <strong>병렬화 자동 스케줄링</strong> 연구 (예: FlexFlow)는 미래 방향이다.</li>
</ul>
<p><strong>대규모 훈련 환경:</strong> </p>
<ul>
<li>현재 메가모델 학습엔 <strong>Megatron-LM, DeepSpeed</strong> 등 특화프레임워크를 쓴다. </li>
<li>그러나 이들은 <strong>응용 제한적</strong>이고 상호 호환이 안된다. </li>
<li>궁극적으로는 <strong>범용 프레임워크가 자체적으로</strong> 모델 병렬, 파이프라인 병렬 등을 지원해야 한다. </li>
<li><strong>OneFlow, MindSpore</strong> 같은 새로운 시도들이 나오고 있고, <strong>Mesh-TensorFlow, GShard</strong> 등 플러그인도 있지만, 여전히 <strong>간편하지 않다</strong>. </li>
<li><strong>OneFlow</strong>는 SBP 개념으로 한 발 내디뎠지만, 완전 자동은 아니고 <strong>일부 수동 annotation</strong>이 필요하다. </li>
<li>미래에는 <strong>Sharding 주석을 부분적으로만 주면 나머지 알아서</strong> (GShard 스타일), 혹은 <strong>완전 자동</strong>으로 parallelism을 최적화하는 방향으로 갈 것이다. </li>
<li>이는 <strong>딥러닝 컴파일러/스케줄러 분야</strong>의 도전이며, 성과가 나오면 <strong>PTM 훈련 속도가 획기적</strong>으로 개선될 수 있다.</li>
</ul>
<p><strong>요약:</strong> </p>
<ul>
<li>컴퓨팅 효율은 <strong>끝없는 이슈</strong>다. <strong>모델 대형화 속도 &gt; HW 성능향상 속도</strong>인 현 상황에서, <strong>SW적으로 최대 효율을 짜내는</strong> 것이 필수다. </li>
<li><strong>데이터 이동 최적화, 병렬화 자동화</strong> 등은 앞으로도 심화 연구될 것이고, <strong>새 프레임워크나 전용 하드웨어(TPU vN, IPU 등)</strong>도 계속 나올 것이다. </li>
<li>이러한 기술혁신은 <strong>더 큰 PTM, 더 빠른 실험 사이클</strong>을 가능케 하여, PTM 연구의 가속도를 높일 전망이다.</li>
</ul>
<h3 id="84-theoretical-foundation-이론적-기초"><strong>8.4 Theoretical Foundation (이론적 기초)</strong></h3>
<p><strong>불확실성 (Uncertainty):</strong> </p>
<ul>
<li>딥러닝 모델은 <strong>자신의 모르는 영역도 확신 있게 답하는</strong> 경향이 있다 (과잉확신). </li>
<li>GPT-3 같은 거대 모델도 예를 들면 “내 발에는 눈이 몇 개?”라는 황당한 질문에 “두 개”라고 자신만만하게 답한다. </li>
<li>이러한 <strong>OOD(분포밖) 입력 처리</strong>는 미해결 과제로, <strong>AI 안전성</strong>에 직결된다.</li>
<li><strong>베이지안 접근</strong>이 한 해법으로 떠오른다. </li>
<li><strong>Bayesian Neural Network</strong>는 <strong>모델 파라미터나 출력에 분포</strong>를 할당하여, <strong>데이터/모델의 불확실성</strong>(aleatoric / epistemic)을 정량화한다. </li>
<li>최근 <strong>Bayesian Deep Learning</strong>의 이론/알고리즘/라이브러리가 발전하여, <strong>대형 모델에도 적용</strong>하려 시도 중이다. </li>
<li>PTM에 Bayesian 기법을 도입하면, <strong>예측에 대한 confidence</strong>를 추출하거나 <strong>아웃라이어 탐지</strong>를 할 수 있을 것이다. </li>
<li>다만 Bayesian 방법은 <strong>계산비용 증가</strong>를 야기하므로, 효율 개선과 함께 연구되어야 한다. </li>
</ul>
<p><strong>일반화와 강건성 이론:</strong> </p>
<ul>
<li>앞서 7.4 논의처럼, <strong>PTM의 일반화 메커니즘</strong>은 아직 퍼즐이다. </li>
<li><strong>Zhang et al.(2017)</strong>은 <strong>딥넷이 랜덤라벨까지도 과적합 가능</strong>함을 보여, 기존 VC차원 등 이론이 부적합함을 지적했다. </li>
<li>PTM에 대해서도, <strong>Transformer 구조 자체의 일반화</strong>(예: self-attention이 가진 inductive bias)와 <strong>사전학습이 일반화에 미치는 역할</strong>을 해명해야 한다. </li>
<li>Saunshi(2019)의 대조학습 이론은 한 출발점이나, <strong>더 현실가까운 가정 하에 분석</strong>이 필요하다. </li>
<li>또한 <strong>적대적 강건성 이론</strong>으로 <strong>Schmidt(2018)</strong>의 결과가 있으나, <strong>대형 PTM가 강건성에 끼치는 영향</strong>은 미지수다. </li>
<li>PTM가 일종의 <strong>“추가 데이터”</strong> 역할을 해서 작은 데이터셋의 robust 학습을 돕는지, 또는 PTM 자체를 robust하게 만드는 특별한 방법이 있는지 등이 연구될 만하다.</li>
</ul>
<p><strong>요약:</strong> </p>
<ul>
<li>이론적으로 PTM를 이해하는 것은 장기적 난제다. </li>
<li><strong>확률론, 통계학, 정보이론</strong> 등 도구를 총동원해도, 워낙 복잡한 현상이기에 부분적인 성과만 나오고 있다. </li>
<li>그러나 <strong>신뢰성 요구가 높아질수록</strong> 이 분야 중요성은 커질 것이다. </li>
<li><strong>Uncertainty estimation</strong>은 실제 시스템 안전장치로 유용하고, <strong>일반화에 대한 이해</strong>는 <strong>새 학습원리 발견</strong>으로 이어질 수 있다. </li>
<li>연구자들은 <strong>PTM를 단순화한 모델 (예: 선형화한 NN)</strong>로 분석하거나, <strong>가정된 데이터 분포</strong>하에서 결과를 내는 등 접근을 취하고 있다. </li>
<li>이런 축적이 언젠가 <strong>PTM의 작동원리</strong>를 수학적으로 기술할 수 있는 토대를 마련해줄 것으로 기대된다.</li>
</ul>
<h3 id="85-modeledge-learning-모델리지-학습"><strong>8.5 Modeledge Learning (“모델리지” 학습)</strong></h3>
<p><strong>개념 복습:</strong> </p>
<ul>
<li><em>Modeledge</em>는 저자들이 새로 명명한 용어로, <strong>PTM에 저장된 연속적인 지식 표현</strong>을 가리킨다. </li>
<li>이는 사람이 이해하는 <strong>이산(symbolic) 지식</strong>과 대비되는 개념이다. </li>
<li>사람 입장에선, <strong>PTM의 벡터가 무엇을 의미하는지 직접 해석하기 어려우므로</strong> 그것을 하나의 새로운 형태의 지식 (modeledge)으로 보자는 제안이다. </li>
</ul>
<p><strong>모델리지 활용 측면:</strong> </p>
<ul>
<li><strong>이미 PTM를 지식베이스로 간주</strong>하려는 시도가 여럿 있었고 (LAMA, 탄력적 지식추출 등), <strong>모델 내 상식/사실 지식을 외부 지식그래프로 변환</strong>하려는 연구도 있었다. </li>
<li><strong>Petroni(2019)</strong>는 PTM를 KB로 보고 <strong>triple 보완(knowledge completion)</strong>을 실험했고, <strong>Ethayarajh(2019)</strong>는 PTM embed 간 유사도로 <strong>자가 지도적 knowledge graph 구축</strong>을 시도했다. </li>
<li>이런 작업들은 PTM 안에 <strong>풍부한 인간지식이 잠재</strong>됨을 보여준다. 향후 <strong>modeledge를 어떻게 활성화(stimulate)하여 쓰느냐</strong>가 과제다. </li>
<li><strong>프롬프트 학습</strong>이나 <strong>모델 probing</strong> 등은 그 일환으로 볼 수 있다.</li>
</ul>
<p><strong>모델리지 저장/관리:</strong> </p>
<ul>
<li>현재는 각 PTM이 자기 파라미터 안에 지식을 담고 있는데, 모델마다 <strong>커버하는 지식이 다르고 중복</strong>된다. </li>
<li><strong>여러 PTM들의 modeledge를 합쳐 하나로 모을 수 없을까?</strong>라는 문제를 제기한다. </li>
<li>그래서 나온 아이디어가 <strong>UCKB (범용 연속 지식베이스)</strong>이다. </li>
<li><strong>Chen et al.(2020)</strong>이 이 개념을 처음 실험했는데, <strong>여러 서로 다른 PTM를 “지식증류” 기법으로 한 공용공간에 압축/병합</strong>하고, 필요 시 그로부터 다시 모델을 생성하는 방식을 탐색했다. 쉽게 말해 <strong>N개 PTM의 지식을 1개 UCKB로 합치고, 이 UCKB로부터 원하는 modeledge를 꺼내 task-specific 모델에 주입</strong>하는 것이다. </li>
<li>이를 통해 <strong>여러 모델을 개별 저장해야 하는 비효율</strong>을 해결하고, <strong>지식 융합으로 더 강한 모델</strong>을 만들 수 있다. </li>
<li>초기 결과는 지식증류로 어느정도 가능함을 보였으나, <strong>효과적인 UCKB 구조와 인터페이스 설계</strong>는 아직 어렵다고 한다. </li>
<li>앞으로 <strong>modeledge 전용 저장장치</strong> 개념이 발전할 수 있으며, 이는 <strong>기존 심볼릭 KB와는 다른 continuous한 KB</strong>로서 흥미로운 연구 주제다.</li>
</ul>
<h3 id="86-cognitive-and-knowledgeable-learning-인지-및-지식-기반-학습"><strong>8.6 Cognitive and Knowledgeable Learning (인지 및 지식 기반 학습)</strong></h3>
<p><strong>Knowledgeable PTM 발전:</strong> </p>
<ul>
<li><p><strong>PTM를 더 “지식 풍부”하게</strong> 만드는 접근 세 가지를 제시한다:</p>
</li>
<li><p><strong>Knowledge Augmentation:</strong> <strong>입력에 관련 지식을 확충</strong>하는 방법. </p>
</li>
<li><p>예를 들어 질문이 주어지면, <strong>외부 지식베이스를 찾아 관련 문장이나 triple을 입력에 덧붙여</strong> PTM에 넣는 것이다. </p>
</li>
<li><p>이미 <strong>open-domain QA</strong> 등에서 쓰이는 기법이다. 과제는, </p>
</li>
<li><p><strong>텍스트 vs 지식의 표현 형식 차이</strong>를 극복하는 것이다. </p>
</li>
<li><p><strong>심볼</strong>(기호) 기반 지식과 연속 벡터를 어떻게 통합할지, 그리고 PTM가 <strong>추가된 지식을 잘 반영하도록 pretraining 목표</strong>를 설계하는 것이 필요하다. </p>
</li>
<li><p>예를 들어 <strong>KEPLER</strong>는 KG 임베딩과 MLM을 공동학습했고, <strong>K-Adapter</strong>는 개체/관계판별 task로 어댑터를 학습해 BERT에 붙였다. </p>
</li>
<li><p>이 방향은 <strong>지식-언어 간 격차 해소</strong>가 핵심이다.</p>
</li>
<li><p><strong>Knowledge Support:</strong> </p>
</li>
<li><p>이는 <strong>모델 구조 측면에서 지식 활용</strong>이다. </p>
</li>
<li><p>현재 Transformer 등은 규칙적 동일 구조 층으로 되어 있는데, 만약 <strong>입력에 대한 사전 지식</strong>이 있다면 <strong>다른 처리 경로</strong>를 통해 효율을 높일 수 있다는 발상이다. </p>
</li>
<li><p>예를 들어 <strong>복잡한 수식이 포함된 문장은 수식 전용 모듈</strong>로 처리하고 나머지 텍스트와 합치는 식으로, <strong>입력특성별 서브네트워크</strong>를 두면 좋을 수 있다. </p>
</li>
<li><p>이는 <strong>모듈화</strong>, <strong>Mixture-of-Experts</strong> 아이디어와 일맥상통하며, 인간 뇌의 <strong>기능 영역 분화</strong>에 영감을 얻은 것이다. </p>
</li>
<li><p>앞으로 <strong>사전 지식을 이용해 모델 구조를 동적으로 선택하거나 구성</strong>하는 연구가 기대된다.</p>
</li>
<li><p><strong>Knowledge Supervision:</strong> </p>
</li>
<li><p><strong>사전학습 단계에서 지식 정보를 직접 학습신호로 사용</strong>하는 것이다. </p>
</li>
<li><p>예를 들어 <strong>텍스트와 지식그래프를 모두 입력으로</strong> 넣고 <strong>멀티태스크 학습</strong>을 하면, 모델이 두 소스 모두에서 배운다. </p>
</li>
<li><p>혹은 <strong>지식그래프의 삼중항을 문장처럼 학습</strong>시키거나, <strong>텍스트+지식 결합 태스크</strong> (예: 추론체인 완성) 등을 설정할 수 있다. </p>
</li>
<li><p>이렇게 <strong>대량의 구조화 데이터와 텍스트를 함께 사전학습</strong>하면, <strong>단순 텍스트만 학습한 PTM보다 더 깊은 언어이해/생성 능력</strong>이 기대된다. </p>
</li>
<li><p>이미 <strong>ERNIE (THU)</strong>, <strong>KnowBERT</strong> 등이 이런 방향을 시도했다. </p>
</li>
<li><p>목표는 <strong>PTM가 글을 넘어서 의미, 지식까지 파악</strong>하는 것으로, 성공시 다양한 응용에서 성능 향상이 가능하다.</p>
</li>
</ul>
<p><strong>Cognitive PTM 발전:</strong> </p>
<ul>
<li><p><strong>PTM를 더 “인지적으로 향상”</strong>시키기 위한 방향들도 제시한다:</p>
</li>
<li><p><strong>Cognitive Architecture:</strong> 인간 두뇌의 <strong>거시적 작동 원리</strong>에서 영감받은 새로운 아키텍처를 탐구하는 것이다. </p>
</li>
<li><p>예로 <strong>글로벌 워크스페이스 이론(GWT)</strong>은 의식과 무의식적 처리를 설명하는 인지 과학 이론인데, 이것을 모델화한 AI 구조를 생각해볼 수 있다. </p>
</li>
<li><p><strong>CogQA, CogLTX</strong> 같은 앞서 본 연구들이 시사점을 준다. </p>
</li>
<li><p>요컨대 <strong>Transformer 등 미시적 뉴런 모방</strong>에서 나아가, <strong>기억, 주의, 추론의 거시적 통합 메커니즘</strong>을 모방하는 새 PTM 설계가 도전과제로 남아 있다.</p>
</li>
<li><p><strong>Explicit and Controllable Reasoning:</strong> </p>
</li>
<li><p>딥러닝은 인식/패턴처리에는 강하지만, <strong>복잡한 의사결정이나 다단계 추론</strong>은 약하다. </p>
</li>
<li><p>미래 PTM는 <strong>스스로 사고 과정을 계획(예: 그래프 구성)하고, 명시적으로 단계별 추론</strong>할 수 있어야 한다. </p>
</li>
<li><p>이를 위해 <strong>logical reasoning 모듈</strong>을 통합하거나, <strong>추론 과정을 중간에 피드백하며 통제하는 기법</strong>이 필요하다. </p>
</li>
<li><p><strong>Inverse Prompting(2021)</strong>은 생성 결과를 중간에 평가해 주제를 통제하는 방식으로, 이런 <strong>제어된 생성</strong>의 한 예를 보여줬다.</p>
</li>
<li><p>앞으로 <strong>PTM가 알아서 reasoning chain을 형성하고 답을 도출</strong>하는 모습이 이상적이다.</p>
</li>
<li><p><strong>Interactions of Knowledge:</strong> PTM 내부를 <strong>뇌의 기능 영역</strong>에 비유하면, <strong>다른 기능 모듈들이 어떻게 협력하는지</strong> 궁금하다.</p>
</li>
<li><p>예를 들어 BERT의 각 레이어/헤드가 서로 다른 지식을 담고 있다면, 그것들이 <strong>상호작용하여 문제를 푸는 방식</strong>을 밝히고 싶다는 것이다. </p>
</li>
<li><p>이는 interpretability 문제와 이어지는데, <strong>점점 커지는 PTM 내부에도 어떤 부분은 어휘법칙을 처리, 어떤 부분은 문법, 어떤 부분은 상식</strong> 이런 식 분화가 있을 수 있다. </p>
</li>
<li><p>이를 <strong>탐구하여 시각화</strong>하면, <strong>PTM의 “내부 협업”</strong>을 이해할 수 있을 것이다. </p>
</li>
<li><p>이는 장차 <strong>PTM를 개선할 단서</strong>를 제공할 수 있다.</p>
</li>
</ul>
<h3 id="87-applications-응용-분야"><strong>8.7 Applications (응용 분야)</strong></h3>
<ul>
<li><p>PTM의 응용은 이미 <strong>다양한 AI 분야</strong>를 덮고 있다. </p>
</li>
<li><p>몇 가지 대표적인 영역과 과제를 짚으면:</p>
</li>
<li><p><strong>자연어 생성 (NLG):</strong> <strong>기계번역, 요약, 대화생성, 스토리생성, 시 생성</strong> 등 거의 모든 생성 태스크가 현재 <strong>GPT-2, BART, T5, UniLM</strong> 등의 PTM 주도로 연구되고 있다. </p>
</li>
<li><p>사실 번역은 Transformer (non-PTM)로 이미 혁신되었지만, <strong>Pre-trained T5 등의 등장으로 +상식/배경지식까지 활용하는 번역</strong>이 가능해졌다. </p>
</li>
<li><p><strong>요약</strong>도 BART 등으로 SOTA가 올라갔고, <strong>대화</strong>는 후술. <strong>장문 생성</strong>(스토리 등)에서도 GPT-2,3 등이 인상적 결과를 냈다. </p>
</li>
<li><p>또한 <strong>이미지→텍스트 생성(캡셔닝)</strong>, <strong>텍스트→이미지 생성(DALL-E)</strong> 등 <strong>멀티모달 생성</strong>에도 PTM가 쓰이고 있다.</p>
</li>
<li><p><strong>저자원 언어</strong> 생성도, 거대 PTM는 여러 언어를 학습해두었기에 <strong>few-shot 번역/요약</strong>이 가능해지는 추세다.</p>
</li>
<li><p>요약하면, <strong>PTM는 자연언어 생성의 질과 범위를 크게 확장</strong>하고 있다.</p>
</li>
<li><p><strong>대화 시스템:</strong> 최근 <strong>오픈도메인 챗봇</strong>들은 거의 다 <strong>초대규모 Transformer 기반</strong>이다. </p>
</li>
<li><p>구글의 <strong>Meena(2020)</strong>, Facebook의 <strong>Blender(2021)</strong>, 중국의 <strong>CDial-GPT, PLATO-2</strong> 등이 대표적이다. </p>
</li>
<li><p>이들은 수억~수십억 대화 데이터로 학습되었고, <strong>대부분 seq2seq 구조 (인코더=과거 대화, 디코더=응답)</strong>를 쓴다. </p>
</li>
<li><p><strong>상용 수준</strong>에 근접한 응답 자연스러움을 보이는 등 진전을 이뤘다. </p>
</li>
<li><p>하지만 <strong>대화 특화 사전학습 태스크</strong>는 아직 명확치 않다.(Blender 등은 그냥 일반 LM으로 학습 후, persona나 context tune을 추가로 했다.) </p>
</li>
<li><p><strong>향후 대화에 특화된 pre-training</strong> (예: 대화 대본 예측, 발화 행위 분류 등)을 탐색하는 것이 과제다. </p>
</li>
<li><p>또한 <strong>대화의 일관성, 사실성</strong> 문제 등은 남아있어, <strong>상식 장착</strong>과 <strong>윤리/안전 장치</strong> 등도 연구될 것이다.</p>
</li>
<li><p><strong>도메인 특화 PTM:</strong> 특정 분야에 <strong>대량의 전문 텍스트</strong>가 있다면, <strong>전용 PTM</strong>을 훈련하는 것이 효과적이다. </p>
</li>
<li><p><strong>BioBERT (2020)</strong>는 생의학 논문/논문 초록으로 추가 pretraining하여, 일반 BERT보다 <strong>의학 개념 이해, 용어 소인식</strong>이 뛰어났다. </p>
</li>
<li><p><strong>SciBERT (2019)</strong>도 과학 논문으로 학습되어, <strong>과학 QA 등</strong>에서 좋은 성능을 냈다. </p>
</li>
<li><p>이런 <strong>전문 PTM</strong>들은 해당 <strong>분야 지식과 어휘 사용</strong>을 더 잘 반영하여, 많은 <strong>도메인 과제</strong> (예: EHR 분석, 특허 분류 등)에 강점이 있다. </p>
</li>
<li><p><strong>도메인/태스크 적응:</strong> </p>
</li>
<li><p>한편, 거대 일반 PTM를 <strong>소량의 도메인 데이터</strong>로 fine-tuning만 하는 것은 충분하지 않을 때가 있다. </p>
</li>
<li><p><strong>Gururangan(2020)</strong> 등은 <strong>도메인 보정(pretraining)</strong> 단계를 거치면 성능 향상을 보고했다. </p>
</li>
<li><p>이는 <strong>일반 말뭉치→도메인 말뭉치→태스크 데이터</strong> 순으로 학습하는 식이다. </p>
</li>
<li><p><strong>분포 차이</strong>(예: 뉴스 vs 의학논문)가 크면, <strong>domain-adaptive pretraining</strong>으로 갭을 줄여야 한다는 것이다. </p>
</li>
<li><p>또한 <strong>태스크 적응</strong>도 문제인데, <strong>대부분 PTM fine-tune은 작은 라벨셋에 대해 거대한 파라미터를 다 업데이트</strong>하므로 <strong>비효율/비안정</strong>일 수 있다. </p>
</li>
<li><p><strong>few-shot 세팅</strong>에선 대형모델이 과적합하거나 학습이 불안정해지기도 한다. </p>
</li>
<li><p>그래서 <strong>프롬프트 러닝, Adapters</strong> 등이 대안으로 나온 것이다. </p>
</li>
<li><p><strong>Soares(2019)</strong>, <strong>Ding(2021)</strong> 등은 <strong>관계추출</strong> 등 작은 태스크에 최적화된 <strong>효율 fine-tune 전략</strong>을 모색했다. </p>
</li>
<li><p>미래에는 <strong>fine-tuning 자체를 고도화</strong>하여 <strong>적은 라벨로도 큰 PTM을 효과적으로 활용</strong>할 방법들이 더욱 연구될 것이다.</p>
</li>
<li><p><strong>그 외 영역:</strong> PTM는 본래 NLP용이지만, <strong>프로그래밍 언어 (코드) 모델링</strong>에도 쓰이며 <strong>AlphaCode, Codex</strong> 등 결과를 냈다. </p>
</li>
<li><p><strong>Recommendation</strong> 분야도 대량 시퀀스 처리에 Transformer 사용이 늘고, <strong>Vision</strong> 분야에서는 ViT 같은 PTM 등장으로 <strong>이미지 특화 PTM</strong> 시대가 열렸다. </p>
</li>
<li><p>또한 <strong>강화학습</strong>에서도 텍스트 생성 PTM (예: 인공지능 던전)이나 정책 사전학습 등에 활용 논의가 있다. </p>
</li>
<li><p>따라서 응용은 <strong>언어외 영역</strong>으로도 확장 중이다.</p>
</li>
</ul>
<p><strong>요약:</strong> </p>
<ul>
<li>응용 측면에서, <strong>PTM의 영향력은 자연어 처리 전역으로 퍼졌다</strong>. </li>
<li>이해부터 생성, 대화, 멀티모달까지, PTM 없는 연구를 찾기 어려울 지경이다. </li>
<li>앞으로 <strong>더 많은 산업/실생활 문제</strong>를 PTM로 풀려는 시도가 있을 것이며, <strong>전문분야나 멀티모달, 복합 task</strong>에 PTM를 맞춤화하는 일도 진행될 것이다. </li>
<li>중요한 건 <strong>도메인 적응 기법</strong>과 <strong>소수 데이터 활용</strong> 방법으로, 이는 <strong>PTM 기술의 민주화</strong>와 연결된다. </li>
<li>거대한 PTM를 소수 리소스 환경에서도 활용 가능하게 만드는 것은 미래 과제지만, prompt 튜닝 등은 그 희망을 보여주고 있다.</li>
</ul>
<hr />
<h2 id="9-conclusion-결론"><strong>9. Conclusion (결론)</strong></h2>
<ul>
<li>이 논문에서는 <strong>사전학습 모델(PTM)의 발전사</strong>와 <strong>최신 연구 동향</strong>을 폭넓게 다뤘다. </li>
<li><strong>역사적 맥락</strong>에서 보면, PTM는 <strong>전이학습/자기지도학습의 흐름 속에 등장</strong>하여 현재 AI 패러다임을 바꾸어놓은 핵심 기술로 부상했다. </li>
<li><strong>최근 2-3년간</strong> 수많은 연구자들의 노력으로, <strong>효과적인 아키텍처 설계, 풍부한 컨텍스트 활용, 계산 효율 개선, 이론적 통찰</strong> 등 여러 측면에서 PTM가 향상되어왔다. </li>
<li>그 결과 <strong>거대 PTM들은 zero-shot, few-shot 학습에서 인간 비슷한 능력</strong>을 보이며, <strong>“프롬프트 몇 개로 새로운 과제를 해결”</strong>하는 등 <strong>기존 머신러닝 상식을 뒤집는 장면</strong>도 연출하고 있다. </li>
<li>하지만 <strong>PTM의 미래 방향은 여전히 열린 문제</strong>다. </li>
<li><strong>인간은 지식을 기호화(discrete)하여 저장</strong>하지만 <strong>PTM는 벡터로 암묵 저장</strong>한다는 근본 차이가 있으며, 이 <strong>“연속 지식 (modeledge)”</strong>를 어떻게 하면 더 효과적으로 저장하고 활용할지에 대한 연구가 필요하다. </li>
<li>또한 <strong>PTM의 해석성과 효율성, 신뢰성</strong>을 높여야 <strong>광범위한 영역에서 안심하고 사용할 수 있는 AI</strong>가 될 것이다.</li>
</ul>
<hr />
<p><strong>맺음말:</strong> </p>
<ul>
<li>저자들은 이 논문이 <strong>PTM 연구의 흐름을 정리하고 미래를 조망</strong>함으로써, 이후 연구에 영감을 주기를 희망한다. </li>
<li><strong>사전학습 모델</strong>은 불과 몇 년만에 AI의 지형을 바꿔놓았고, 앞으로도 <strong>더 발전할 잠재성</strong>이 크다. </li>
<li><strong>모델 자체의 더 똑똑한 설계, 지식와 추론의 통합, 학습 비용 절감, 이론 기반 이해</strong> 등이 두루 진전된다면, <strong>PTM는 진정 인간 수준의 언어 능력</strong> (더 나아가 인지 능력)을 갖춘 <strong>만능 AI 엔진</strong>으로 나아갈 수 있을 것이다. </li>
<li>지금까지의 연구 축적과 공동체의 노력은 이미 그 방향으로 성큼 가고 있으며, 이 논문도 그 길에 작은 이정표가 되고자 한다.</li>
</ul>