# predixy-redis-cluster

##### 레디스(redis-net) 네트워크 생성
```
docker network create --gateway 172.24.0.1 --subnet 172.24.0.0/16 redis-net
```

#### 레디스 정보
```
$ docker exec -it node1 redis-cli cluster info
cluster_state:ok
cluster_slots_assigned:16384
cluster_slots_ok:16384
cluster_slots_pfail:0
cluster_slots_fail:0
cluster_known_nodes:6
cluster_size:3
cluster_current_epoch:6
cluster_my_epoch:1
cluster_stats_messages_ping_sent:310
cluster_stats_messages_pong_sent:309
cluster_stats_messages_sent:619
cluster_stats_messages_ping_received:309
cluster_stats_messages_pong_received:310
cluster_stats_messages_received:619

$ docker exec -it node1 redis-cli cluster nodes
e35038db94bb15781a7b755f53f049d4d368f2aa 172.24.0.14:6379@16379 slave 3e1c9278cd382c0fe54959de0e3f2fc0996ece91 0 1626008143468 3 connected
985cf76aa3b6d6aaec787d57909a2dd0036d820b 172.24.0.16:6379@16379 slave 5cf61520c26d6dcc41f9e252fddfa6079dd57c59 0 1626008144472 2 connected
5cf61520c26d6dcc41f9e252fddfa6079dd57c59 172.24.0.12:6379@16379 master - 0 1626008143000 2 connected 5461-10922
6206555220ef97a6a565821862cc0d70bef770a3 172.24.0.11:6379@16379 myself,master - 0 1626008144000 1 connected 0-5460
adc98e6c2abfd3c40871fd6597bbe4e6ea5890c9 172.24.0.15:6379@16379 slave 6206555220ef97a6a565821862cc0d70bef770a3 0 1626008142465 1 connected
3e1c9278cd382c0fe54959de0e3f2fc0996ece91 172.24.0.13:6379@16379 master - 0 1626008143000 3 connected 10923-16383
```

#### 레디스 데이터 입출력(predixy 7616)
```
$ redis-cli -c -h 127.0.0.1 -p 7617 set hello world

$ redis-cli -c -h 127.0.0.1 -p 7617 get hello
```
###### 레디스 서버(컨테이너)로 데이타 입출력
```
docker exec -it node1 redis-cli -c get hello
```

###### git push
```
git add .
git commit -m "first commit"
git push -u origin main
```
