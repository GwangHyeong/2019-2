# 클라우드 컴퓨팅  

### Web server  

* 웹서버 : 클라이언트가 웹 브라우저에게 서버에 페이지 요청을 하면 웹 서버에서 요청을 받아 정적 페이지을 제공하는 서버.
* 대표적인 웹 서버 : 아파치 nginx와 windows전용 웹 서버인 iis 
* WAS : HTML만으로 할수 없는 데이터베이스 조회나 다양한 로직 처리 같은 동적인 컨텐츠를 제공하기 위해 만들어진 애플리케이션 서버.
* 대표적인WAS : TOMCAT,JEUE,JBoss,WenSphere

* 클라이언트가 전송할 데이터를 ESP IP 주소로 입력하여 웹 페이지를 요청하면 서브 루틴에 의해 처리되고 서브 루틴 이름은, SEVER.ON에 정의
* server.on("/",handleRoot);    //Which routine to handle at root location  
* server.on("/",root);          //root location  
* server.on("/page1",First_page); // this is first page location  
* server.on("/page2",Second_page); //this is second page location  

### MDNS    
mdns.begin ('esp8266')을 지정하면 mDNS서버가 ESP8266이라는 이름으로 정의된다. 잘 작동하는 경우 mdns.begin 함수는 true를 반환하고 server.begin()을 사용하여 서버를 시작할 수 있따.


### index.h

* PROGMEM : 플래시 프로그램 메모리 영역에 데이터를 저장하기 위한 자료형 변경자.
* 데이터가 상수임을 CONST예약어를 사용  
* const char MAIN_page[] PROGMEM = R"=====(......)=====";  
* 기본적으로 두 구분 기호 'R " ===== ('및') ===== "' 사이의 모든 것은 특수문자 또는 변수가 들어감.  
* Basically everything between the two delimiters

### ESP8266WiFi.h 
연결 ap등과 같은 모든 WiFi 관련 기능 수행.

### WiFiClient.h
웹 브라우저에 요청 수행. 

### esp8266webserver.h
http프로토콜 수행

# ===실습 코드 돌려보고 led on_off 서버온 으로 바꾸기.===

ESP8266 웹 서버2
~~~~~~
#include <ESP8266WiFi.h>
#include <WiFiClient.h>
#include <ESP8266WebServer.h>
#include "index.h"

//
const char* ssid = "SMART324_3";
const char* password = "76543210";

ESP8266WebServer server(80);

void handleRoot() {
  String s = MAIN_page;
  server.send(200, "text/html", s);
  
}

void setup() {
  Serial.begin(9600);
  WiFi.begin(ssid,password);
  Serial.println("");

  while (WiFi.status() != WL_CONNECTED){
    delay(500);
    Serial.print(".");
  }
  Serial.println();
  Serial.println();
  Serial.print("Connecting to ");
  Serial.println(ssid);
  Serial.print("IP address : ");
  Serial.println(WiFi.localIP());

  server.on("/",handleRoot);
  server.begin();
  Serial.println("http start");

  
}

void loop() {
  // put your main code here, to run repeatedly:
  server.handleClient();
}
~~~~~~
