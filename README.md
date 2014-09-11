# Template Linux CassandraDB

A Zabbix template for CassandraDB (cluster) monitoring

Based on nagios checks and harisekhon's github repo

Tested on:
CentOs 6.x x86_64
Zabbix 2.0.x
CassandraDB 1.2.x

next values can be added over JMX util:
bash-4.1# java -jar ./cmdline-jmxclient-0.10.3.jar - 127.0.0.1:7199 java.lang:type=Runtime Uptime

and JMX items is:
org.apache.cassandra.request:type=*
org.apache.cassandra.internal:type=*
org.apache.cassandra.db:type=*

### Authors
* Patrik Majer p.majer@tcpisek.cz (<patrik.majer.pisek@gmail.com>)


### installation

(* install a configure zabbix-agent)

* copy file "zabbix-cassandraDB.conf" into your zabbix-agent include folder

* copy script "cassandra.pl" into script folder (/root/scripts)
source: http://exchange.nagios.org/directory/Plugins/Java-Applications-and-Servers/Check-Cassandra-status-and-heap-memory-utilization/details

* copy script "check_cassandra_nodes.pl" and "check_cassandra_nodes.pl" into script folder (/root/scripts)
source: https://github.com/harisekhon/nagios-plugins

* install perl JSON module (cpan JSON)

* copy perl modules: Cassandra.pm, HariSekhonUtils.pm, Nodetool.pm
source: https://github.com/harisekhon/lib/tree/master/HariSekhon

* reboot zabbix-agent service

* import xml file into your zabbix server


### Monitored items

* Info - Host ID

* Info - Uptime

* Info - Native Transport Active

* Info - Exceptions

* Info - Thrift Active

* Info - Gossip Active

* Info - Heap Memory (Used)

* Info - Main Status Text

* Info - Main Status

* Status - Nodes global status

* Status - Nodes ALL (text)

* Status - Nodes Down (count)

* Status - Nodes Up (count)


* TPstats - global status

* TPstats - ReadStage Active

* TPstats - ReadStage Pending

* TPstats - ReadStage All time blocked

* TPstats - ReadStage Blocked

* TPstats - ReadStage Completed


### Trigers

* CassandraDB - found down nodes on {HOST.NAME} (High)

* CassandraDB - Gossip state active is not "true" (Not classified)

* CassandraDB - Heap Memory usage is >85% (Warning)

* CassandraDB - Heap Memory usage is >95% (Average)

* CassandraDB - low nodes on {HOST.NAME} (Average)

* CassandraDB - Main Status is "PROBLEM" on {HOST.NAME} (High)

* CassandraDB - Nodes global status is not "OK" on {HOST.NAME} (Average)

* CassandraDB - Thrift state active is not "true" (Not classified)

* CassandraDB - TPstats is not "OK" on {HOST.NAME} (Average)

* CassandraDB - Host ID was changed on {HOST.NAME} (Information)

* CassandraDB - server was rebooted on {HOST.NAME} (Information)


### Links

* https://github.com/mrmichalis/CassyCmd

* http://www.mail-archive.com/user@cassandra.apache.org/msg08100.html

* https://code.google.com/p/simple-cassandra-monitoring/

* http://mail-archives.apache.org/mod_mbox/cassandra-user/201205.mbox/%3C2C85E14562B39345BCCAD90B8E7955C90D9354@DKEXC001.adform.com%3E

* https://github.com/jamesgolick/cassandra-munin-plugins

* http://www.jointhegrid.com/cassandra/cassandra-cacti-m6.jsp

* http://wiki.apache.org/cassandra/Operations

* http://crawler.archive.org/cmdline-jmxclient/cmdline-jmxclient-0.10.3.jar

