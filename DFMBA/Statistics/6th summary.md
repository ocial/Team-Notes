## 경영통계분석 6주차 요약 자료 - 20214025 오수열

> 본 요약 과제는 깃허브를 통해 정리하여 pdf 파일로 다운로드 하였습니다.  

<br>

# Estimation

> <u>**추론(inference) = 추정(estimation) + 검정(가설검정, hypothesis testing)**</u>
>
> * 과학적 추론(scientific inference) - 사과 떨어지는 현상을 관찰하여 만유인력이라는 현상 유추
> * 통계적 추론(statistical inference) - 표본에서 얻은 정보를 이용하여 모집단에 대하여 알아보려고 하는 것
>
> **추정(estimation)**
>
> * 점추정(point estimation) : 모수를 어떤 하나의 값으로 추정하는 것
> * 예시) 피그미족 평균 키는 135cm이다. $\hat\mu=\bar{X}=135cm$
>
> * 구간추정(interval estimation) : 구간으로 추정하는 것
> * 예시) 피그미족의 키는 평균 120cm에서 150cm 사이이다. $\hat\mu\in(120, 150)$
>
> <u>표본에서 얻은 통계량(statistic)으로 모수(parameter)를 추론하는 데 사용한다면 이것은 추정량(estimator)으로 불린다.</u>

<br>

## 점추정

> <u>**점추정**이란?</u> 
>
> : 표본에서 얻어지는 정보를 이용하여 미지인 모수의 참값으로 생각되는 하나의 값을 일정한 기준에 따라 택하는 과정
>
> <u>point estimator(점추정량)</u> : 점추정에 사용된 통계량
>
> <u>point estimate(점추정값)</u> : 표본에서 구한 point estimator의 값
>
> 점추정에는 항상 <u>sampling error(표집오차)</u>가 생긴다
>
> <br>
>
> 비편향성이란?
>
> : 엉뚱하게 다른 것을 추정하고 있는 것은 아닌지 판단하려는 것
>
> 추정량( $\hat\theta$ ) - 모수( $\theta$ ) = sampling error = 변동 + 편향
>
> 변동 = $\hat\theta - E(\hat\theta)$
>
> 편향 = $E(\hat\theta) - \theta$
>
> unbiased estimator(비편향추정량) : 추정량의 편향이 0이 되는 추정량
>
> <br>
>
> 효율성이란?
>
> : 어느 한 추정량의 분산이 다른 추정량의 분산보다 작은 경우(Low Variance)
>
> <br>
>
> Minimum variance unbiased estimator(최소분산비편향추정량)
>
> : 점추정에서 가장 이상적으로 추구하는 추정량의 하나

<img src="https://lh3.googleusercontent.com/rq_iMVSuIK1K4ykF9RQnF05hH6xxWm3lmNPWuQ3hfK9r4-3GBIuCxCW3L7QH53M3EIwbVWOcaRiRLDc0AIJ-0uq8-qzavpSWPceQ1lchq-ZPF16l3KLst24-x6MbGYFqQbEJmEI3gEc" height=500 />

 <br>

## 구간추정

> <u>**구간추정**이란?</u>
>
> : 모수를 하나의 값으로 추정하는 것이 아니라, 오차의 크기가 고려된 구간으로 나타내는 것
>
> confidence interval(신뢰구간) - 예시 : (a, b)
>
> confidence level(신뢰수준) - 예시 : 95%

<br>

### 모평균 $\mu$ 에 대한 구간추정

> * 모분산을 아는 경우
>
> $$(\bar{X}-z_{a/2}\frac{\sigma}{\sqrt{n}},\quad \bar{X}+z_{a/2}\frac{\sigma}{\sqrt{n}})$$
>
> * 모분산을 모르는 경우
>
> $$(\bar{X}-t_{a/2,\,n-1}\frac{s}{\sqrt{n}},\quad \bar{X}+t_{a/2,\,n-1}\frac{s}{\sqrt{n}})$$

<br>

### 모비율 $p$ 에 대한 구간추정

>  $$\bar{p}\pm z_{a/2}\sqrt{\frac{\bar{p}(1-\bar{p})}{n}}$$

<br>

## 표본수의 결정

> 오차한계( $d$ ) = 신뢰구간 폭의 절반
>
> $$d = z_{a/2}\frac{\sigma}{\sqrt{n}}$$
>
> 표본수 $n$ 이 증가할 수록 오차한계 $d$ 는 줄어든다.

<br>

### 오차한계 $d$ 를 만족시키는 표본수 $n$

>  $\sigma$ 를 알 경우의 $\mu$
>
> $$n=(z_{a/2}\frac{\sigma}{d})^2$$
>
> $\sigma$ 를 모를 경우의 $\mu$
>
> $$n=(t_{a/2,\,n-1}\frac{s}{d})^2$$
>
> 모비율 $p$
>
> $$n=z^2_{a/2}\frac{p(1-p)}{d^2}$$

<br>

# Hypothesis Testing

> **가설검정(hypothesis testing)**
>
> : 모집단의 어떤 현상에 대한 예상 또는 주장이 옳은지 틀린지를 표본자료를 이용하여 판단하려는 것
>
> **통계적 가설(statistical hypothesis)**
>
> * **귀무가설(null hypothesis)**
>
>     : 일반적으로 과거이론이나 또는 경험적으로 참이라고 믿어지지만 검정되어야 하는 가설
>
>     예시 - 생우유의 함유량은 50% 이다.
>
> * **대립가설(alternative hypothesis)**
>
>     : 귀무가설이 참이 아닌 경우 참이라고 믿어지는 가설
>
>     예시 - 생우유의 함유량은 [50%가 아니다, 50% 보다 적다, 50% 보다 많다]
>
>     one-sided test(단측검정) -  50% 보다 적다, 50% 보다 많다
>
>     two-sided test(양측검정) - 50%가 아니다
>
> **검정통계량(test statistic)** 
>
> : 검정에 사용하기 위하여 표본자료에서 구한 통계량
>
> **검정오류(test error)**
>
> * 제 1종 오류 : 귀무가설이 맞는데도 잘못하여 이를 기각
> * 제 2종 오류 : 대립가설이 사실임에도 불구하고 귀무가설을 채택

