**Deployment server**

-------------------

sudo su

cd /opt

wget key

tar -zxvf splunk package .tgz

cd splunk/bin/

./splunk start --accept-license



cd /opt/splunk/etc/deployment-apps/



**creating app folder and local folder to keep inputs.conf and outputs.conf file**

--------------------------------------------------------------------------------



mkdir credit
mkdir local



**create inputs.conf and outputs.conf file inside the local folder**

--------------------------------------------------------------------

vi inputs.conf

[monitor///usr/aa/test.log]

_TCP_ROUTING = abc

index = bank 



vi outputs.conf

[tcpout: abc]

server = <index ip>:9997



**configuring the forwarders Deploymentclient.conf file**

-------------------------------------------------------

cd /opt/splunk/etc/system/local



vi deploymentclient.conf



[deployment-client]

[target-broker: deploymentServer]

targetUri = <deploymentserver ip>:8089



**Using deployment server UI we can configure the server class and apps**

**in setting agent management distributed environment**



**to push configuration file in DS**

------------------------------------

bin]# ./splunk reload deploy-server



**Restart all clients (UI)**

---------------------------

Forwarder Management → Restart Splunkd

Restart all connected clients



