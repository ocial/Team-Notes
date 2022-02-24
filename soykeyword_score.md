# SoyKeyword



## 연관어 점수 산정 기준

* 결과 예시

```python
> print(extract_soykeyword_associate('용역')[:5])

> [KeywordScore(word='용역', frequency=1461, score=1.0),
  KeywordScore(word='학술', frequency=78, score=0.9953686442064426),
  KeywordScore(word='연구', frequency=108, score=0.9830756172269993),
  KeywordScore(word='버스', frequency=11, score=0.9812304261912907),
  KeywordScore(word='검진', frequency=12, score=0.9721074053439924)]
```

<br>

* score 산정 기준

>  $score(w) = P(w|pos)\;/\;\{\;P(w|pos) + P(w|neg)\;\}$
>
> $P(w|pos)$ : 키워드를 추출할 문서 집합에서의 단어 $w$ 의 출연 비율
>
> $P(w|neg)$ : 그 외 문서 집합에서의 단어 $w$ 의 출연 비율
>
> 키워드를 추출할 문서 집합 : 키워드와 연관어가 동시에 나온 문서 집합의 수 총합
>
> 그 외 문서 집합 : 키워드를 제외한 연관어만 나온 문서 집합의 수 총합

<br>

* 예시 - 검색어 : '용역', 연관어 : '학술'

    >'용역' 키워드가 나온 문서 집합에서의 연관어가 나온 집합의 수 총합
    >
    > : sum( {'용역' : 1461, '학술' : 74, '연구' : 90, ... }.values( ) ) = 11,465
    >
    >그외 문서 집합의 수 총합
    >
    > : sum( {'용역' : 0, '학술' : 4, '연구' : 18, '입찰' : 2260, ... }.values( ) )  = 133,192
    >
    ><br>
    >
    >$P(w|pos) = 74\;/\;11465$
    >
    >$P(w|neg) = 4\;/\;113192$
    >
    ><br>
    >
    >$score(w) = (74/11465)\;/\;((74/11465) + (4/113192)) = 0.9954$

    

