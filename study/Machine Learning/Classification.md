# 분류

> 분류 : 지도 학습 중 클래스 예측

<br>

## MNIST

> 손으로 쓴 숫자 이미지

* 이미지 데이터 가져오기

```python
from sklearn.datasets import fetch_openml

mnist = fetch_openml('mnist_784', version=1)  # 가끔 불러오는데 오류뜸
mnist.keys()  # 자료 목록 확인
## dict_keys(['data', 'target', 'frame', 'categories', 'feature_names', 
##            'target_names', 'DESCR', 'details', 'url'])

# 데이터, 라벨 구분
X, y = mnist['data'], mnist['target']
X.shape, y.shape
```

<br>

* 이미지 데이터 샘플 확인

```python
import matplotlib as mpl
import matplotlib.pyplot as plt

example = X[0]
example_image = example.reshape(28, 28)  # 28 x 28 배열로 변경

plt.imshow(example_image, cmap='binary')
plt.axis('off')
plt.show()
```

![image-20210217141335953](/Users/ocial/Library/Application Support/typora-user-images/image-20210217141335953.png)

<br>

* 훈련 세트, 테스트 세트 구분

```python
y[0]  # 레이블 확인
## '5'

y = y.astype(np.uint8)  # 문자열을 정수로 변환

X_train, X_test, y_train, y_test = X[:60000], X[60000:], y[:60000], y[60000:]
```

<br>

* 이진 분류기 훈련

```python
y_train_5 = (y_train == 5)  # 5는 True고, 다른 숫자는 모두 False
y_test_5 = (y_test == 5)

from sklearn.linear_model import SGDClassifier  # 확률적 경사 하강법(SGD), 큰 데이터셋 효율적으로 처리, 온라인 학습 굿

sgd_clf = SGDClassifier(random_state=42)
sgd_clf.fit(X_train, y_train_5)
```

<br>

* 교차 검증 구현

```python
from sklearn.model_selection import StratifiedKFold
from sklearn.base import clone  # 모델 복사

skfolds = StratifiedKFold(n_splits=3, random_state=42, shuffle=True)

for train_index, test_index in skfolds.split(X_train, y_train_5):
    clone_clf = clone(sgd_clf)
    
    # 훈련 세트의 일부를 떼어내어 검증 세트로 구분
    X_train_folds = X_train[train_index]
    y_train_folds = y_train_5[train_index]
    X_valid_folds = X_train[test_index]
    y_valid_folds = y_train_5[test_index]
    
    clone_clf.fit(X_train_folds, y_train_folds)
    y_pred = clone_clf.predict(X_valid_folds)
    n_correct = sum(y_pred == y_valid_folds)
    print(n_correct / len(y_pred))
```

<br>

* 교차 검증을 사용한 정확도 측정

```python
# cross_val_score는 내부적을 StratifiedKFold 을 사용함
from sklearn.model_selection import cross_val_score

cross_val_score(sgd_clf, X_train, y_train_5, cv=3, scoring='accuracy')
```

<br>



