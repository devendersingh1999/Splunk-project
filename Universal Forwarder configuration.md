**Universal Forwarder**

---------------------

sudo su

cd /opt

wget key

tar -zxvf splunk package .tgz

cd splunk/bin/

./splunk start --accept-license





**cd /opt/splunk/etc/system/local**

vi inputs.conf



[master///usr/aa/a.log]

index = bank

_TCP_ROUTING = ab



**cd /opt/splunk/etc/system/local**

vi outputs.conf



[tcpout:ab]

server = <index ip>:9997



**Enable receiving port on indexer**

--------------------------------

cd /opt/splunk/bin

./splunk enable listen 9997

./splunk restart





