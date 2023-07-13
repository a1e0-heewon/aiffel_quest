# AIFFEL Campus Online 5th Code Peer Review
- 코더 : 서희원
- 리뷰어 : 황인준


# PRT(PeerReviewTemplate) 
각 항목을 스스로 확인하고 토의하여 작성한 코드에 적용합니다.

- [O] 코드가 정상적으로 동작하고 주어진 문제를 해결했나요?
  > 문제를 잘 해결했고, 각도가 약간 틀어진 얼굴에서도 랜드마크가 동작하는것을 확인,
  > 문제인식 및 이후에 수행할만한 목표 또한 제시했다.
- [O] 주석을 보고 작성자의 코드가 이해되었나요?
  > 스티커의 흰 바탕을 대체하는 방법에 대해서 잘 설명했다.
  ```python
       # 스티커와 이미지를 합친다
      img_show_ = img_show.copy()

      # 이미지 합성을 위해서 스티커가 들어갈 부분을 crop한 이미지를 구한다.
      sticker_area = img_show_[refined_y:refined_y+cat_sticker.shape[0], refined_x:refined_x+cat_sticker.shape[1]]

      # 스티커가 들어갈 위치에 스티커에서 255 인 부분 즉 흰색인 부분을 모두 crop 한 이미지로 대체한다.
      img_show_[refined_y:refined_y+cat_sticker.shape[0], refined_x:refined_x+cat_sticker.shape[1]] = \
      np.where(cat_sticker==255,sticker_area,cat_sticker).astype(np.uint8)
  ```
- [O] 코드가 에러를 유발할 가능성이 없나요?

  > 모듈화를 통해 혹여 발생할 에러에도 대응이 가능하게끔 만들었다
- ```python
  # 다양한 이미지 테스트를 위한 위 과정 모듈화
    def find_face(path):
      face = cv2.imread(path)
    
      dlib_rects = bounding_box_(face)
      landmarks = find_landmark_(face, dlib_rects)
    
      if(len(landmarks) == 0):
        print("error: cant find face")
        return 0

      img_show = sticker_set_(face, dlib_rects, landmarks)
      plt.imshow(cv2.cvtColor(img_show, cv2.COLOR_BGR2RGB))
      plt.show()
    
      return(img_show)
  ```
- [O] 코드 작성자가 코드를 제대로 이해하고 작성했나요?
  > 마지막 마크다운에 추가적인 이미지를 통해 테스트를 진행했고, 결과 분석 및 이후 방향을 제시한 것으로 보아 코드를 이해하고
  > 있음을 알 수 있다
- [O] 코드가 간결한가요?
  > 주피터 노트북이기때문에 셀 별로 코드 동작상황을 볼 수 있고, 추가적으로 모듈화를 해서 코드의 역할도 쉽게 알 수 있다.



# 참고 링크 및 코드 개선
> 이미지의 기하학적 변형과 관련된 문서가 있으니 살펴 보는것도 좋을것 같다
> 'https://opencv-python.readthedocs.io/en/latest/doc/10.imageTransformation/imageTransformation.html'
