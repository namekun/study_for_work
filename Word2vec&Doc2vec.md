---


---

<h1 id="word-embedding">Word Embedding</h1>
<ul>
<li>단어를 밀집 벡터(dense vector)의 형태로 표현하는 방법</li>
<li>이 밀집 벡터를 워드 임베딩 과정을 통해 나온 결과라고 하여 임베딩 벡터(embedding vector)라고 한다.</li>
</ul>
<h1 id="word2vec">Word2Vec</h1>
<p>word2vec은 단어들을 벡터 값으로 표기하는데 있어 단어의 의미와 맥락을 고려하여 단어를 벡터로 표현하는 단어 수치화(word embedding)를 위한 텍스트 처리 방식이다.</p>
<p>word2vec 모델에서의 두 가지 중요한 알고리즘<br>
<img src="https://roboreport.co.kr/wp/wp-content/uploads/2019/03/word2vec-1.png" alt="CBOW와 Skip-gram"></p>
<ul>
<li>CBOW(문장내에서 단순하게 단어를 카운트하는 방식)
<ul>
<li>주변의 단어들로 가운데 있는 단어를 유추할 수 있다.</li>
</ul>
</li>
<li>Skip-gram(앞뒤 문맥을 살피는 방식)
<ul>
<li>가운데 있는 단어로 주변 단어를 유추한다.</li>
</ul>
</li>
</ul>
<h1 id="doc2vec">Doc2vec</h1>
<ul>
<li>뉴스 기사 본문과 같은 큰 텍스트 블록에 대해서 vector값으로 변환시키는 것을 말한다.</li>
<li>즉 paragraph id(document id)를 하나의 단어(paragraph token)처럼 사용해서 문서를 훈련 데이터로 사용하는 방법이다.</li>
<li>word2vec와 같이 두개의 중요한 알고리즘이 있다.<br>
<img src="https://roboreport.co.kr/wp/wp-content/uploads/2019/03/doc2vec_%EC%A2%85%EB%A5%98.png" alt="">
<ul>
<li>PV-DM(Distributed memory)
<ul>
<li>paragraph vector 와 앞의 단어들을 사용해서 다음에 나오는 단어를 유추합니다. window라는 정해진 사이즈의 단어들을 문맥정보(context)로 사용하며 맨 앞에서부터 한 단어씩 옆으로 이동하면서 훈련 데이터로 사용합니다.</li>
<li>같은 패러그래프에서 생성된 훈련 데이터에서는 하나의 paragraph vector로 공유되기에, paragraph vector는 훈련시 문서의 주제를 잡아주는 memory 같은 역할을 합니다. 그래서 이 알고리즘의 이름 자체가 분산회된 메모리를 가진 패러그래프 백터로 지어졌습니다.</li>
</ul>
</li>
<li>PV-DBOW(Distributed Bag of Words)
<ul>
<li>위 방식에서 나오는 context 단어들을 사용하지 않고 paragraph id 만 가지고 이 패러그래프에서 나오는 단어를 랜덤하게 예측하는 방식을 사용합니다. input은 패러그래프 벡터이고 output은 패러그래프에서 random하게 뽑인 단어들입니다.</li>
</ul>
</li>
</ul>
</li>
</ul>
<h2 id="출처">출처</h2>
<p><a href="%5Bhttps://lovablebaby1015.wordpress.com/2018/08/07/word2vec-%EA%B0%9C%EB%85%90%EC%A0%95%EB%A6%AC-8-7-%EB%AF%B8%EC%99%84%EC%84%B1/%5D(https://lovablebaby1015.wordpress.com/2018/08/07/word2vec-%EA%B0%9C%EB%85%90%EC%A0%95%EB%A6%AC-8-7-%EB%AF%B8%EC%99%84%EC%84%B1/)">Word2Vec 개념정리</a></p>
<p><a href="%5Bhttps://roboreport.co.kr/doc2vec-%ED%9B%88%EB%A0%A8-%ED%8C%8C%EB%9D%BC%EB%AF%B8%ED%84%B0-%EC%84%A4%EB%AA%85/%5D(https://roboreport.co.kr/doc2vec-%ED%9B%88%EB%A0%A8-%ED%8C%8C%EB%9D%BC%EB%AF%B8%ED%84%B0-%EC%84%A4%EB%AA%85/)">doc2vec 훈련 파라미터 설명</a></p>
<p><a href="%5Bhttps://lovit.github.io/nlp/representation/2018/03/26/word_doc_embedding/%5D(https://lovit.github.io/nlp/representation/2018/03/26/word_doc_embedding/)">Word / Document embedding (Word2Vec / Doc2Vec)</a></p>

