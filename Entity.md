---


---

<h1 id="과제-관련-미리-공부">과제 관련 미리 공부</h1>
<h2 id="엔티티">엔티티?</h2>
<ul>
<li>실체, 개체라는 의미로 실무적으로는 엔티티라고 부른다.</li>
<li>업무에 필요하며, 유용한 정보를 저장하고 관리하기 위한 집합적인 것</li>
<li>업무 활동상 지속적인 관심을 가지고 있어야 하는 대상</li>
<li>그 대상들 간에 동질성을 지닌 인스턴스들이나 그들이 행하는 행위의 집합</li>
<li>그 집합에 속하는 개체들의 특성을 설명할 수 있는 속성</li>
<li>인스턴스의 집합</li>
</ul>
<h3 id="엔티티-표기법">엔티티 표기법</h3>
<p><img src="https://jistol.github.io/assets/img/database/database-entity-attribute-relationship/1.png" alt=""></p>
<h3 id="엔티티-특징">엔티티 특징</h3>
<p>아래의 특징을 만족하지 못하는 엔티티는 부적절한 엔티티이다.</p>
<ol>
<li>반드시 시스템을 구축하고자 하는 업무에서 필요하고 관리하고자 하는 정보여야한다.</li>
<li>유일한 식별자에 의해 식별이 가능해야한다.</li>
<li>영속적으로 존재하는 인스턴스의 집합이 되어야한다.</li>
<li>업무 프로세스는 그 엔티티를 반드시 이용해야한다.</li>
<li>엔티티타입에는 반드시 속성(attributes)이 포함되어있다.</li>
<li>엔티티 타입은 다른 엔티티 타입과 최소 한 개 이상의 관계가 있어야한다.
<ul>
<li>단, 데이터 모델링을 하며 관계를 생략하여서 표현해야 하는 경우는 통계성 엔티티 도출, 코드성 엔티티 도출, 시스템 처리시 내부 필요에 의한 엔티티 도출과 같은 경우이다.</li>
</ul>
</li>
</ol>
<h3 id="엔티티-분류">엔티티 분류</h3>
<ol>
<li>유무형에 따른 분류</li>
</ol>

<table>
<thead>
<tr>
<th>명칭</th>
<th>설명</th>
<th>예시</th>
</tr>
</thead>
<tbody>
<tr>
<td>유형 엔티티</td>
<td>물리적 형태가 있고, 안정적이며 지속적으로 활용되는 엔티티</td>
<td>사원, 물품, 강사</td>
</tr>
<tr>
<td>개념 엔티티</td>
<td>물리적 형태가 없고, 관리해야할 개념적 정보로 구분되는 엔티티</td>
<td>조직, 보험상품</td>
</tr>
<tr>
<td>사건 엔티티</td>
<td>업무를 수행함에 따라 발생되는 엔티티 타입으로, 각종 통계자료에 이용되는 엔티티</td>
<td>주문, 청구, 미납</td>
</tr>
</tbody>
</table><ol start="2">
<li>발생시점에 따른 분류</li>
</ol>

