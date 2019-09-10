# WordEmbedding, Word2vec, fastText

## 희소 표현(Sparse representation)

희소표현은 벡터 또는 행렬의 값이 대부분 0으로 표현되는 방법이다. 예를 들자면, 원-핫 인코딩을 통해서 나온 원-핫 벡터들은, 표현하고자 하는 단어의 인덱스 값만 1이고, 나머지 인덱스에는 전부 0으로 표현되는 벡터 표현 방법이기에 희소표현이라고 할 수 있다.

#### 단점

- 단어의 크기만큼, 벡터 열의 크기 역시 커져야하기에, 공간적 낭비가 발생한다.
- 원-핫 벡터에서 각 단어의 내적(inner product)은 0, 즉 직교하므로 각 단어사이에 어떠한 연관성도 찾아낼 수 없다.



## 밀집 표현(Dense representation)

위의 희소표현과는 반대의 표현으로, 벡터의 차원을 단어 집합의 크기로 상정하지 않는다.

사용자가 설정한 값으로 모든 단어의 벡터 표현의 차원을 맞추고, 이 과정에서 더 이상 0과 1만 가진 값이 아니라, 실수 값을 갖게 된다.

이 경우 벡터의 차원이 조밀해졌다고 하여, **밀집 벡터**(dense vector)라고 한다.



## Word Embedding

- 사람의 언어를 컴퓨터가 이해할 수 있도록 바꿔준다는 것이다.
- 단어를 **밀집 벡터**(dense vector)의 형태로 표현하는 방법
- 이 **밀집 벡터**를 워드 임베딩 과정을 통해 나온 결과라고 하여 **임베딩 벡터**(embedding vector)라고 한다.



## 정리된 표

| -         | 원-핫 벡터               | 임베딩 벡터              |
| :-------- | :----------------------- | :----------------------- |
| 차원      | 고차원(단어 집합의 크기) | 저차원                   |
| 다른 표현 | 희소 벡터의 일종         | 밀집 벡터의 일종         |
| 표현 방법 | 수동                     | 훈련 데이터로부터 학습함 |
| 값의 타입 | 1과 0                    | 실수                     |



## 국소표현 (Local representation)

국소 표현은 해당 단어 그 자체만 보고, 특정값을 mapping하여 단어를 표현하는 방법.

- **one-hot encoding** : Text를 숫자로 바꿔주지만, 단어간의 유사도를 측정하기 힘들다.
- **TF-IDF** : 단어가 문서에 (n번) 존재함을 기준으로 중요도를 구하고, 단어 중요도의 가중합을 구함(순서를 고려하지 않는 bag of words 방식)
  - Bag of Words : 단어들의 순서는 전혀 고려하지 않고, 단어들의 출현 빈도에만 집중하는 텍스트 데이터 수치화 표현 방법
  - TF(단어 빈도, term frequency)는 특정한 단어가 **문서 내에 얼마나 자주 등장하는지를 나타내는 값**. 이 값이 **높을수록 문서에서 중요**하다고 생각할 수 있다.하지만 하나의 문서에서 많이 나오지 않고 **다른 문서에서 자주 등장하면 단어의 중요도는 낮아진다**.
  - DF(문서 빈도, document frequency)라고 하며, 이 값의 역수를 IDF(역문서 빈도, inverse document frequency)라고 한다.
  - IDF는 전체 문서 갯수를 해당 엔티티가 포함된 문서의 갯수로 나누는 것이다.
  - TF-IDF는 TF와 IDF를 곱한 값으로 점수가 높은 단어일수록 **다른 문서에는 많지 않고 해당 문서에서 자주 등장하는 단어를 의미한다.**
- sparse, long vectors등



## 분산표현(Distributed representation)

분산 표현은 기본적으로 **분포 가설**(distributional hypothesis)이라는 가정 하에 만들어진 표현 방법.

여기서 분포 가설은 '**비슷한 위치에서 등장하는 단어들은 비슷한 의미를 갖는다**' 라는 가정이다.

- word2vec
- fastText
- glove
- dense, short vectors등

![](https://inspiringpeople.github.io/assets/img/local_distributed.png)



# Word2Vec

**Distributional Hypothesis(분포가설)**

- 두 단어의 문맥(주변 단어들)/분포도가 비슷하면 “**의미적**”으로 유사한 단어
- 비슷한 위치에서 등장하는 단어들은 비슷한 의미를 갖는다
- 예) 집 앞 편의점에서 아이스크림을 사 먹었는데, ___ 시려서 너무 먹기가 힘들었다.

**word2vec**

- word2vec은 단어들을 벡터 값으로 표기하는데 있어 분포 가설 기반으로 단어의 의미와 맥락을 고려하여 단어를 벡터로 표현하는 단어 수치화(word embedding)를 위한 텍스트 처리 방식이다.
- 주변단어(window) Size에 따라 말뭉치를 슬라이딩하면서 중심단어별의 주변단어들을 보고 각 단어의 벡터값을 업데이트 해나가는 방식으로 훈련
- window 내에 등장하지 않는 단어에 해당하는 벡터는 중심단어 벡터와 벡터공간상에서 멀어지게끔(내적값 줄이기), 등장하는 주변단어 벡터는 중심단어 벡터와 가까워지게끔(내적값 키우기) 값을 변경해 나감



