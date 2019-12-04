# 머신러닝  

### Logistic Regression Model의 또 다른 표현 방법
1. 입력 feature들의 선형결합  
2. 선형결합값의 비선형 변환  

### 연쇄법칙이란?  
* 합성함수의 미분은 합성 함수를 구성하는 각 함수의 미분의 곱으로 나타낼 수 있다.

![캡처](https://user-images.githubusercontent.com/54932560/70112714-9ee77e00-1699-11ea-93af-1d0ebc252cb9.PNG)

## 활성화 함수 계층 구현하기
### ReLU계층  

![캡처2](https://user-images.githubusercontent.com/54932560/70112786-e241ec80-1699-11ea-9703-02794cdb68f5.PNG)

### sigmod계층  
* 소실을 막기 위해 잘 안썼었음. (렐루 사용)
![캡처3](https://user-images.githubusercontent.com/54932560/70113629-24206200-169d-11ea-924b-81c246d95263.PNG)


## Backporpagation  
1. dataset구분 (Training , Test)  
2. y=f(z)  
3. b를 계산 -> Loss  
4. backpropagation (weight spdate) 