<table>
<thead>
<tr>
<th>명칭</th>
<th>설명</th>
<th>예시</th>
</tr>
</thead>
<tbody>
<tr>
<td>기본 엔티티</td>
<td>업무에 원래 존재하는 정보로서 독립적으로 생성되며, 자신은 타 엔티티의 부모 역할을 수행</td>
<td>사원, 부서, 고객, 상품</td>
</tr>
<tr>
<td>중심 엔티티</td>
<td>기본엔티티 타입에서 발생되고, 그 업무에서 중심적인 역할을 수행</td>
<td>계약, 사고, 청구, 주문</td>
</tr>
<tr>
<td>행위 엔티티</td>
<td>두 개 이상의 부모 엔티티 타입에서 발생되고, 내용이 자주 바뀌거나 데이터 양이 증가</td>
<td>주문목록, 로그인 이력</td>
</tr>
</tbody>
</table><h3 id="엔티티-설계하기">엔티티 설계하기</h3>
<p>데이터 모델링은 엔티티를 정의하는 것으로 시작한다.<br>
분석 초기에 엔티티를 선정하기 위해서 다음과 같은 방법, 자료를 이용하는 것이 좋다.</p>
<h2 id="속성attribute">속성(Attribute)?</h2>
<ul>
<li>업무에서 필요로 하는 인스턴스로 관리하고자 하는 의미상 더 이상 분리되지 않는 최소의 데이터 단위</li>
<li>의미상 더 이상 분리되지 않는 단위</li>
<li>엔티티를 설명하는 인스턴스의 구성요소</li>
</ul>
<h3 id="엔티티-인스턴스-속성-속성값의-관계">엔티티, 인스턴스, 속성, 속성값의 관계</h3>
<ul>
<li>
<p>한 개의 엔티티에는 두 개 이상의 인스턴스가 존재</p>
</li>
<li>
<p>각각의 엔티티에는 고유의 성격을 표현하는 속성정보를 두 개 이상 갖음</p>
</li>
<li>
<p>한 개의 속성은 한 개의 속성값을 갖음</p>
<p><img src="https://jistol.github.io/assets/img/database/database-entity-attribute-relationship/2.jpg" alt=""></p>
</li>
</ul>
<h3 id="속성의-특징">속성의 특징</h3>
<ul>
<li>업무에 필요한 정보</li>
<li>주 식별자에 함수적 종속성</li>
<li>한 개의 속성값만 갖는다. 다중 값일 경우, 별도의 엔티티를 이용하여 분리 필요</li>
</ul>
<h3 id="속성의-분류">속성의 분류</h3>
<ol>
<li>특성에 따른 분류</li>
</ol>

<table>
<thead>
<tr>
<th>명칭</th>
<th>설명</th>
<th>예시</th>
</tr>
</thead>
<tbody>
<tr>
<td>기본속성</td>
<td>업무로부터 추출한 값</td>
<td>이름, 전화번호, 성별</td>
</tr>
<tr>
<td>설계속성</td>
<td>규칙화를 위해 변형 // 새로 정의한 값</td>
<td>과목코드, 지역코드</td>
</tr>
<tr>
<td>파생속성</td>
<td>다른 속성에 영향을 받아 발생한 값</td>
<td>예금이자, 평균성적</td>
</tr>
</tbody>
</table><ol start="2">
<li>엔티티 구성 방식에 따른 분류</li>
</ol>

<table>
<thead>
<tr>
<th>명칭</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr>
<td>primary Key</td>
<td>엔티티를 식별할 수 있는 속성</td>
</tr>
<tr>
<td>Foreign Key</td>
<td>다른 엔티티와의 관계에서 포함된 속성</td>
</tr>
<tr>
<td>일반 속성</td>
<td>PK, FK에 포함되지 않은 속성</td>
</tr>
</tbody>
</table>
<table>
<thead>
<tr>
<th>명칭</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr>
<td>단순형</td>
<td>원자값 속성</td>
</tr>
<tr>
<td>복합형</td>
<td>여러 세부 속성으로 나뉠수 있는 속성</td>
</tr>
</tbody>
</table><h2 id="관계relationship">관계(Relationship)?</h2>
<h3 id="정의">정의</h3>
<ul>
<li>인스턴스 사이의 논리적인 연관성</li>
</ul>
<h3 id="관계의-패어링">관계의 패어링</h3>
<ul>
<li>
<p>엔티티안에 인스턴스가 개별적으로 관계를 가지는 것</p>
</li>
<li>
<p>패어링의 집합 -&gt; 관계</p>
<p><img src="https://jistol.github.io/assets/img/database/database-entity-attribute-relationship/3.jpg" alt=""></p>
</li>
</ul>
<h3 id="관계의-표기법">관계의 표기법</h3>
<ul>
<li>
<p>관계명(Membership) : 관계의 이름</p>
</li>
<li>
<p>관계차수(Cardinality) : 1:1, 1:M, M:N</p>
</li>
<li>
<p>관계 선택사항(Optionality) : 필수 관계(not null), 선택 관계(nullable, O를 표시)</p>
<p><img src="https://jistol.github.io/assets/img/database/database-entity-attribute-relationship/4.jpg" alt=""></p>
</li>
</ul>

