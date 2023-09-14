# AIFFEL Campus Online Code Peer Review Templete
- 코더 : 서희원
- 리뷰어 : 조준규


# PRT(Peer Review Template)
- [X]  **1. 주어진 문제를 해결하는 완성된 코드가 제출되었나요?**
    - widerface dataset의 전처리가 온전히 이루어졌다.
    - SSD를 활용한 얼굴 인식을 온전히 수행하였다.
```python
TEST_IMAGE_PATH = os.path.join(PROJECT_PATH, 'image.png')

img_raw = cv2.imread(TEST_IMAGE_PATH)
img_raw = cv2.resize(img_raw, (IMAGE_WIDTH, IMAGE_HEIGHT))
img = np.float32(img_raw.copy())

img = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
img, pad_params = pad_input_image(img, max_steps=max(BOX_STEPS))
img = img / 255.0

boxes = default_box()
boxes = tf.cast(boxes, tf.float32)

predictions = model.predict(img[np.newaxis, ...])

pred_boxes, labels, scores = parse_predict(predictions, boxes)
pred_boxes = recover_pad(pred_boxes, pad_params)

for box_index in range(len(pred_boxes)):
    draw_box_on_face(img_raw, pred_boxes, labels, scores, box_index, IMAGE_LABELS)

plt.imshow(cv2.cvtColor(img_raw, cv2.COLOR_BGR2RGB))
plt.show()
```

- [X]  **2. 전체 코드에서 가장 핵심적이거나 가장 복잡하고 이해하기 어려운 부분에 작성된 
  주석 또는 doc string을 보고 해당 코드가 잘 이해되었나요?**
    - 코드블록 별로 코드의 설명이 적혀 있어 이해하기 수월했다.
```
TFRecord
TFRecord는 TensorFlow만의 학습 데이터 저장 포맷으로, 이진(binary) 레코드의 시퀀스를 저장한다. TFRecord 형태의 학습 데이터를 사용하여 모델 학습을 하면 학습 속도가 개선되기 때문에 데이터셋의 처리 속도 향상을 위해 TFRecord 데이터셋으로 변환하는 과정이다.
```
  
- [ ]  **3. 에러가 난 부분을 디버깅하여 문제를 “해결한 기록을 남겼거나” 
  ”새로운 시도 또는 추가 실험을 수행”해봤나요?**
    - 추가 실험이 따로 진행된 것 같지는 않았다.

- [X]  **4. 회고를 잘 작성했나요?**
    - 성능이 잘 나타나지 않은 부분에 대해 고찰한 부분이 잘 나타나있다.
```
회고
30 epoch으로 학습을 돌렸지만 이상한 부분을 잡는 경우도 있고 얼굴을 잡지 못하는 경우도 있어 100 epoch 정도로 돌려 성능을 확인해봐야할 것 같다.
```
    
- [X]  **5. 코드가 간결하고 효율적인가요?**
    - 함수화를 통해 각 코드가 효율적으로 돌아가도록 작성하였다.
```python
# 함수 하나로 이미지에 스티커를 붙일 수 있도록 함
img_result = put_sticker_on_face(os.path.join(PROJECT_PATH, 'image.png'))
plt.imshow(cv2.cvtColor(img_result, cv2.COLOR_BGR2RGB))
plt.show()
```
    
# 참고 링크 및 코드 개선
```python
# import 문제로 스티커 붙인 모습이 나타나진 않았는데 업데이트 되면 좋겠습니다.😊
# 100 epoch 돌린 결과랑 같이 비교하는 것도 좋을 것 같네요 ㅎㅎ
```
