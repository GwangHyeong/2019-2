# 클라우드컴퓨팅  

## SPRI 이슈리포트 제2018-008호
### IT 페러다임 변화와 클라우드의 확산.
- 클라우드 컴퓨팅은 4차산업혁명의 핵심 기술 중 하나로 받으면서 글로벌 클라우드 시장은 급성장 추세.

### 왜 가상화 기술을 사용하는가?
- 클라우드 컴퓨팅이 처음 등장한 배경은 서비스 사업자들의 유후 컴퓨팅 자원의 재활용을 목적으로 시작됨.
- 하드웨어 장비를 가사오하하면 해당 장비가 제공하는 컴퓨팅 자원의 활용도를 높일 수 있게 된다.
- 사업자는 컴퓨팅자원 구매과 유지보수에 들어가는 비용을 절감할 수 있고, 사전에 환경을 구축하기 위한 공간 확보와 인력채용과 같은 고정비용도 절약할 수 있게 된다.

### 가상화 기술의 변화와 컨테이너 기반 기술의 부상
클라우드 컴퓨팅 환경을 구축하는 데에 있어서 시스템 환경에 대한 의존성이 없고, 경량화를 통한 속도 및 이식성 향상을 추구하는 컨테이너 기반의 가상화 기법이 널리 활용되고 있다.  
##### 컨테이너 기반 기술이란? - 알아보기

## 클라우드 컴퓨팅 가상화 기술.
### 2.1 가상화 기술의 개요  
* 가상화는 물리적인 컴퓨터 자원을 추상화 하며, 분산컴퓨팅 환경을 가능하게 함.  
* 가상화는 물리적인 컴포넌트를 논리적인 객체로 추상화 하는 것을 의미.

## 가상화의 종류
### 1. 서버 가상화
- 서버의 효율성을 올리기 위해 등장하였으며, 가상화 개념의 시초가 되는 역할을 한 가상화.  
### 2. 데스크톱 가상화  
- 데이터 센터의 서버에서 운영되는 가상의 PC환경을 의미.  
### 3. 어플리케이션 가상화
- 해당 응용프로그램이 실행되는 운영체제(OS)로부터 응용소프트웨어를 캡슐화 하는 기법.

## ===2.3 가상머신과 하이퍼바이저는 다음 시간에===


## Temperature & Humidity(온도 & 습도) 센서
* H/W spec. -> Vcc,GnD,Control(GPIO,D#);
* SW Design -> #include<.h>, lib

### 1. sensor출력
### 2. sensor with OLED
### 3. WEB control

* 저번시간에 했던 코드에 OLED 와 온습도 붙여서 사용.
~~~~~~
#include <ESP8266WiFi.h>
#include <SSD1306.h>

#include <DHT.h>
#define DHTPIN D6
#define DHTTYPE DHT11
#include <WiFiClient.h>
#include <ESP8266WebServer.h>

DHT dht(DHTPIN, DHTTYPE);
SSD1306 display(0x3c, D2, D1);



const char MAIN_page[] PROGMEM = R"=====(

<!doctype html>

<html>

<body>

<h2>Dept of Smartmedia</h2>

<h3>HTML Form ESP8266</h3>

<form action="/action_page">

Device name:<br>

<input type="text" name="device" value="LED"><br>

Control data:<br>

<input type="text" name="number" value="On/Off number"><br>

<input type="submit" name="Submit"><br>

</body>

</html>



)=====";



const char * ssid = "SMART324_3";
const char * password = "76543210";

ESP8266WebServer server(80);



int ledPin=D0;
int tones[] = {261, 294, 330, 349, 392, 440, 494, 523};
int numTones = 8;

void handleRoot(){

  String s=MAIN_page;

  server.send(200, "text/html",s);

}

void handleForm(){

  String device = server.arg("device");
  String number = server.arg("number");

  Serial.print("Debice:");
  Serial.println(device);


  Serial.print("Number:");
  Serial.println(number);
  
  Serial.print("num:");
  Serial.println(number);

  int num = number.toInt();



    String s ="<a href='/'>Go Back</a>";

    server.send(200,"text/html",s);

    }

  void setup(void){
    dht.begin();
    display.init();
    display.flipScreenVertically();
    display.clear();
    display.display();
    Serial.begin(115200);
    WiFi.begin(ssid,password);
    Serial.println("");
    while(WiFi.status() != WL_CONNECTED){
      delay(500);
      Serial.print(".");
    }
  Serial.println("");
  Serial.println("connected to");
  Serial.println("WiFi");
  Serial.println("IP address:");
  Serial.print(WiFi.localIP());


  server.on("/", handleRoot);

  server.on("/action_page", handleForm);

  server.begin();

  Serial.println("HTTP server started");

  }

  void loop(void) {

  server.handleClient();
 float temp = dht.readTemperature();
  float humidity = dht.readHumidity();

  
  Serial.print("Humidity:");
  Serial.print(humidity);
  Serial.print("Temperature:");
  Serial.print(temp);
  Serial.println("ºC");

  display.clear();

  display.setTextAlignment(TEXT_ALIGN_LEFT);
  display.setFont(ArialMT_Plain_10);
  display.drawString(0,20,"Temperature:");
  display.drawString(65,20,String(temp)+String("C"));
  display.drawString(0,40,"Humidity:");
  display.drawString(55,40,String(humidity)+String("%"));
  display.display();


  }
~~~~~~
