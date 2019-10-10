# 클라우드 컴퓨팅  

### nodemcu Basic Pracitce  

==== 오늘은 이론 없이 실기.(환경설정 테스트) ====  

- 1. 우리가 사용하는 공유기는 대소문자를 구분한다
- 2. https://www.arduino.cc/en/Reference/WiFi 와이파이 매뉴얼 확인..  
- 3. https://www.arduino.cc/en/Reference/WiFiServer 와이파이 서버 메뉴얼
- 4. https://www.arduino.cc/en/Reference/WiFiBegin 와이파이 비긴 메뉴얼
- 5. https://www.arduino.cc/en/Reference/WiFiLocalIP 와이파이 로컬아이피 메뉴얼



### Wifi.mode  
* WIFI_STA   
 다른 공유기에 접속해서 IP를 할당받고 HTTP 통신을 사용하는모드, 가장많이 사용되는 모드  
 * WIFI_AP  
 공유기처럼 여러 개의 WIFI모듈들이 접속할 수 있도록 해주는, 일종의 WIFI HUB모드로 근거리에 WIFI모듈들이 산재한 경우 이들을 WIFI네트웍으로 묶을 수 있다. 
 
 * WIFI_STA+WIFI_AP  
 앞선 두 가지 모드를 동시에 수행하는 모드로 와이파이 모듈을 따라서.
 
 
 ### wifi scan  
 ~~~~~~
 #include <ESP8266WiFi.h>

void setup() {

Serial.begin(115200);

WiFi.mode(WIFI_STA); // station mode
WiFi.disconnect(); //초기화 해줘야 된다?
delay(100); // 통신에서 딜레이는 아주 중요한 의미가 있음. 
            // 통신자체가 안정적이게끔 아주 작은 시간이지만 딜레이가 필요함.(시스템으로 되게 안정됨.)
Serial.println("Ready to scan..");
}

void loop() {
  Serial.println("scan start");
  int n = WiFi.scanNetworks(); // 와이파이 스캔 찾기.
  Serial.print("scan done"); //스캔완료 알기
  if(n == 0){ // 아무것도 없다.
    Serial.println("no networks found");
  }
  else{
    Serial.print(n);
    Serial.print("networks found");
    for (int i = 0; i < n; ++i){
      Serial.print(i + 1 );
      Serial.print(":");
      Serial.print(WiFi.SSID(i));
      Serial.print("(");
      Serial.print(WiFi.RSSI(i));
      Serial.print(")");
      Serial.println((WiFi.encryptionType(i) == ENC_TYPE_NONE) ? "": "*");
      delay(10);
    }
  }
  Serial.println("");
  delay(5000);
}
 ~~~~~~
 
 
