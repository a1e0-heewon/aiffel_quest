# AIFFEL Campus Online 5th Code Peer Review Templete
- 코더 : 서희원
- 리뷰어 : 조준규


# PRT(PeerReviewTemplate) 
각 항목을 스스로 확인하고 토의하여 작성한 코드에 적용합니다.

- [X] 코드가 정상적으로 동작하고 주어진 문제를 해결했나요?

- [X] 주석을 보고 작성자의 코드가 이해되었나요?
  > 코드마다 어떤 역할을 하는지 주석이 잘 적혀있어 이해하기 수월했다.
  
- [X] 코드가 에러를 유발할 가능성이 없나요?
  > 코드가 깔끔하게 작성되어 있어서 에러를 유발할 부분은 없는 것으로 보인다.
- [X] 코드 작성자가 코드를 제대로 이해하고 작성했나요?
  > 주석 등을 활용해 코드를 제대로 이해하고자 하는 노력을 보였다.  
  > 적재적소에 함수를 잘 사용한 것으로 보아 제대로 이해했다고 생각된다.
- [X] 코드가 간결한가요?
  > 코드가 군더더기 없이 깔끔하게 정리되어 있었고, 반복문과 함수를 사용하여 코드 길이를 최소화 하였다.

# 예시
1. 코드의 작동 방식을 주석으로 기록합니다.
2. 코드의 작동 방식에 대한 개선 방법을 주석으로 기록합니다.
3. 참고한 링크 및 ChatGPT 프롬프트 명령어가 있다면 주석으로 남겨주세요.
```python
# 코드 주석 예시
# Augmentation 적용
@tf.function()  # 빠른 텐서플로 연산을 위해 @tf.function()을 사용합니다.
def apply_augmentation(sketch, colored):
    # 이미지 합치기; 3채널의 이미지 두 개를 6채널의 이미지 하나로 합침
    stacked = tf.concat([sketch, colored], axis=-1)
    
    _pad = tf.constant([[30,30],[30,30],[0,0]])
    if tf.random.uniform(()) < .5:
        padded = tf.pad(stacked, _pad, "REFLECT")
    else:
        padded = tf.pad(stacked, _pad, "CONSTANT", constant_values=1.)
    # 50% 미만의 확률로 (if 부분) Reflection padding 적용
    # 반대의 경우엔 Constant padding 적용
    ## 위 두 내역은 padded에 반영됨

    # 이미지를 랜덤하게 자름(crop)
    out = image.random_crop(padded, size=[256, 256, 6])
    # 이미지를 좌우반전시킴
    out = image.random_flip_left_right(out)
    # 이미지를 상하반전시킴
    out = image.random_flip_up_down(out)
    
    if tf.random.uniform(()) < .5:
        # 이미지를 50% 미만 확률로 회전시킴(image.rot90)
        # k 인자는 회전 시 몇번 회전하였는가를 결정함
        degree = tf.random.uniform([], minval=1, maxval=4, dtype=tf.int32)
        out = image.rot90(out, k=degree)
    
    return out[...,:3], out[...,3:]
```
```python
# 코드 간결성 예시
  def call(self, x, y):
        # Block 통과한 출력값 out 초기화
        out = None
        # __init__()에서 쌓은 blocks를 local var로 가져와보자
        blocks = self.blocks

        # list인 blocks를 순회
        for idx_of_blocks in range(len(blocks)):
            if idx_of_blocks == 0:
                # blocks[0] == layers.Concatenate()
                out = blocks[idx_of_blocks]([x, y])
            else:
                out = blocks[idx_of_blocks](out)
        
        return self.sigmoid(out)
```

# 참고 링크 및 코드 개선
```python
# 조건이 n번째 까지와 이후가 다르기 때문에 초기값을 먼저 설정하고 조건마다 바꾸는 것도 방법입니다.
# none이 아닌 시작 값들로 초기화를 하면 다음과 같이 코드가 더 간결해질 수 있습니다.😊

# Discriminator __init__ 부분
    def __init__(self):
        super(Discriminator, self).__init__()
        
        filters = [64,128,256,512,1]
        self.blocks = [layers.Concatenate()]
        
        for i, f in enumerate(filters):
            stride, custom_pad, use_bn, act = 2, 0, 1, 1
            
            if i == 0 or i == 4:
                use_bn = 0
            if i > 2:
                stride, custom_pad = 1, 1
            if i > 3:
                act = 0
                
            self.blocks.append(DiscBlock(f, stride, custom_pad, use_bn, act))
         
        self.sigmoid = layers.Activation('sigmoid')
```
