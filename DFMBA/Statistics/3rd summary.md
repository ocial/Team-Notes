## 경영통계분석 3주차 요약 자료 - 20214025 오수열

> 본 요약 과제는 깃허브를 통해 정리하여 pdf 파일로 다운로드 하였습니다.  
> github 주소 : http://bit.ly/2NpKPmE

<br>

# Probability

> **확률**
>
> : 통계를 분석하기 위하여는 통계이론이 필요하고, 통계이론은 확률을 바탕으로 확립된다. 
>
> * 확률을 정의하기 위해선 먼저 일어날 수 있는 모든 사건을 정확히 정의해야 한다.
> * 확률은 표본공간의 원소들을 0에서 1사이의 숫자로 연결시키는 함수
> * <u>**표본공간(sample space)**</u> = <u>**일어날 수 있는 모든 가능(exhaustive)**</u>한 <u>**사건(simple event)**</u>의 집합
> * 사건들은 <u>**상호배반(mutually exclusive)적**</u>이어야 한다.
> * 상호배반 = 겹치는 부분이 없다.

<br>

## 확률의 정의

> <u>**전통적(논리적) 접근(classical approach)**</u>
>
>  - 똑같은 가능성의 사건을 똑같은 확률값을 갖도록 정의
>  - 똑같은 가능성이 아닌 경우의 확률에는 사용할 수 없다.(비가 올 확률과 맑은 확률)
>
> <u>**상대적 비율 접근(reletive frequency approach)**</u>
>
>  - 실험을 진행하면서 전체 실험 중에 특정 사건이 발생한 상대적 비율을 계속 기록해 나갈때 
>     그 수열이 어떤 값으로 수렴해간다면 그 값을 정의하는 것  
>     (주사위를 무수히 많이 계속 던지면서 '5'가 나올 상대적 비율을 계속 기록)
>
> <u>**주관적 접근(subjective approach)**</u>
>
>  - 어떤 사건이 일어날 가능성에 대한 믿음의 정도(degree of belief)  
>     (내일 비가 올 가능성에 대한 믿음이 강하면 비올 확률이 높은 값)
>
> * <u>**빈도론자(Frequentist)**</u> : 상대적 비율 접근을 택하는 학자
> * <u>**베이지안(Bayesian)**</u> : 주관적 접근을 택하는 학자

<br>

## 확률 공식

**확률 할당의 기본 필요조건**

> 표본공간이 사건 {$E_1,\,E_2,\,...,\,E_n$} 들로 이루어졌을 때  
> 각각의 확률은 0과 1사이에 있어야 하고,  
> 이들 확률을 전부 더하면 1이 되어야 한다.

$$0 \leq P(E_i)  \leq 1 \,\, for\,all\,i$$

$$P(E_1)\,+\,P(E_2)\,+\,...\,+\,P(E_n)\,=\,1$$


**여집합 규칙(complement rule)**

> Ex) 비가 오는 확률은 1에서 비가 오지 않는 확률을 뺀 것과 같다.

​	$$P(A)\,=\,1\,-\,P(A^c)$$


**합 규칙(addition rule)**

> 합집합 확률 = 각각의 확률 - 교집합 확률

​	$$P(A\,\cup\,B)\,=\,P(A)\,+\,P(B)\,-\,P(A\,\cap\,B)$$


**상호 배반(mutually exclusive) 사건의 합 규칙**

> 상호배반 = 사건 A와 B가 서로 겹치는 부분이 없을 때, 공집합일 때

$$P(A\,\cup\,B)\,=\,P(A)\,+\,P(B)$$


**조건확률(conditional probability)**

> 조건이 걸려있는 확률값

$$P(A|B)\,=\,\frac{P(A\,\cap\,B)}{P(B)}$$

$$P(B|A)\,=\,\frac{P(A\,\cap\,B)}{P(A)}$$


**독립사건(independent events)의 정의**

> 어느 사건이 다른 사건과 일어나는 확률이 서로 무관할 때 이를 독립사건이라 한다.

