# Week 5 회고

Spark RDD와 DataFrame으로 같은 TLC 데이터를 처리하면서 두 API의 차이를 비교했다. RDD에서는 `map`, `filter`, `reduceByKey`로 정제와 일별 집계를 구현했고, DataFrame에서는 `select`, `filter`, `groupBy`, `join`으로 데이터를 처리했다. `count`, `collect`, `write`가 Transformation을 실제로 실행하는 Action이라는 점과, `persist`로 반복 계산을 줄이는 방식도 확인했다.

Spark UI에서 Job과 Stage를 보고 `explain()`으로 실행 계획을 확인하면서 코드가 작성된 순서와 실제 실행 순서가 다를 수 있다는 것을 알게 됐다. 다만 캐시나 파티션을 언제 적용해야 성능이 좋아지는지는 아직 경험이 부족하다. 실행 계획을 보는 것과 성능 문제의 원인을 판단하는 것은 별개의 일이라는 생각이 들었다.

다음에는 데이터 크기와 연산 종류에 따라 RDD와 DataFrame 중 무엇을 선택할지 근거를 적어보겠다. 최적화도 일단 적용하기보다 적용 전후의 Stage와 실행 시간을 비교하면서 확인하겠다.
