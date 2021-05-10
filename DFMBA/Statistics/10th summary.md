## 경영통계분석 10주차 요약 자료 - 20214025 오수열

> 본 요약 과제는 깃허브를 통해 정리하여 pdf 파일로 다운로드 하였습니다.  

<br>

# Simple Linear Regression

> 선형회귀분석 : 두 변수 사이의 관계를 선형함수 관계로 분석하는 것
>
> 예시) 아버지와 아들의 키, 광고비와 매출액, 소득과 신용카드 사용금액 등
>
> 단순선형회귀 : X변수가 하나인 경우 <> 다중선형회귀 : 여러개인 경우
>
> Y 변수 = 반응변수(response variable), 종속변수(dependent variable)
>
> X 변수 = 설명변수(explanatory variable), 예측변수(predictor), 독립변수(independent) 
>
> **단순선형회귀모형**
>
> $Y = \beta_0 + \beta_1X + \varepsilon$
>
> $Y$ : 종속변수, $X$ : 독립변수, $\beta_0$ : 절편(intercept), $\beta_1$ : 기울기(slope), $\varepsilon$ : 오차
>
> **단순선형회귀식**
>
> Y의 기댓값(평균) : $E(Y) = \beta_0 + \beta+1X$

<br>

### 최소제곱추정법

> 최소제곱법(least squares method) :
>
> 회귀분석의 목적은 회귀식에서 미지의 모수 $\beta_0, \beta_1$ 을 추정하는 것
>
> 최소제곱추정법 이용한 $\beta_0, \beta_1$ 의 추정값 $b_0, b_1$
>
> $b_1 = \frac{\Sigma(x_i-\bar{x})(y_i-\bar{y})}{\Sigma(x_i-\bar{x})^2} = r_{xy}\frac{s_y}{s_x}$
>
> $b_0 = \bar{y} - b_1\bar{x}$

<br>

### 단순선형회귀모형의 가정

$$Y_i = \beta_0 + \beta_1X_i + \varepsilon_i\qquad i=1,\;...,\;n$$

1. 오차항($\varepsilon_i$) 의 평균은 0이고 분산은 $\sigma^2$ 이다. 즉, $E(\varepsilon_i) = 0,\; Var(\varepsilon_i)=\sigma^2$ (등분산 가정)
2. 오차항($\varepsilon_i$) 들은 서로 독립이다.
3. 오차항($\varepsilon_i$) 은 정규분포를 따른다.

<br>

### 회귀계수 유의성 검정

> 선형관계가 없다면 회귀계수 $\beta_1$ 의 값이 0일 것이다.  
> 그래서 $\beta_1$ 의 값이 0인지 아닌지에 관심을 갖게 되는 것
>
> $$SST = \Sigma(y_i-\bar{y})^2 = \Sigma(\hat{y}_i-\bar{y})^2 + \Sigma(y_i-\hat{y}_i)^2 = SSR + SSE$$
>
> SST : 총제곱합 (Total Sum of Squares), 총변동량
>
> SSR : 회귀제곱합 (Regression Sum of Squares), 회귀변동량
>
> SSE : 오차제곱합 (Error Sum of Squares), 오차변동량
>
> <br>
>
> $$s^2 = \hat{\sigma^2} = MSE = \frac{SSE}{n-2} = \frac{\Sigma(y_i-\hat{y}_1)^2}{n-2}$$
>
> 오차항($\varepsilon$) 의 분산 $\sigma^2$ 은 위와 같이 오차평균제곱(MSE)로 추정된다.
>
> MSE 자유도 = 관찰값의 수 - 회귀계수의 수($\beta_0, \beta_1$) = n - 2
>
> <br>
>
> 기울기($\beta_1$) 에 대한 유의성 t 검정
>
> 1. 귀무가설 : $H_0 : \beta_1 = 0$  vs 대립가설 : $H_a : \beta_1 \neq 0$
> 2. 검정통계량 : $t = \frac{b_1}{S_{b_1}} \sim t_{n-2}$  
>     여기서 $S_{b_1} = \frac{S}{\sqrt{\Sigma(x_i-\bar{x})^2}},\; S = \sqrt{MSE}$
>
> <br>
>
> 단순회귀모형에 대한 유의성 F 검정
>
> 1. 귀무가설 : $H_0 : \beta_1 = 0$  vs 대립가설 : $H_a : \beta_1 \neq 0$
> 2. 검정통계량 : $F = \frac{MSR}{MSE} \sim F_{1,\; n-2}$

<br>

#### 단순선형회귀모형의 분산분석(ANOVA) 표

| 변동요인 | 제곱합(SS) | 자유도 | 제곱평균(MS) | 검정통계량 |
| -------- | ---------- | ------ | ------------ | ---------- |
| 회귀 | SSR | 1 | MSR = SSR/1 | F = MSR/MSE |
| 잔차 | SSE | n-2 | MSE = SSE/(n-2) | |
| 계 | SST | n-1 | | |

<br>

### 결정계수

> 회귀식이 얼마나 원래의 자료를 잘 정리 요약하여 반영하고 있는지를 나타내는 척도나 계수
>
> $R^2 = \frac{회귀변동량}{총변동량} = \frac{SSR}{SST} = 1 - \frac{SSE}{SST}$
>
> 1. $0 \leq R^2 \leq 1$
> 2. $R^2$ 이 1에 가까울수록 추정된 회귀식이 총변동량의 많은 부분을 설명한다.
> 3. $R^2$ 이 0에 가까울수록 추정된 회귀식이 총변동량을 적절하게 설명하지 못한다.



