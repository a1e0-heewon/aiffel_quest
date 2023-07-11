- 코더 : 서희원
- 리뷰어 : 최한준


# PRT(PeerReviewTemplate) 
각 항목을 스스로 확인하고 토의하여 작성한 코드에 적용합니다.

- [△] 코드가 정상적으로 동작하고 주어진 문제를 해결했나요?
  일부 코드만 수정하면 해결될 것 같습니다.
- [O] 주석을 보고 작성자의 코드가 이해되었나요?
  네
- [O] 코드가 에러를 유발할 가능성이 없나요?
  업습니다.
- [△] 코드 작성자가 코드를 제대로 이해하고 작성했나요?
  train/test split 시에 조금 헷갈려서 label을 train data에 포함시켰긴 하지만 괜찮을 것 같습니다.
- [O] 코드가 간결한가요?
  네 간결합니다.

# 예시
1. 코드의 작동 방식을 주석으로 기록합니다.
2. 코드의 작동 방식에 대한 개선 방법을 주석으로 기록합니다.
3. 참고한 링크 및 ChatGPT 프롬프트 명령어가 있다면 주석으로 남겨주세요.

# 참고 링크 및 코드 개선
```python
# 이 부분이 Data/label을 만들면서 train/test split도 진행하는 코드입니다.
# 그렇기에 Data 내부에는 label 그 자체가 들어가면 안되므로 
X = df.drop(['casual', 'registered', 'workingday'],axis=1)
# -> X = df.drop(['casual', 'registered', 'workingday', 'count'],axis=1)
# 로 수정하면 좋을 거 같습니다.
y = df['count']

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state=34)

print(X_train.shape, y_train.shape)
print(X_test.shape, y_test.shape)
```

```python
# 지금 하는 것은 학습 동향성 확인을 위한 코드이므로 label과 prediction 간의 차이를 나타내어야 합니다.
# 고로 y값에 대한 시각화도 포함되어야 합니다.
plt.figure(figsize=(15,4))

plt.subplot(1, 2, 1)
plt.scatter(X_test['temp'], predictions)
# 추가 :plt.scatter(X_test['temp'], y_test)

plt.subplot(1, 2, 2)
plt.scatter(X_test['humidity'], predictions)
# 추가 :plt.scatter(X_test['humidity'], y_test)
```