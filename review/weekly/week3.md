# Week 3 회고

Docker로 Hadoop Single-Node와 Multi-Node 클러스터를 만들고 HDFS와 YARN이 어떤 역할을 하는지 확인했다. 설정 파일을 수정하는 스크립트와 검증 스크립트를 작성했고, Python Streaming MapReduce로 Twitter 감성 분석을 구현했다. 이후 영화 평점 평균과 Amazon 리뷰 분석까지 진행하면서 Mapper와 Reducer가 입력을 Key-Value로 나눠 처리하는 흐름을 경험했다.

클러스터가 실행되는 것과 실제 job이 성공하는 것은 달랐다. 컨테이너 상태만 보지 않고 YARN 상태와 HDFS 결과까지 확인해야 했다. 설정 파일과 데이터 입력 형식이 조금만 달라도 실행이 실패해서, 작은 샘플로 먼저 확인하는 것이 중요했다.

아직 Hadoop 설정과 MapReduce 로직을 보자마자 전체 흐름이 그려지지는 않는다. 다음에는 설정 파일별 역할과 Mapper/Reducer의 입력·출력 형식을 표로 정리하고, 실행 로그를 읽는 연습을 더 하겠다.
