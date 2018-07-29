# KAFKA
假設我有三台VM
主程式
訊息推送端
訊息接收端

1. 環境設定
有可能導致程式無法開啟的原因有許多，例如:port被其他服務佔住、防火牆設定、記憶體不夠、沒裝Java…等等(暫時只有想到這些，還有其他的可以跟我討論一下)
   a. 其他服務佔住kafka的port
      kafka預設port是使用9092，確認要使用的port有沒有被其他服務所占用
      ```
      netstat -ntpl | grep 9092
      ```
   b. 防火牆
      設定kafka server host上的防火牆
      ```
      allow in 9092 port
      ```
      ref: [Ubuntu 用 ufw 指令快速啟用和設定防火牆](https://www.arthurtoday.com/2013/12/ubuntu-ufw-add-firewall-rules.html)

2. 下載kafka
下載.tar檔(或是用docker-compose)
```
wget http://ftp.tc.edu.tw/pub/Apache/kafka/1.1.0/kafka_2.11-1.1.0.tgz
```
解壓縮這個.tar會出現一個資料夾，啟動的程式放在bin資料夾裡面，而開啟程式的相關參數設定則是放在config資料夾裡面

3. 設定參數
這邊的參數檔有兩個檔案比較相關，config/zookeeper.properties還有config/server.properties
   a. Zookeeper.properties:
      如果kafka只架一台，在zookeeper.properties中，預設的是可以直接使用，不用修改的。如果kafka是要架多台(就是叢集啦)，在dataDir要設定不同的位置來存取快照，服務的port也要有所區隔，不能佔用同一個port(圖1)

   b. Server.properties:
      這個檔案可以設定的東西比較多，我以大邱老師最後一堂課的設定來舉例，. broker.id(圖2)設定broker的數目，每個broker都有個別的id，而不同的broker.id也要對應到不同的port

先開啟zookeeper再開啟kafka，原因是kafka叢集是由zookeeper來掌控，所有kafka的metadata都存在zookeeper)

```
bin/zookeeper-server-start.sh config/zookeeper.properties(開啟zookeeper)
```
```
bin/kafka-server-start.sh config/server.properties(開啟kafka)
```
