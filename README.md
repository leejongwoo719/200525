1. 앱인벤터_디자이너 파트
1)수평배치
목록버튼: 블루투스 검색+연결
버튼: 블루투스 해제
레이블: 연결정보 확인
2) 수직배치
레이블 3,4: 빈칸 삽입
버튼: LED ON,OFF기능
블루투스 클라이언트:
블루투스 기능을 사용

2.앱인벤터_블록코딩파트
1) 블루투스 선택 전,후에
블루투스 기능을
사용하기 위한 블록코딩
2)버튼_연결해제를 클릭
블루투스 연결을 끊음
3)전송하기 함수
텍스트 형식의 신호를
핸드폰에서 아두이노 UNO 모듈로 전송
4) 블루투스 선택 전,후에
블루투스 기능을
사용하기 위한 블록코딩
5)버튼_연결해제를 클릭
블루투스 연결을 끊음
6)전송하기 함수
텍스트 형식의 신호를
핸드폰에서 아두이노
UNO 모듈로 전송

3.결선도

UNO의 POWER 파트의
5V를 브래드보드의 (+)로
GND를 (-)로 사용
1)블루투스 모듈(HC-06)
RXD-> UNO 12번 핀 결선
TXD-> UNO 11번 핀 결선
VCC-> 브래드보드 (+)
GND-> 브래드보드 (-)
2)LED
GND부분은 브래드보드의
(-)부분과 연결
VCC부분은 저항(220Ω)을
직렬로, UNO의 3번 핀으로
입력(5V)를 받음

4. 아두이노 스케치코드
#include<SoftwareSerial.h>
const int LED = 3;	//3번으로 신호출력
char data = 0;

SoftwareSerial BTSerial(11,12);

void setup() {
Serial.begin(9600);
BTSerial.begin(9600);
pinMode(LED,OUTPUT);
}
void loop() {
if (BTSerial.available()){
data = BTSerial.read();
Serial.write(data);
switch(data)
{
 case '1' : digitalWrite(LED, HIGH); break; 
//1을 받으면 LED 점등
 case ‘2' : digitalWrite(LED, LOW); break;
//2를 받으면 LED 점등
}
}
if (Serial.available())
 BTSerial.write(Serial.read());
delay(1);
}
