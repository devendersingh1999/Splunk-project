**Index cluster**
------------------
**cluster master configuration creating server.conf file**
-----------------------------------------------------------
cd /opt/splunk/etc/system/local

vi server.conf

[clustering]
mode = master
replication_factor = 3
search_factor = 2
cluster_label = indexer_cluster

**Indexer**
--------
cd /opt/splunk/etc/system/local

vi server.conf

[clustering]
mode = peer
master_uri = https://<cluster-master-IP>:8089
replication_port = 9887

**search head**
----------------
cd /opt/splunk/etc/system/local

vi server.conf

[clustering]
mode = searchhead
master_uri = https://<cluster-master-IP>:8089

**pushing configuration**
-------------------------

cd /opt/splunk/bin
./splunk apply cluster-bundle





