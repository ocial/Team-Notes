## 경영통계분석 12주차 요약 자료 - 20214025 오수열

> 본 요약 과제는 깃허브를 통해 정리하여 pdf 파일로 다운로드 하였습니다.  

<br>

# Model Building

> 모형구축 : 자료에서 주는 정보를 이용하여 상황을 이해하기 쉬운 형태롤 바꾸는 것  
> (모형구축에는 다양한 방법이 있지만 여기서는 회귀분석의 모형만을 다룬다.)

<br>

### 변수변환

> 변수변환(variable transformation)은 기본적으로 비선형 관계에 있는 설명변수와 반응변수를  
>  선형 관계로 변화시키기 위하여 행해진다.
>
> 자주 사용하는 변수변환 함수
>
> * 로그변환 : $log(x)$
> * 자승변환 : $x^2$
> * 제곱근변환 : $\sqrt{x}$
> * 역수변환 : $\frac{1}{x}$

<br>

### 모형비교

> 고려 대상이 되는 모형들을 비교하여 최적의 모형을 구축

<br>

모형 비교 검정통계량

$$\frac{\frac{SSE_{Small Model}-SSE_{Big Model}}{df_{Small Model}-df_{Big Model}}}{\frac{SSE_{Big Model}}{df_{Big Model}}} \sim F(df_{Small Model} - df_{Big Model},\; df_{Big Model})$$

<br>

예제 16.1 - 검은 체리나무 자료 모형 비교

> 큰 모형 : $logVolume = \beta_0 + \beta_1 logGirth + \beta_2 logHeight + \varepsilon$
>
> 작은 모형 : $logVolume = \beta_0 + \beta_1 logGirth + \varepsilon$ 
>
> 가설 : $H_0 : \beta_2 = 0\quad vs \quad H_1 : not\; H_0$

* 작은 모형(logGrith)의 분산분석표

|           | Df   | Sum Sq | Mean Sq | F value | Pr ( >F )   |      |
| --------- | ---- | ------ | ------- | ------- | ----------- | ---- |
| logGrith  | 1    | 7.9254 | 7.9254  | 599.72  | < 2.2e - 16 | ***  |
| Residuals | 29   | 0.3832 | 0.0132  |         |             |      |

<br>

* 큰 모형(logGrith, logHeight)의 분산분석표

|           | Df   | Sum Sq | Mean Sq | F value | Pr ( >F )   |      |
| --------- | ---- | ------ | ------- | ------- | ----------- | ---- |
| logGirth  | 1    | 7.9254 | 7.9254  | 1196.53 | < 2.2e - 16 | ***  |
| logHeight | 1    | 0.1978 | 0.1978  | 29.86   | 7.805e - 06 | ***  |
| Residuals | 28   | 0.1855 | 0.0066  |         |             |      |

<br>

* 검정통계량

$$F = (\frac{SSE_{Small Model}-SSE_{Big Model}\;/\;df_{Small Model}-df_{Big Model}}{SSE_{Big Model}\;/\;df_{Big Model}}) = (\frac{(0.3832-0.1855)\;/\;{(29-28)}}{0.1855\;/\;28}) = 29.84$$

* 결과 : p값은 0.000007017이 되어 귀무가설을 기각. 즉, logHeight를 제거할 수 없다.

<br>

### 로지스틱회귀

> Y변수가 두 가지 값을 갖는 명목형 자료일 때 사용
>
> X변수가 명목형 자료일 때 사용하는 가변수(dummy variable) 모형은 0과 1을 그대로 사용하지만  
> 로지스틱모형에서는 0 또는 1이 될 확률을 이용하여 Y변수를 만들게 된다.
>
> 즉, Y는 $p = Pr(Y=1)$ 을 모수로 갖는 베르누이 시행

<br>

* 로지스틱회귀모형

$$E(Y) = \frac{e^{\beta_0 + \beta_1X_1 + ... + \beta_kX_k}}{1 + e^{\beta_0 + \beta_1X_1 + ... + \beta_kX_k}} = \frac{1}{1 + e^{-\beta_0 - \beta_1X_1 - ... - \beta_kX_k}}$$

![img](https://t1.daumcdn.net/cfile/tistory/99F325485C7B76BC2B)

<br>

* 로짓변환

어떤 사건이 발생하는 것에 대한 오즈(odds) = 사건이 발생하는 확률(p)을 사건이 발생하지 않는 확률(1-p)로 나눈 값

오즈에 로그를 취한 것 = 로그 오즈(log-odds) = 로짓(logit)

로짓변환(logit transformation) : 오즈를 로짓으로 변환하는 것

<br>

* 회귀계수의 검정

로지스틱회귀에서도 다중회귀에서와 같이 $\beta_1, ..., \beta_k$ 의 값이 전부 0인지 관심이 있다.

가설 : $H_0 : \beta_1 = ... = \beta_k = 0 \quad vs \quad H_1 : not\;H_0$ (At leat on of the parameter is not zero.)

<br>

### 변수선택

> 변수선택(variable selection) : 회귀식에 포함될 설명변수를 고르는 것
>
> 전진선택법(Forward selection method)
>
>  : 더 이상의 유의적인 추가 변수가 없을 때까지 변수를 하나씩 더해가는 방법
>
> 후진제거법(Backward elimination method)
>
>  : k 개의 모든 독립변수들을 포함하는 회귀모형을 우선 만들고 가장 유의하지 않은 독립변수를 제거해 나가는 과정
>
> 단계적선택법(Stepwise selection method)
>
>  : 일단 한 번 모형에 포함된 독립변수는 나중에 절대로 모형에서 제거 되지 않으며 한 번 모형에서 제거된 독립변수는 다시 모형에 포함될 수 없음

