## 카프카 설치
1. 다운로드  
https://kafka.apache.org/downloads  

2. 주키퍼 실행
bin/windows/zookeeper-server-start.bat config/zookeeper.properties

3. 카프카 실행
bin/windows/kafka-server-start.bat config/server.properties

## eventTopic 이라는 Topic 에 메세지 통신

1. publish  
bin/windows/kafka-console-produce.bat --broker-list http://34.85.73.178:31090 --topic eventTopic


2. consume  
bin/window/kafka-console-consumer.bat --bootstrap-server http://34.85.73.178:31090 --topic eventTopic --from-beginning


## 각 팀별로 event-storming 에 있는 프로젝트를 fork

## 각 팀별 개발 시작

## 템플릿 프로젝트는 주문이 발생하였을때 연관되어서 이벤트가 발생하도록 설계됨

http localhost:8081/orders productId=1 productName="TV" quantity=1 customerName="홍길동" customerAddr="서울시"  

