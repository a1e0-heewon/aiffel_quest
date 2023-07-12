# AIFFEL Campus Online 5th Code Peer Review
- 코더 : 서희원
- 리뷰어 : 황인준


# PRT(PeerReviewTemplate) 
각 항목을 스스로 확인하고 토의하여 작성한 코드에 적용합니다.

- [O] 코드가 정상적으로 동작하고 주어진 문제를 해결했나요?
  
- [O] 주석을 보고 작성자의 코드가 이해되었나요?
  > ```python
  > # 집의 총 크기, 재건축 여부, 방의 총 수, 지하실 여부, 평당 가격 변수 생성

  ```
- [O] 코드가 에러를 유발할 가능성이 없나요?
  >
- [O] 코드 작성자가 코드를 제대로 이해하고 작성했나요?
  >```python
  > # GridSearch  함수
      def GridSearchFunc(model, train, y, param_grid, verbose=2, n_jobs=5):
      # GridSearchCV 모델로 초기화
        grid_model = GridSearchCV(model, param_grid=param_grid, scoring='neg_mean_squared_error', \
                              cv=5, verbose=verbose, n_jobs=n_jobs)
    
        # 모델 fitting
        grid_model.fit(train, y)

        # 결과값 저장
        params = grid_model.cv_results_['params']
        score = grid_model.cv_results_['mean_test_score']
    
        # 데이터 프레임 생성
        results = pd.DataFrame(params)
        results['score'] = score
    
        # RMSLE 값 계산 후 정렬
        results['RMSLE'] = np.sqrt(-1 * results['score'])
        results = results.sort_values('RMSLE')

        return results

  ``` 
- [O] 코드가 간결한가요?
  > ```python
  >     # save_submission 함수
      def save_submission(model, train, y, test, model_name, rmsle=None):
        model.fit(train, y)
        prediction = model.predict(test)
        prediction = np.expm1(prediction)
        data_dir = os.getenv('HOME')+'/aiffel/kaggle_kakr_housing/data'
        submission_path = join(data_dir, 'sample_submission.csv')
        submission = pd.read_csv(submission_path)
        submission['price'] = prediction
        submission_csv_path = '{}/submission_{}_RMSLE_{}.csv'.format(data_dir, model_name, rmsle)
        submission.to_csv(submission_csv_path, index=False)
        print('{} saved!'.format(submission_csv_path))

    ```

# 예시
1. 코드의 작동 방식을 주석으로 기록합니다.
2. 코드의 작동 방식에 대한 개선 방법을 주석으로 기록합니다.
3. 참고한 링크 및 ChatGPT 프롬프트 명령어가 있다면 주석으로 남겨주세요.
```python

```

# 참고 링크 및 코드 개선
```python

```
