# R 기초

> R : 오픈 소스 데이터 분석 소프트웨어

* R, R Studio 다운로드

```R
# R 다운로드 : https://cran.r-project.org/mirrors.html
# R Studio 다운로드 : https://www.rstudio.com/products/rstudio/download
```

<br>

* 기본 단축키

```R
# 실행 : Ctrl + Enter
# 대입 연산자 : Option + '-'
```

<br>

* 환경 설정

```R
# Tools > Global Options... > Code > General > ☑️ Sort-wrap R source files
# Tools > Project Options... > Code Editing > Text encoding: UTF-8
```

<br>

* 변수

```R
a <- 1
b <- 2

var1 <- c(1, 2, 3, 4, 5)
var2 <- c(1:5)
var3 <- seq(1, 5)
var4 <- seq(1, 10, 2)

str1 <- "a"
str2 <- "Hello World"
str3 <- c("a", "b", "c")
```

<br>

* 함수

```R
paste(str3, collapse=", ")
```

<br>

* 패키지

> 패키지 : 함수 꾸러미

```R
# 패키지 설치
install.packages("ggplot2")
install.packages('readxl')
install.packges('dplyr')

# 패키지 불러오기
library(ggplot2)  # 시각화
library(readxl)  # 엑셀 불러오기
library(dplyr)  # 데이터 전처리

# 함수 사용
x <- c("a", "a", "b", "c")
qplot(x)  # 빈도 막대 그래프
qplot(data = mpg, x = drv, y = hwy, geom = "boxplot", colour = drv)

# Help 함수
?qplot

# 패키지에 내상된 데이터 불러오기
mpg <- as.data.frame(ggplot2::mpg)
```

<br>

* 데이터 프레임

```R
# 데이터 프레임 만들기
english <- c(90, 80, 60, 70)
math <- c(50, 60, 100, 20)

df_midterm <- data.frame(english, math)

# 분석하기
mean(df_midterm$english)
max(df_midterm$math)

# 엑셀 데이터 불러오기
libray(readxl)
df_exam <- read_excel("excel_exam.xlsx", sheet = 1, col_names=T)  # 첫 번째 행 변수명으로 인식

# csv 파일 불러오기
df_csv_exam <- read.csv("csv_exam.csv", stringsAsFactors = F)  # 문자가 들어 있는 파일 문자 타입으로 지정

# csv 파일로 저장하기
write.csv(df_midterm, file = "df_midterm.csv")

# RData 파일로 저장하기
save(df_midterm, file = "df_midterm.rda")

# RData 파일 불러오기
load("df_midterm.rda")

# 기본 함수
head(df)
tail(df)
View(df)
dim(df)  # 데이터 차원
str(df)  # 데이터 속성
summary(df)  # 요약 통계량
table(df)  # 빈도수 확인
```

<br>

* 데이터 전처리

```R
libary(dplyr)

df_raw <- data.frame(var1 = c(1, 2, 1),
                     var2 = c(2, 3, 2))

df_new <- df_raw
df_new <- rename(df_new, v2 = var2)  # 칼럼명 var2를 v2로 수정

df <- df_raw
df$var_sum <- df$var1 + df$var2  # 파생변수 만들기

mpg$total <- (mpg$cty + mpg$hwy)/2
mpg$test <- ifelse(mpg$total >= 20, "pass", "fail")  # 조건문 활용 파생변수 만들기

mpg$grade <- ifelse(mpg$total >= 30, "A",
                   ifelse(mpg$total >= 25, "B",
                         ifelse(mpg$total >= 20, "C", "D")))  # 중첩 조건문 활용

# 전처리 함수
filter(조건)  # 행 추출, &(and), |(or), %in%(in)
select(열이름1, 열이름2)  # 열 추출, -열이름(제외)
arrange(열이름)  # 정렬, desc(열이름)
mutate(새칼럼명 = 파생변수 만들기)  # 변수 추가
summarise(새변수 = 함수())  # 통계치 산출, n() : 빈도, sd() : 표준편차
group_by(열이름)  # 그룹화
left_join(df1, df2, by="열이름")  # 데이터 합치기(열)
bind_rows(df1, df2)  # 데이터 합치기(행) 

exam <- read.csv("csv_exam.csv")
exam %>% filter(class == 1)  # exam에서 class가 1인 경우만 출력

exam %>% 
	filter(class == 1) %>% 
	select(english)  %>%
	head  # %>% 추가 사용으로 조합 가능

exam %>% summarise(mean_math = mean(math))  # math 평균 산출

exam %>%
	group_by(class) %>%
	summarise(mean_math = mean(math),
              sum_math = sum(math),
              median_math = median(math),
              n = n())

mpg %>%
	group_by(manufacturer) %>%  # 회사별 분리
	filter(class == "suv") %>%  # suv 추출
	mutate(tot = (cty+hwy)/2) %>%  # 통합 연비 변수 생성
	summarise(mean_tot = mean(tot)) %>%  # 통합 연비 평균 산출
	arrange(desc(mean_tot)) %>%  # 내림차순 정렬
	head(5)  # 1~5위 까지 출력
```

<br>

* 데이터 정제(결측치, 이상치)

```R
# 결측치
is.na(df)  # 결측치 확인
table(is.na(df))  # 결측치 빈도 출력
na.omit(df)  # 결측치가 있는 행 삭제

함수(df$열이름, na.rm = T)  # 결측치 제외하고 산출

exam[c(3, 8, 15), "math"] <- NA  # 3, 8, 15행의 math에 NA 할당

exam$math <- ifelse(is.na(exam$math), 55, exam$math)  # math가 NA면 55로 대체

# 이상치
outlier <- data.frame(sex = c(1, 2, 1, 3, 2, 1),
                      score = c(5, 4, 3, 4, 2, 6))

table(outlier$sex)
table(outlier$score)  # 빈도로 이상치 확인

boxplot(mpg$hwy)  # 상자그림으로 극단치(이상치) 확인
boxplot(mpg$hwy)$stats  # 통계치 출력

mpg$hwy <- ifelse(mpg$hwy < 12 | mpg$hwy > 37, NA, mpg$hwy)  # 극단치 NA 할당
```