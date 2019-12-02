# 머신러닝

## regression

~~~~~~
  * KNN  
 
                             ┌ ---- Logit Regression
  선형구분,선형예측  * Regression ---- Ridge Regression
                             └------ Lasso Regression
        
        
  * suooprt vector machine (svm)
 
  * Tree ---- Decision tree
             └------ Random Forest
  
  * PCA
  
  ~~~~~~
  
  * 기본으로 시작.
  Regression -> LogitRegression -> Perceptron -> Muilt.layer perceptron(비선형) -> Depp Neural NetWork (=Artificiil Neural Network) 
  
  ![캡처](https://user-images.githubusercontent.com/54932560/69934264-c82ad180-1514-11ea-9a0c-93052f7ba57b.PNG)
  
  
  ## K - Nearest neighbor 
  
  * 거리에따라..? 측정..?
  * 거리에 따른 인접성을 측정. 홀수로만 측정(k) 
  
  1. 분류할 관측치 x선택  
  2. x로부터 인접한 k 찾기.  
  3. 인접한k 를 기준으로 측정.  
  4. k 여러개일 경우 평균값으로 예측한다.  
  
  
  k 값이 작으면 과대적합.(복잡)  
  k 값이 크면 과소적합.(단순)  

![800px-KnnClassification svg](https://user-images.githubusercontent.com/54932560/69935147-5c963380-1517-11ea-8299-ee5e15b25e8b.png)  
검증 표본(초록색 원)은 첫 번째 파랑 네모의 항목이나 빨강 삼각형의 두 번째 항목으로 분류되어야 한다. 만약 “k = 3” (실선으로 그려진 원)이면 두 번째 항목으로 할당되어야 한다. 왜냐하면 2개의 삼각형과 1개의 사각형만이 안쪽 원 안에 있기 때문이다. 만약 “k = 5” (점선으로 그려진 원)이면 첫 번째 항목으로 분류되어야 한다. (바깥쪽 원 안에 있는 3개의 사각형 vs. 2개의 삼각형).
  

## SVM(Support Vector Machine)  
* 2개의 클래스가 있을 때 특정 점이 어느 클래스 속하는지를 결정하는 문제.
* 한차원 낮은 차원으로 W와b를 찾는 문제.

![캡처](https://user-images.githubusercontent.com/54932560/69935368-fe1d8500-1517-11ea-85f2-a99ba3705e00.PNG)

![캡처2](https://user-images.githubusercontent.com/54932560/69935413-26a57f00-1518-11ea-9ff1-47a26978584f.PNG)

* 데이터가 많아도 그중에 몇개만 사용해서 결과를 결정. 속도가 빠름  

### 소프트마진svm - 몇개는 틀려도 괜찮은..  
### 하드마진svm - 하나도 틀리는거 없이...  

* SVM은 SCALE에 민감하기때문에 정규화(Normalization) 꼭 해줘야함..!  


## Decision Tree
* 조건을주고 True or False . 
* greedy serch 를 사용. greedy하면 속도가 엄청 늦어지지만, 카테고리가 적기때문에 greedy serch를 쓴다.


![캡처3](https://user-images.githubusercontent.com/54932560/69936195-6c634700-151a-11ea-8862-2036bca2b594.PNG)
