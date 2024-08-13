Terjadi alert pada ambari

NameNode Last Checkpoint

## Solusi

hdfs dfsadmin -safemode enter
hdfs dfsadmin -saveNamespace
hdfs dfsadmin -safemode leave

Restart all HDFS Service, or hanya NN dan JN

Sumber:
https://community.cloudera.com/t5/Support-Questions/NameNode-Last-Checkpoint-script-alert-definition-does-not/td-p/110844
https://support.huaweicloud.com/intl/en-us/trouble-mrs/mrs_03_0078.html
