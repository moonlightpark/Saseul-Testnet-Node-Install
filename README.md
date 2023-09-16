# Testnet-Node-Install
Saseul Testnet Node install


docker check.
[23/09/16 9:07:27] ➜  ~ docker ps

CONTAINER ID   IMAGE                               COMMAND              CREATED       STATUS       PORTS                NAMES

ee1de1d0a65c   artifriends/saseul-network:latest   "/bin/saseul-init"   5 weeks ago   Up 5 hours   0.0.0.0:80->80/tcp   saseul-node

[23/09/16 9:14:35] ➜  ~

​

bash in docker.

[23/09/16 9:15:43] ➜  ~ docker exec -it saseul-node /bin/bash
[root@ee1de1d0a65c /]# cd /var/saseul/saseul-network
[root@ee1de1d0a65c saseul-network]# pwd
/var/saseul/saseul-network

​

[root@ee1de1d0a65c saseul-network]# vi saseul.ini
;;;
; Copyright by ArtiFriends Inc.
; All rights reserved.
;;;

​

; This variable is the path to keep the log.
; You can write relative paths or absolute paths.

[Directory]
log_file = "saseul.log"
err_file = "debug.log"
data_dir = "data"

​

; full | partial
; full: When the capacity is full, it stops the node without erasing the data.
; partial: When the capacity is full, keep only a partial of the data.

[Node]
ledger_type = "partial"
database = false
mining = false

​

[Storage]

data_dir = "data"

​

[Database]

mysql_host = "localhost"
mysql_port = "3306"
mysql_user = ""
mysql_password = ""
mysql_database = ""

​

; The starting point of the peer search.
; If not, scan all IPs.

[Network]

peers[] = "test.saseul.net"

​

; This is information of genesis block.
network_name = "AMERICANO TEST NETWORK"
system_nonce = "A cup of coffee for relaxation."
genesis_address = "51d6429fd0641f37c125eb6d0d3e269d1283588dc612"
manager_addresses[] = "51d6429fd0641f37c125eb6d0d3e269d1283588dc612"

:wq   //save and exit vi

​

[root@ee1de1d0a65c saseul-network]# exit

[23/09/16 9:07:27] ➜  ~  docker restart saseul-node   // docker restart

[23/09/16 9:19:32] ➜  ~ docker exec -i saseul-node saseul-script forcesync --peer test.saseul.net

[23/09/16 9:19:32] ➜  ~ docker exec -i saseul-node saseul-script start

[23/09/16 9:19:32] ➜  ~ docker exec -i saseul-node saseul-script startmining

[23/09/16 9:19:32] ➜  ~ docker exec -i saseul-node saseul-script info

​

END.
