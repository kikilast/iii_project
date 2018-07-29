# KAFKA
���]�ڦ��T�xVM
�D�{��
�T�����e��
�T��������

1. ���ҳ]�w
���i��ɭP�{���L�k�}�Ҫ���]���\�h�A�Ҧp:port�Q��L�A�Ȧ���B������]�w�B�O���餣���B�S��Java�K����(�Ȯɥu���Q��o�ǡA�٦���L���i�H��ڰQ�פ@�U)
   a. ��L�A�Ȧ���kafka��port
      kafka�w�]port�O�ϥ�9092�A�T�{�n�ϥΪ�port���S���Q��L�A�ȩҥe��
      ```
      netstat -ntpl | grep 9092
      ```
   b. ������
      �]�wkafka server host�W��������
      ```
      allow in 9092 port
      ```
      ref: [Ubuntu �� ufw ���O�ֳt�ҥΩM�]�w������](https://www.arthurtoday.com/2013/12/ubuntu-ufw-add-firewall-rules.html)

2. �U��kafka
�U��.tar��(�άO��docker-compose)
```
wget http://ftp.tc.edu.tw/pub/Apache/kafka/1.1.0/kafka_2.11-1.1.0.tgz
```
�����Y�o��.tar�|�X�{�@�Ӹ�Ƨ��A�Ұʪ��{����bbin��Ƨ��̭��A�Ӷ}�ҵ{���������ѼƳ]�w�h�O��bconfig��Ƨ��̭�

3. �]�w�Ѽ�
�o�䪺�Ѽ��ɦ�����ɮפ�������Aconfig/zookeeper.properties�٦�config/server.properties
   a. Zookeeper.properties:
      �p�Gkafka�u�[�@�x�A�bzookeeper.properties���A�w�]���O�i�H�����ϥΡA���έק諸�C�p�Gkafka�O�n�[�h�x(�N�O�O����)�A�bdataDir�n�]�w���P����m�Ӧs���ַӡA�A�Ȫ�port�]�n���ҰϹj�A������ΦP�@��port(��1)

   b. Server.properties:
      �o���ɮץi�H�]�w���F�����h�A�ڥH�j���Ѯv�̫�@��Ҫ��]�w���|�ҡA. broker.id(��2)�]�wbroker���ƥءA�C��broker�����ӧO��id�A�Ӥ��P��broker.id�]�n�����줣�P��port

���}��zookeeper�A�}��kafka�A��]�Okafka�O���O��zookeeper�Ӵx���A�Ҧ�kafka��metadata���s�bzookeeper)

```
bin/zookeeper-server-start.sh config/zookeeper.properties(�}��zookeeper)
```
```
bin/kafka-server-start.sh config/server.properties(�}��kafka)
```
