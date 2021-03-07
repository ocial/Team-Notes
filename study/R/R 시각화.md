# R 시각화 도구, ggplot2

> ggplot2 패키지 :
>
> *  통계 프로그래밍 언어 R에 대한 데이터 시각화 패키지

1. 각종 데이터에 대한 다양한 시각화 방식
2. 패키지 설치 및 준비
3. 기본 그래프 그리기(코드 설명)
4. 응용 그래프 샘플 보여주기
5. (추가) 기본 그래프 그리기 실습자료 만들기



## 패키지 설치 및 준비

```R
# ggplot2 패키지 설치
install.packages("ggplot2")

# ggplot2 패키지 불러오기
library(ggplot2)
```

<br>

## 기본 그래프 그리기

> ggplot( ) 함수를 이용해 기본 그래프를 그려봅니다.

```R
# ggplot() 기본 형식 :
# ggplot(data = 데이터 세트, aes(x = x축 데이터, y = y축 데이터))
ggplot(data = mpg, aes(x = displ, y = hwy))
```

