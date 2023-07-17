# AIFFEL Campus Online 5th Code Peer Review
- 코더 : 서희원
- 리뷰어 : 홍서이


# PRT(PeerReviewTemplate) 
각 항목을 스스로 확인하고 토의하여 작성한 코드에 적용합니다.

- [O] 코드가 정상적으로 동작하고 주어진 문제를 해결했나요?
  > 정상적으로 동작하고 문제를 해결하였다. segmentation에서의 문제점도 잘 파악하였다.
- [O] 주석을 보고 작성자의 코드가 이해되었나요?
  > 새롭게 등장한 함수에 대해 주석을 달아 쉽게 이해할 수 있도록 하였다.

  ```Python
  # np.where(조건, 참일때, 거짓일때)
  # 세그멘테이션 마스크가 255인 부분만 원본 이미지 값을 가지고 오고 
  # 아닌 영역은 블러된 이미지 값을 사용합니다.
  img_concat = np.where(img_mask_color==255, img_orig, img_bg_blur)
  # plt.imshow(): 저장된 데이터를 이미지의 형식으로 표시한다.
  # cv2.cvtColor(입력 이미지, 색상 변환 코드): 입력 이미지의 색상 채널을 변경
  # cv2.COLOR_BGR2RGB: 원본이 BGR 순서로 픽셀을 읽다보니 
  # 이미지 색상 채널을 변경해야함 (BGR 형식을 RGB 형식으로 변경)
  plt.imshow(cv2.cvtColor(img_concat, cv2.  COLOR_BGR2RGB))
  plt.show()
  ```

- [O] 코드가 에러를 유발할 가능성이 없나요?
  > 없다.
- [O] 코드 작성자가 코드를 제대로 이해하고 작성했나요?
  > image segmentation을 하기 위한 코드를 제대로 작성하였다.
- [O] 코드가 간결한가요?
  > 간결하게 필요한 코드만 작성하였다

# 참고 링크 및 코드 개선
# 회고
