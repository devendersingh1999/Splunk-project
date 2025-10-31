**Cluster Master**
----------------
sudo su
cd /opt
wget key
tar -zxvf splunk package .tgz
cd splunk/bin/
./splunk start --accept-license

*this is cluster bundle*
---------------------------
cd opt/splunk/etc/master-apps/_cluster/local

**creating indexes.conf file inside the local folder**
----------------------------------------------------
vi indexes.conf

[default]
homePath   = /opt/splunk/var/lib/splunk/defaultdb/db
coldPath   = /opt/splunk/var/lib/splunk/defaultdb/colddb
thawedPath = /opt/splunk/var/lib/splunk/defaultdb/thaweddb

[main]
homePath   = /opt/splunk/var/lib/splunk/main/db
coldPath   = /opt/splunk/var/lib/splunk/main/colddb
thawedPath = /opt/splunk/var/lib/splunk/main/thaweddb

[security_logs]
homePath   = /opt/splunk/var/lib/splunk/security_logs/db
coldPath   = /opt/splunk/var/lib/splunk/security_logs/colddb
thawedPath = /opt/splunk/var/lib/splunk/security_logs/thaweddb

**defining the rf and sf**
-------------------------
/opt/splunk/etc/system/local/server.conf

[clustering]
mode = master
replication_factor = 3
search_factor = 2
cluster_label = indexer_cluster

**pushing the index to peers**
------------------------------------------
bin] # ./splunk apply cluster-bundle

**Reloads bundle changes without restarting peers**
--------------------------------------------------
bin] # ./splunk reload cluster-bundle