## word2vec에서의 두 가지 중요한 알고리즘

![img](https://deeplearning4j.org/images/guide/word2vec_diagrams.png)

- CBOW(문장내에서 단순하게 단어를 카운트하는 방식)
  - 주변의 단어들로 중심 단어를 유추할 수 있다.
  - ex) **나는** ___ **에 간다**.
  - 이렇게 주변 단어를 통해 빈칸에 들어갈 단어를 유추해 내는 것이 바로 CBOW
- Skip-gram(앞뒤 문맥을 살피는 방식)
  - 중심 단어로 주변 단어를 유추하기 위해 단어벡터들을 조금씩 업데이트하면서 학습이 이뤄지는 구조
  - ex ) ___ 외나무 다리 ___
  - 학습시킨 말뭉치에서 만약 '외나무 다리'라는 단어 뒤에 '에서', '만난다'가 있었다면, word2vec은 이 단어들과 어떤 연관성이 있다고 파악하고, 이를 감안해서 벡터를 만든다.



## word2vec의 입력과 Skip-Gram

word2vec의 Skip-gram이 말 뭉치로부터 어떻게 입력값과 정답을 만들어내는지 보자.

`The quick brown fox jumps over the lazy dog`

라는 문장이 있다고 치자. window(한번에 학습할 단어 개수)의 크기가 2인 경우, 아키텍쳐가 받는 입력과 정답은 다음과 같다.

