## 카프카 설치
1. 다운로드  
https://kafka.apache.org/downloads  

2. 주키퍼 실행
bin/windows/zookeeper-server-start.bat config/zookeeper.properties

3. 카프카 실행
bin/windows/kafka-server-start.bat config/server.properties

## eventTopic 이라는 Topic 에 메세지 통신

1. publish  

---- window   
bin/windows/kafka-console-produce.bat --broker-list http://34.85.73.178:31090 --topic eventTopic

---- mac  
/usr/local/bin/kafka-console-producer --broker-list http://34.85.73.178:31090 --topic eventTopic


2. consume  

---- window   
bin/window/kafka-console-consumer.bat --bootstrap-server http://34.85.73.178:31090 --topic eventTopic --from-beginning


---- mac  
/usr/local/bin/kafka-console-consumer --bootstrap-server http://34.85.73.178:31090 --topic eventTopic --from-beginning

## 이벤트 발송 시나리오


주문이 발생함 – order  
배송 시작됨 – delivery  
배송 완료됨 – delivery  
고객 설문조사 완료됨 – marketing  
추가 물량이 필요함 - service_center  
상품이 입고됨 - products  


## 팀별 이벤트 발송

```
{"type":"OrderPlaced","stateMessage":"주문이 들어옴","productId":1,"orderId":2,"productName":"TV","quantity":1,"price":0,"customerName":"홍길동","customerAddr":"서울시"}

{"type":"DeliveryStarted","stateMessage":"배송이 시작됨","deliveryId":1,"orderId":2,"customerName":"홍길동","deliveryAddress":"서울시","deliveryState":"DeliveryStarted"}
{"type":"DeliveryCompleted","stateMessage":"배송이 완료됨","deliveryId":1,"orderId":2,"customerName":"홍길동","deliveryAddress":"서울시","deliveryState":"DeliveryCompleted"}

{"type":"SurveyCompleted","stateMessage":"설문이 완료됨","customerName":"홍길동","surveyMessage":"넉넉하게 수량 챙겨주세요"}

{"type":"ProductRequired","stateMessage":"추가 물량이 필요함","productName":"리모콘"}

{"type":"ProductChanged","stateMessage":"상품 변경이 발생함","productId":1,"productName":"리모콘","productPrice":10000,"productStock":21}

```

## 각 팀별로 event-storming 에 있는 프로젝트를 fork

1. 상품개발팀 같은 경우 event-storming/product 프로젝트에 들어가서 오른쪽 상단의 Fork 버튼 클릭

2. IDE 환경에서 해당 git 소스코드를 clone 받아서 개발 함

```
git clone https://github.com/event-storming/[username]/products.git
```


## 템플릿 프로젝트는 주문이 발생하였을때 연관되어서 이벤트가 발생하도록 설계됨

http localhost:8081/orders productId=1 productName="TV" quantity=1 customerName="홍길동" customerAddr="서울시"  

