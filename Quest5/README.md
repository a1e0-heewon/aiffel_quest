# AIFFEL Campus Online 5th Code Peer Review
- 코더 : 서희원
- 리뷰어 : 김성진


# PRT(PeerReviewTemplate) 
각 항목을 스스로 확인하고 토의하여 작성한 코드에 적용합니다.

- [x] 코드가 정상적으로 동작하고 주어진 문제를 해결했나요?
  > Mecab을 사용할 수 없는 환경이라 코드 동작유무 확인은 못했지만,
  > 코드상으로는 주어진 문제를 해결했습니다.
- [x] 주석을 보고 작성자의 코드가 이해되었나요?
  > 네, 잘 이해되었습니다.
- [x] 코드가 에러를 유발할 가능성이 없나요?
  > 네, 없습니다.
- [x] 코드 작성자가 코드를 제대로 이해하고 작성했나요?
  > 네, 프로세스의 흐름상 이해한 것으로 판단됩니다.
- [x] 코드가 간결한가요?
  > 네, 코드의 흐름이 간결하며, 쉽게 파악이 됩니다.

- 문장 길이 분석으로 최대 길이 구하기

```python
total_data_text = list(X_train) + list(X_test)

# 텍스트 데이터 문장길이의 리스트를 생성
num_tokens = [len(tokens) for tokens in total_data_text]
num_tokens = np.array(num_tokens)

# 문장 길이의 평균값, 최대값, 표준편차를 계산해본다.
print("문장 길이의 평균 : ", np.mean(num_tokens))
print("문장 길이의 최대 : ", np.max(num_tokens))
print("문장 길이 표준 편차 : ", np.std(num_tokens))

# 예를들어, 최대 길이를 (평균 + 2*표준편차)로 한다면,
max_tokens = np.mean(num_tokens) +4*np.std(num_tokens)
maxlen = int(max_tokens)
print("pad_sequences maxlen : ", maxlen)
print("전체 문장의 {}%가 maxlen 설정값 이내에 포함됩니다.".format(np.sum(num_tokens<max_tokens)/len(num_tokens)))
```

- 우수한 결과값으로 문제를 해결

```python
1537/1537 - 3s - loss: 0.9565 - accuracy: 0.8228
[0.9564872980117798, 0.8227719068527222]
```

- loss, accuracy 그래프 분석

```python
acc = history_dict['accuracy']
val_acc = history_dict['val_accuracy']
loss = history_dict['loss']
val_loss = history_dict['val_loss']

epochs = range(1, len(acc) + 1)

# "bo"는 "파란색 점"입니다
plt.plot(epochs, loss, 'bo', label='Training loss')
# b는 "파란 실선"입니다
plt.plot(epochs, val_loss, 'b', label='Validation loss')
plt.title('Training and validation loss')
plt.xlabel('Epochs')
plt.ylabel('Loss')
plt.legend()

plt.show()
```

```python
plt.clf()   # 그림을 초기화합니다

plt.plot(epochs, acc, 'bo', label='Training acc')
plt.plot(epochs, val_acc, 'b', label='Validation acc')
plt.title('Training and validation accuracy')
plt.xlabel('Epochs')
plt.ylabel('Accuracy')
plt.legend()

plt.show()
```


# 참고 링크 및 코드 개선



# 회고

- 최대 문장 길이를 고려할 때, 평균/최대/편차값으로 정하는 부분이 큰 도움이 되었습니다.
- word2vec 모델 구성과 에러나는 부분에 대해 논의하였습니다.
- loss, accuracy 결과에는 토크나이저(mecab, okt..), 모델 구성(오히려 간단한 네트워크가 더 높은 성능을 내었음) 등이 영향을 줄 수 있음을 알게 되었습니다.
- 감사합니다.

