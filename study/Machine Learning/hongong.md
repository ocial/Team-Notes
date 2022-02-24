# 빅데이터분석기사 정리



```python
import numpy as np
import pandas as pd

from sklearn.preprocessing import LabelEncoder
from sklearn.preprocessing import StandardScaler
from sklearn.preprocessing import MinMaxScaler
from sklearn.preprocessing import PolynomialFeatures  # 다중회귀

from sklearn.model_selection import train_test_split

from sklearn.neighbors import KNeighborsClassifier

from sklearn.linear_model import LinearRegression
from sklearn.linear_model import Ridge

from sklearn.linear_model import LogisticRegression

from sklearn.linear_model import SGDClassifier

from lightgbm import LGBMClassifier
```

<br>

```python
# 도움말
help(객체)
dir(객체)

# 결측치 처리
df['column'].fillna(0, inplace=True)

# 레이블 인코딩
le = LabelEncoder()
le.fit(df['column'])
df['column'] = le.transform(df['column'])

# 원-핫 인코딩
one-hot_df = pd.get_dummies(df['column'])
df = pd.concat(df, one-hot_df, axis=1)

# 정규화
ss = StandardScaler()
ss.fit(data)
data = ss.transform(data)

# 최소-최대 스케일링
ms = MinMaxScaler()
ms.fit(data)
data = ms.transform(data)

# 다중회귀
poly = PolynomialFeatures()
poly.fit(data)
data = poly.transform(data)

# 검증셋 만들기
x_train, x_test, y_train, y_test = train_test_split(data, target, test_size=0.2, stratify=target)
x_train.shape, x_val.shape, y_train.shape, y_val.shape

# 학습 예시
lr = LogisticRegression(C=20, max_iter=1000)
lr.fit(x_train, y_train)
print(lr.score(x_train, y_train))
print(lr.score(x_test, y_test))

proba = lr.predict_proba(x_test)
np.round(proba, decimals=3)

# 온라인 학습 예시
sc = SGDClassifier(loss='log', max_iter=10, random_state=42)
sc.fit(x_train, y_train)
print(sc.score(x_train, y_train))
print(sc.score(x_test, y_test))

sc.partial_fit(x_train, y_train)  # 1 에포크씩 이어서 훈련
print(sc.score(x_train, y_train))
print(sc.score(x_test, y_test))
```

