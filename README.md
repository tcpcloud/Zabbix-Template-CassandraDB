# Template Linux CassandraDB

A Zabbix template for CassandraDB (cluster) monitoring

Based on nagios checks and harisekhon's github repo

Tested on:
CentOs 6.x x86_64
Zabbix 2.0.x
CassandraDB 1.2.x

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

* High			CassandraDB - found down nodes on {HOST.NAME}

* Not classified	CassandraDB - Gossip state active is not "true"

* Warning	        CassandraDB - Heap Memory usage is >85%	

* Average	        CassandraDB - Heap Memory usage is >95%	

* Average	        CassandraDB - low nodes on {HOST.NAME}

* High		        CassandraDB - Main Status is "PROBLEM" on {HOST.NAME}

* Average	        CassandraDB - Nodes global status is not "OK" on {HOST.NAME}

* Not classified	CassandraDB - Thrift state active is not "true"

* Average	        CassandraDB - TPstats is not "OK" on {HOST.NAME}	

* Information		CassandraDB - Host ID was changed on {HOST.NAME}

* Information		CassandraDB - server was rebooted on {HOST.NAME}


### Links

