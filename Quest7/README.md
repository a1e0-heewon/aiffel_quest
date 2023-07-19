# AIFFEL Campus Online 5th Code Peer Review Templete
- 코더 : 서희원
- 리뷰어 : 홍수정


# PRT(PeerReviewTemplate) 
각 항목을 스스로 확인하고 토의하여 작성한 코드에 적용합니다.

- [] 코드가 정상적으로 동작하고 주어진 문제를 해결했나요?
  > 분석단계, 정제단계, 정규화와 불용어 제거, 데이터셋 분리, 인코딩 과정등을 순서대로 진행하고 로스가 지수적으로 감소하는 것을 확인함.
  > 두 요약 결과를 문법완성도 측면과 핵심단어 포함 측면으로 나누어 비교하고 분석 결과를 표로 정리하여 제시하지는 못함.
- [X] 주석을 보고 작성자의 코드가 이해되었나요?
  > 위 항목에 대한 근거 작성 필수
- [X] 코드가 에러를 유발할 가능성이 없나요?
  > 에러가 날 수 있는 부분은 거의 없다고 보이며 특정 상황에 대해서는 if문 처리하여 진행해 불필요한 코드 진행을 방지
  ```
      if (i!=0): 
        temp = temp + src_index_to_word[i]+' '
  ```
- [X] 코드 작성자가 코드를 제대로 이해하고 작성했나요?
  > 분석 단계가 순차적으로 진행되며 tqdm 등의 활용으로 프로젝트 진행 정도를 가시적으로 표현함
```
for sentence in tqdm(data['text'], desc="text컬럼 전처리.."):
    clean_text.append(preprocess_sentence(sentence, remove_stopwords=True))
```
- [X] 코드가 간결한가요?
  > 반복적으로 사용되는 기능을 함수화하여 코드가 무작위로 반복되는 것을 피함

# 예시
1. 코드의 작동 방식을 주석으로 기록합니다.
2. 코드의 작동 방식에 대한 개선 방법을 주석으로 기록합니다.
3. 참고한 링크 및 ChatGPT 프롬프트 명령어가 있다면 주석으로 남겨주세요.
```python
# 사칙 연산 계산기
class calculator:
    # 예) init의 역할과 각 매서드의 의미를 서술
    def __init__(self, first, second):
        self.first = first
        self.second = second
    
    # 예) 덧셈과 연산 작동 방식에 대한 서술
    def add(self):
        result = self.first + self.second
        return result

a = float(input('첫번째 값을 입력하세요.')) 
b = float(input('두번째 값을 입력하세요.')) 
c = calculator(a, b)
print('덧셈', c.add()) 
```

# 참고 링크 및 코드 개선
```python
# 코드 리뷰 시 참고한 링크가 있다면 링크와 간략한 설명을 첨부합니다.
# 코드 리뷰를 통해 개선한 코드가 있다면 코드와 간략한 설명을 첨부합니다.
```
