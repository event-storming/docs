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


