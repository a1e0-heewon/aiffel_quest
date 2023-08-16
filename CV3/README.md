# AIFFEL Campus Online 5th Code Peer Review Templete
- 코더 : 서희원
- 리뷰어 : 최연석


# PRT(PeerReviewTemplate) 
각 항목을 스스로 확인하고 토의하여 작성한 코드에 적용합니다.

- [-] 코드가 정상적으로 동작하고 주어진 문제를 해결했나요?
  > 34plain, 50plain 모델이 작동하지 않습니다.
- [-] 주석을 보고 작성자의 코드가 이해되었나요?
  > 주석이 작성되지 않았습니다.
- [-] 코드가 에러를 유발할 가능성이 없나요?
  > 모델 학습 중에 발생하는 오류인 것으로 보아 데이터 전처리에 문제가 있을 것으로 예상됩니다.
  > 모델 전처리 및 학습 코드가 없습니다.
- [X] 코드 작성자가 코드를 제대로 이해하고 작성했나요?
  > 구동하는 모델의 작동 및 설명에 대해 충분히 이해하여 모델을 작성 했음을 알 수 있었습니다.
- [X] 코드가 간결한가요?
  > 모델 블럭을 function으로 구분하여 간결하게 작성 하엿습니다.
  '''
  def build_resnet_block(input_layer, block_num, cnn, channel, strides, not_plain=True, is_50=False):
  def build_resnet(input_shape, is_50=False, not_plain = True):
  '''

# 참고 링크 및 코드 개선
```python
#cat_vs_dog 데이터의 image resize를 test 해보시는 것도 좋다고 생각됩니다.
```
