# m1_mtcars 데이터셋 분석하기
## 학습목표
mtcars 데이터셋을 분석하고 그래프를 그리는 방법을 배웁니다.
- Jupyter notebook의 기본 사용법을 배웁니다.
- pandas의 DataFrame의 기본 사용법을 배웁니다.
- matplotlib로 그래프를 그리는 방법을 배웁니다.

## 기능요구사항

- Jupyter notebook을 만드세요.
- 다음 DataFrame methods을 사용해서 데이터셋의 결과를 출력하세요.
  - head, tail
  - shape
    - shape method를 이용해서 데이터의 갯수 (row count)를 출력하세요.
  - columns : 데이터셋의 컬럼 중 이름이 없는 컬럼을 찾아서 적합한 이름으로 변경하세요.
  - info, dtypes
  - describe
- gear, transmission features에는 각각 몇가지 값이 있는지를 출력하세요.
- gear와 transmission의 경우의 수 조합별로 나누고 각 조합에 몇개의 차량이 있는지를 알아내세요.
  - 먼저 결과값을 화면에 출력하세요.
  - 결과값을 바 그래프로 그리세요. 타이틀은 '# of Cars by Gear x Transmission'로, x축 레이블은 '(Gear, Auto Transmission)', y축 레이블은 '# of Cars'로 만드세요.
- 모든 그래프는 Jupyter 노트북에 그려져야 합니다.
- 데이터셋에 포함된 모든 features의 히스토그램을 그리세요.
  - 그래프 타이틀은 "Histograms of Variables"로 하세요.
  - 최대한 잘 보이도록 그래프들을 배치하세요.
- Cylinder와 HorsePower 간의 상관 관계를 알아보기 위해 scatter 차트를 그리세요.
  - 그래프 타이틀은 "Cylinder vs Horse Power"로 하세요.
- MPG와 HorsePower 간의 상관 관계를 알아보기 위해 scatter 차트를 그리세요.
  - 그래프 타이틀은 "MPG vs Horse Power"로 하세요.
- 각 변수들 간의 상관 관계를 알아 보기 위해 상관계수를 구하는 표를 출력하세요.

## 프로그래밍 요구사항

- 데이터는 pandas 라이브러리의 DataFrame을 이용해서 처리합니다.
- 위의 기능적 요구사항을 수행할 때는 가급적 numpy는 사용하지 마세요.
- 그래프는 matplotlib 라이브러리를 이용하세요. (필요한 경우, 다른 라이브러리를 사용해도 됩니다.)
## gear x transmission 조합 구하기

- gear와 transmission의 경우의 수 조합별로 나누고 각 조합에 몇개의 차량이 있는지를 알아낼 때
  1)pandas.crosstab method를 사용하는 방법과 2)사용하지 않는 방법, 2가지 모두의 결과값을 각각 출력해야 합니다.


