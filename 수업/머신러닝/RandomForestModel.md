# 머신러닝  

## RandomForestModel
  많은양의 데이터중 랜덤으로 뽑아 트리 작성.  

## 앙상블
* 앙상블이란 여려 개의 weak learners들의 Prediction결과를 Voting는 평균을 이용해 예측정확성 확장.  


![캡처](https://user-images.githubusercontent.com/54932560/70115632-af045b00-16a3-11ea-83c6-873e44eb76f7.PNG)

* 여려개의 Training Dataset을 생성하여 각 Dataset별로 Decision Tree Model 구축  
-> Bagging

* Decision Tree Model 구축시 feature변수 무작위 선택  


## Random Subspace
![캡처2](https://user-images.githubusercontent.com/54932560/70116020-d871b680-16a4-11ea-83b5-e0c35125763a.PNG)  

### Bootstrap
여러개의 레이어를 만들어서 하는 앙상블 방법중 하나.  

