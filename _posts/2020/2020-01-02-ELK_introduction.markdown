---
layout: post
title: "1. introduction"
date: 2020-01-02 19:20:23 +0900
category: ELK
---

# session 1 환경 구축

ELK 스택(ElasticSearch, Logstash Kibana)으로 데이터 분석

도커 우분투 환경에서 진행

	- ElasticSearch install
1. java Install
sudo add-apt-repository –y ppa:webupd8team/java
sudo apt-get update
sudo apt-get -y install aracle-java8-installer
java –version
* 에러 발생 
<img src="/img/elk/error1.PNG" width="350px" height="300px"></img> <br>

-> 위가 강의내용이나 되지않아 다른 방식으로 진행
apt-get install openjdk-8-jdk

2. 엘라스틱서치 설치 
* 이번에도 강의와 다른방식으로 설치 진행
https://www.elastic.co/kr/downloads/elasticsearch -> 여기에서 찾아보고 wget으로 다운로드
*강의와 같은 버전을 맞춰서 설치 (사용 X)
wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-6.5.1.deb
dpkg -i elasticsearch-5.1.1.deb
* 최신 버전 정리를 위해 2020-01-15를 기준으로 최신버전 설치 
https://www.elastic.co/kr/downloads/elasticsearch 에서 검색 최신버전 찾기 <br>
<br>
```
간편 설치 
apt-get install elasticsearch -y
sed -i 's/#START_DAEMON/START_DAEMON/' /etc/default/elasticsearch
/usr/share/elasticsearch/bin/elasticsearch &
-> 에러 발생
can not run elasticsearch as root
-> 해결책 el 계정 만든후 관리자 권한 주고 java까지 전부 다시 셋팅
useradd el
chown -R el:el /etc/sysconfig/elasticsearch
chown -R el:el /usr/share/elasticsearch/
chown -R  el:el  /etc/elasticsearch/
chown -R  el:el /var/log/elasticsearch/
chown -R  el:el /var/lib/elasticsearch/
/usr/share/elasticsearch/bin/elasticsearch &

```

> 설치 설명 추가
```
apt-get install elasticsearch
위 명령어 하나로도 가능 
+ 루트권한 실행시 --allow-root 로 가능
    - 서비스 시작 방법
#엘라스틱서치 서비스 등록
systemctl enable elasticsearch.service
# 서비스 실행 status로 상태확인 가능
service elasticsearch start
```


