## 경영통계분석 11주차 요약 자료 - 20214025 오수열

> 본 요약 과제는 깃허브를 통해 정리하여 pdf 파일로 다운로드 하였습니다.  

<br>

# Multiple Linear regression

> 다중선형회귀분석 : 둘 이상의 설명변수를 고려하는 것

<br>

### 다중선형회귀

- 다중선형회귀모형

    $$Y = \beta_0 + \beta_1X_1 + \beta_2X_2 + ... + \beta_kX_k + \varepsilon$$

    여기서 $Y$ : 종속변수, $X_j$ : $j$번째 독립변수, $\beta_0$ : $Y$ 절편, $\beta_j$ : $j$번째 모수, $\varepsilon$ : 오차

    오차 $\varepsilon$ 은 평균 $\mu_\varepsilon = 0$  와 분산 $\sigma^2$ 이고, 독립변수 $X$ 와 연관이 없는 것으로 가정

- 다중선형회귀식

    $$E(Y_i) = \beta_0 + \beta_1x_{1i} + \beta_2x_{2i} + ... + \beta_kx_{ki},\quad i=1,\;...,\;n$$

- 추정된다중선형회귀식

    $$\hat{y}_i = b_0 + b_1x_{1i} + b_2x_{2i} + ... + b_kx_{ki},\quad i=1,\; ...,\; n$$

- 최소제곱추정법

    추정값 제곱의 합이 최소화되도록 $\beta_0$ 을 선택하는 방법

- 추정계수의 해석

    $j$ 번째 설명변수 $X_j$ 를 제외한 나머지 설명변수 들이 고정되어 있다는 가정하에  
    $X_j$ 가 1단위 변화할 때 $Y$ 의 변화량

<br>

### 유의성 검정

> $$SST = \Sigma(y_i-\bar{y})^2 = \Sigma(\hat{y}_i-\bar{y})^2 + \Sigma(y_i-\hat{y}_i)^2 = SSR + SSE$$
>
> SST : 총제곱합 (Total Sum of Squares), 총변동량
>
> SSR : 회귀제곱합 (Regression Sum of Squares), 회귀변동량
>
> SSE : 오차제곱합 (Error Sum of Squares), 오차변동량
>
> $SSE = \Sigma(y_i-\hat{y}_i)^2 = \Sigma(y_i - b_0 - b_1x_{1i} - b_2x_{2i} - ... - b_kx_{ki})^2$
>
> 오차항의 분산은 다음과 같이 오차평균제곱 MSE(Mean Square due to Error)로 추정된다.
>
> $s^2 = \hat{\sigma^2} = MSE = \frac{SSE}{n-k-1},\quad n-k-1$ 은 자유도이다.

<br>

#### 다중선형회귀모형에 대한 유의성 $F$ 검정

> 1. 귀무가설 및 대립가설
>
>     $H_0 : \beta_1 = ... = \beta_k = 0$
>
>     $H_a :$  적어도 하나의 $\beta_j$ 는 0이 아님
>
> 2. 검정통계량
>
>     $F = \frac{MSR}{MSE} = \frac{SSR/k}{SSE/(n-k-1)} \sim F(k, n-k-1)$
>
> 3. 검정 방법
>
>     (1) p값 방법 : 만약  $p값 \leq \alpha$ 이면, $H_0$ 기각
>
>     (2) 기각역 방법 : 만약 $F \geq F_\alpha$ 이면, $H_0$ 기각

<br>

#### 다중회귀모형의 분산분석(ANOVA) 표

| 변동요인 | 제곱합(SS) | 자유도 | 제곱평균(MS)      | 검정통계량  |
| -------- | ---------- | ------ | ----------------- | ----------- |
| 처리     | SSR        | k      | MSR = SSR/1       | F = MSR/MSE |
| 오차     | SSE        | n-k-1  | MSE = SSE/(n-k-1) |             |
| 계       | SST        | n-1    |                   |             |

<br>

#### 개별 계수($\beta_j$) 에 대한 유의성 $t$ 검정

> 1. 귀무가설 및 대립가설
>
>     $H_0 : \beta_j =0$
>
>     $H_a : \beta_j \neq 0$
>
> 2. 검정통계량
>
>     $t = \frac{b_j}{s_{b_j}} \sim t(n-k-1)$

<br>

### 결정계수

> 회귀식이 얼마나 원래의 자료를 잘 정리 요약하여 반영하고 있는지를 나타내는 척도나 계수
>
> $R^2 = \frac{회귀변동량}{총변동량} = \frac{SSR}{SST} = 1 - \frac{SSE}{SST}$
>
> 1. $0 \leq R^2 \leq 1$
> 2. $R^2$ 이 1에 가까울수록 추정된 회귀식이 총변동량의 많은 부분을 설명한다.
> 3. $R^2$ 이 0에 가까울수록 추정된 회귀식이 총변동량을 적절하게 설명하지 못한다.

<br>

### 다중회귀모형의 가정사항과 진단

> * 다중선형회귀모형의 가정
>
>     1. 오차항의 평균은 0이다. $E(\varepsilon_i) = 0$
>     2. 오차항의 분산 $\sigma^2$ 는 $X_{ij}$ 의 모든 값에 대하여 항상 같다(등분산 가정 : $Var(\varepsilon_i) = \sigma^2$)
>     3. 오차항들은 서로 독립적이다.
>     4. 오차항은 정규분포를 따른다.
>
> * 회귀진단 항목
>
>     모형의 선형성(linearity)
>
>     오차의 정규성(normality), 등분산성(homoscedasticity), 독립성(independence)
>
>     이상값(outlier)의 존재
>
>     영향관찰치(influential observation)의 존재
>
>     다중공선성(multicollinearity)

<br>

### 가변수

> 가변수 : 질적변수이지만 통계분석을 위하여 0과 1로 코딩된 변수
>
> 예시) 남 = 0, 녀 = 1

<br>

### 다항회귀

> 다항회귀모형(polynomial regression model)
>
> 2차다항회귀모형(quadratic regression model)