$$P(A|B)\,=\,P(A) \quad 또는 \quad P(B|A)\,=\,P(B)$$


**곱셈 규칙(multiplication rule)**

> 조건확률의 공식을 이용함

$$P(A\,\cap\,B)\,=\,P(B)\,P(A|B)$$

$$P(A\,\cap\,B)\,=\,P(A)\,P(B|A)$$


**독립사건의 곱셈 규칙**

> 독립사건의 정의 공식을 이용함

$$P(A\,\cap\,B)\,=\,P(A)\,P(B)$$

<br>

## 베이즈 정리

> 어떤 조건확률을 구할 때 그 조건 상황이 역으로 되어 있는 확률을 이용하는 것
>
> * evidence를 관측하여 갱신하기 전 후의 내 주장에 관한 신뢰도

<img src="https://raw.githubusercontent.com/angeloyeo/angeloyeo.github.io/master/pics/2020-01-09-Bayes_rule/pic1.png" width="600" height="300"/>

<br>

## 나무그림

> 수형도, tree diagram

<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/9/9c/Probability_tree_diagram.svg/848px-Probability_tree_diagram.svg.png" width="600" height="400"/>

<br>

<br>

# Discrete random varible

<br>

## 확률변수

> <u>**확률변수(random variable)**</u> : 확률 실험 결과(에 대한 숫자적 표현)
>
> <u>**이산 확률변수(discrete random variable)**</u>
>
> : 유한(finite) 개이거나 셀수 있는 무한한(countable) 값을 갖는 확률변수
>
> <u>**연속형 확률변수(continuous random variable)**</u>
>
> : 무한개이거나 그것이 취할 수 있는 값들이 셀수 없는 값을 갖는 확률변수

<br>

## 이산형 확률분포

> <u>**확률분포(probability distribution)**</u> : 확률변수가 취할 수 있는 값들에 확률을 대응해 둔 것
>
> <u>**이산형 확률분포(discrete probability distribution)**</u>
>
> : 이산형 확률변수에 대응되는 확률분포
>
> **확률질량함수(probability mass function)** : 확률변수 X가 값 x를 갖는 확률, $f(x_k)$
>
> 누적확률질량함수 : $F(x_k)$

<br>

## 평균과 표준편차

> <u>**기댓값(expected value, expectation)**</u> : $E$
>
> X의 평균, $E(X)$
>
> X의 분산, $Var(X)$ = $E([X-E(X)]^2)$ = $E(X^2)-E(X)^2$
>
> X의 표준편차, $SD(X)$ = $\sqrt{Var(X)}$

<br>

## 이항분포

> <u>실험이 오직 두 가지의 결과만을 갖는 경우를 설명하기 위한 분포</u>
>
> **베르누이 시행(Bernoulli trial)**
>
> 1. 각 시행은 성공과 실패로 표현될 수 있는 두 가지 결과만을 갖는다.
> 2. 각 시행에서 성공의 확률은 $p$ 이고, 실패의 확률은 $1-p$ 이다.

**이항확률분포의 평균과 분산**

$$E(X) = n \cdot p$$

$$Var(X) = n \cdot p \cdot (1-p)$$


**이항분포의 가법성(additivity)**

$$X \sim B(n, p),\,Y \sim B(m, p)\,\, 이고\,\, X와\,\, Y가\,\,독립이면 $$  

$$X+Y \sim B(n+m,\, p)$$

<br>

## 포아송분포

> 고정된 지역, 시간 또는 부피 등에서 관심 있는 사건의 관찰수 또는  
> 발생 횟수 $X$를 표현하는데 자주 사용된다.
>
> * $X$의 예시
>
> 1. 오늘 하루 우리 학교 컴퓨터에 접속한 사용자의 수
> 2. 어느 주말 일요일에 발생한 교통사고 사망자의 수
> 3. 어느 보험 회사의 주말 동안의 보험 클레임 건수
> 4. 어느 하루 동안 지정된 생산라인에서 발생한 불량품의 개수
> 5. 전국에서 조류독감 '리' 단위 발생지역의 수