![](http://i.imgur.com/8zNRwsn.png)

위와 같은 방식으로 말뭉치내에 존재하는 모든 단어를 윈도우 크기로 슬라이딩 해가면서 학습을 하면 iteration 1회분이 완료가 된다.

 여기서 iteration은 다음 그림을 보고 이해하도록 하자

![](http://postfiles11.naver.net/MjAxOTAxMjNfMjU4/MDAxNTQ4MjM1Nzg3NTA2.UtvnGsckZhLHOPPOBWH841IWsZFzNcgwZvYKi2nxImEg.CdtqIxOjWeBo4eNBD2pXu5uwYGa3ZVUr8WZvtldArtYg.PNG.qbxlvnf11/20190123_182720.png?type=w773)



## word2vec 코드보고 이해하기

- word2vec을 사용하기 위해서는 다음과 같은 코드를 사용하면 된다.



파일 경로 및 파일 로드, 그리고 문장의 벡터화

```java
String filePath = new File(DataPath).getAbsolutePath();

// 문자열(String)을 반환하는 데이터 셋의 데이터
SentenceIterator iter = new BasicLineIterator(filePath);
// 텍스트의 토큰화에 사용된다. TokenizerFactory는 문장 하나를 위한 tokenizer의 인스턴스를 생성한다.
TokenizerFactory t = new DefaultTokenizerFactory();
/*
 CommonPreprocessor 는 각 토큰에 다음과 같은 정규표현식을 적용한다: [\d\:,"'\(\)\[\]|/?!;]+
그래서 사실상 모든 숫자, 문장 부호, 그리고 몇몇 특별한 기호는 제거된다.
또한 모든 토큰에 대해 대문자였던 것들은 소문자로 변경한다
*/
t.setTokenPreProcessor(new CommonPreprocessor());
```

word2vec모델 build, 그리고 학습

```java
log.info("build model");
org.deeplearning4j.models.word2vec.Word2Vec vec = new org.deeplearning4j.models.word2vec.Word2Vec.Builder()
.minWordFrequency(5) // 말뭉치(corpus)에서 나와야하는 단어의 최소빈도
.iterations(1)       // 몇개의 batch를 사용할 것인가?, batch = 한번에 처리하는 데이터의 수
.epochs(10)          // 전체 데이터 셋에 대한 학습을 몇번 시킬 것인가?
.layerSize(100)      // 단어 벡터의 차원.
.seed(42)            // 난수 알고리즘을 위해서 쓰는 수
.windowSize(5)       // window size = 주변 단위의 앞과 뒤에서 몇단어까지 볼 것인가?
.iterate(iter)       // 데이터의 여러 배치(batch, 데이터를 쪼갠 단위)중 어떤 배치에서 현재 학습할 것인지?
.tokenizerFactory(t)
.build();

// 학습 시작
vec.fit();
```

모델 재사용을 위한 저장

```java
String modelPath = "modelpath";
WordVectorSerializer.writeWord2VecModel(vec, modelPath);
```



## word2vec의 한계

- 단어의 형태학적 특성을 반영하지 못한다
  - 예를 들어, teach, teacher, teachers 이 3가지 단어는 의미적으로 유사한 단어임이 분명하다. 그런데 과거의 word2vec이나, glove등과 같은 방법은 이러한 단어들을 개별적으로 임베딩하기 때문에, 위 3단어의 벡터가 유사하게 구성되지 않는다.
- 희소한 단어를 임베딩하기 힘들다.
  - word2vec등과 같은 기존의 방법은 Distribution hypothesis를 기반으로 학습하는 것이기에, 출현횟수가 많은 단어에 대해서는 잘 임베딩되지만, 출현 횟수가 적은 단어에 대해서는 제대로 임베딩이 되지않는다.
- Vocabulary외의 단어에 대해 처리할 수 없는 점
  - word2vec은 단어단위로 vocabulary를 구성하기에, 어떤 단어가 없다면, 데이터를 다시 전체학습시켜야만한다.



# FastText

**Facebook에서 발표한 word Embedding기법으로, Word2vec과 비교해서 다음과 같은 차별점이 있다.**

- 단어 임베딩에는 다양한 방법이 있지만, 대부분의 방법들은 언어의 형태학적(Morpological)인 특성을 반영하지 못하고, 또 희소한 단어에 대해서는 임베딩이 되지않음.
- fastText에서는 단어를 Bag-of-Characters로 보고, 개별단어가 아닌 n-gram의 Characters를 임베딩함(skip-gram모델 사용)
- 최종적으로 각 단어는 임베딩된 n-gram의 합으로 표현된다. 그러기에 더 빠르고 좋은 성능을 나타낸다.



## fastText4j

출처 : https://github.com/mayabot/fastText4j

여기서는 java를 위해 포팅된 api인 fastText4j를 사용하였기에 이에대해 설명하도록 한다.

#### 특징

- 자바(코틀린)으로 구현
- 잘 설계된 API
- C++ 모델 파일과 호환 가능
- 훈련된 모델 제공
- 자바 파일 포맷 지원(mmap을 사용하여 파일 read 가능), 적은 메모리로 큰 모델파일 읽기 가능
  - mmap - memory mapping



## how to use fastText4j?

#### Maven

```xml
<dependency>
  <groupId>com.mayabot</groupId>
  <artifactId>fastText4j</artifactId>
  <version>1.2.2</version>
</dependency>
```

### Train model

Train model에는 3가지 모델을 지원한다.

- Supervised - `ModelName.sup`
- Skip-gram - `ModelName.sg`
- Cbow - `ModelName.cow`

코드에서의 사용은 다음과 같다

```java
// word representation learning
FastText fastText = FastText.train(new File("data.txt"), ModelName.sg);

// Text classification
FastText fastText = FastText.train(new File("data.txt"), ModelName.sup);
```

data.txt는 또한 utf-8로 인코딩되며 각 선마다 하나의 샘플로 인코딩된다. 그리고 단어 분할도 미리 해놓아야 한다.



### Parameters of TrainArgs

훈련 파라미터 설정 메서드들은 다음과 같다.

```java
TrainArgs trainArgs = new TrainArgs();
trainArgs.setWs();
trainArgs.setEpoch();
trainArgs.setDim();
trainArgs.setLoss();
trainArgs.setLr();
trainArgs.setLrUpdateRate();
trainArgs.setNeg();
trainArgs.setPretrainedVectors();
trainArgs.setThread();
```

파라미터 내용은 다음과 같다. ( -파라미터  설명 [default Setting] )

```plain text
The following arguments for the dictionary are optional:
  -minCount           minimal number of word occurences [1]
  -minCountLabel      minimal number of label occurences [0]
  -wordNgrams         max length of word ngram [1]
  -bucket             number of buckets [2000000]
  -minn               min length of char ngram [0]
  -maxn               max length of char ngram [0]
  -t                  sampling threshold [0.0001]
  -label              labels prefix [__label__]

The following arguments for training are optional:
  -lr                 learning rate [0.1]
  -lrUpdateRate       change the rate of updates for the learning rate [100]
  -dim                size of word vectors [100]
  -ws                 size of the context window [5]
  -epoch              number of epochs [5]
  -neg                number of negatives sampled [5]
  -loss               loss function {ns, hs, softmax} [softmax]
  -thread             number of threads [12]
  -pretrainedVectors  pretrained word vectors for supervised learning []
  -saveOutput         whether output params should be saved [0]

The following arguments for quantization are optional:
  -cutoff             number of words and ngrams to retain [0]
  -retrain            finetune embeddings if a cutoff is applied [0]
  -qnorm              quantizing the norm separately [0]
  -qout               quantizing the classifier [0]
  -dsub               size of each sub-vector [2]
```



### save model

모델을 저장하는 방법은 다음과 같다

```java
fastText.saveModel("path/data.model");
```



### Load model

모델을 읽어 오는 방법은 다음과 같다.

```java
//load from java format 
FastText fastText = FastText.loadModel("path/data.model",true);

//load from c++ format
FastText fastText = FastText.loadFasttextBinModel("path/wiki.bin") 
```



## NearestNeighbor

주어진 단어와 유사도가 높은 단어들을 가져오는 메서드이다.

```java
// get Nearest 10 Words
FastText fastText = FastText.loadModel("fastTextDataModel.model", true);
List<FloatStringPair> list = fastText.nearestNeighbor("Word", 원하는 단어 갯수)
    
for (FloatStringPair s : list){
    System.out.println(s.second  + "," + s.first);
    // second 가 단어, first가 similarity이다.
   }
```

