# 6.맵리듀스_개념_및_동작방식

> 맵리듀스(MapReduce)

```
1999 ~ 2005년 수행 방식
초창기 google에서 HDFS에 데이터를 저장한 후
데이터를 가지고 작업을 하기위해 고안을 함.
두 단개로 나눠 계산을 수행
fork-join(큰 작업을 나눠서 수행하는 방식)
각 block 단위로 연산해서 하나로 합치는 과정
ex) 단어 카운트 -> 각 블럭별로 count를 계산해서 합쳐나감
맵 -> 리듀스 -(write)> 맵 -> 리듀스 -(write)>..... (계속 작업을 수행)
     - 맵(Map)
 각 블럭별로 계산을 수행 
 
     - 리듀스(ReducE)
맵에서 계산한 작업을 합치는 작업     
수행한 작업을 write

Map과 Reduce 사이에는 shuffle과 sort라는 스테이지가 있음 
```

> 맵리듀스 JobTracker

```
맵리듀스 Job들은 JobTracker라는 소프퉤어 데몬에 의해 제어됨.
JobTracker는 Master Node에 있음.

각각의 slave node 에는 task tracker가 있음 

Map의 모든작업이 끝나야 Reduce가 가능하다.
(많은 노드의 작업이 끝나도 특정 노드가 늦게 긑나면 모두 기다려야 작업 가능)

Job 은 Full program
task 는 map, reduce 두개로 나눠서 구별
task attempt는 Task를 실행하기 위한 특정 인스턴스 

    - 맵퍼는 Key/Value 쌍의 형태로 데이터를 읽는다.
key 값은 파일명 or 라인번호 등의 고유값
    - 맵퍼의 0개 또는 그 이상의 Key/Value 상을 출력한다.
map(in_key, in_value) -output> (inter_key, inter_value)list
- 입력은 key value 출력은 key value의 리스트
```


















