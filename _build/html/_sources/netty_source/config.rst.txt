Configuration
=============

NettySourceConnector
--------------------

The Source Connector will receive data from network and write to kafka a
topic.

.. code:: properties

   name=nettyConnector
   tasks.max=1
   connector.class=com.mckesson.kafka.connect.nettysource.NettySourceConnector
   topic=network_data

   # Set these required values
   transport.protocol=TCP
   port=1234

+-----------+-----------+---------+----------+-----------+-----------+
| Name      | De        | Type    | Default  | I         | Notes     |
|           | scription |         |          | mportance |           |
+===========+===========+=========+==========+===========+===========+
| bin       | Bind      | string  | 0.0.0.0  | high      |           |
| d.address | address   |         |          |           |           |
+-----------+-----------+---------+----------+-----------+-----------+
| transport | Transport | string  | tcp      | high      | allowed   |
| .protocol | level     |         |          |           | values:   |
|           | protocol  |         |          |           | **tcp**,  |
|           |           |         |          |           | \ **udp** |
+-----------+-----------+---------+----------+-----------+-----------+
| port      | Listening | int     |          | high      |           |
|           | port      |         |          |           |           |
+-----------+-----------+---------+----------+-----------+-----------+
| pipe      | Class     | class   | depends  | high      | for tcp:  |
| line.fact | name      |         | on       |           | ``com.    |
| ory.class | imp       |         | protocol |           | mckesson. |
|           | lementing |         |          |           | kafka.con |
|           | ``org     |         |          |           | nect.nett |
|           | .jboss.ne |         |          |           | ysource.D |
|           | tty.chann |         |          |           | efaultTcp |
|           | el.Channe |         |          |           | PipelineF |
|           | lPipeline |         |          |           | actory``, |
|           | Factory`` |         |          |           | for udp:  |
|           |           |         |          |           | ``com.    |
|           |           |         |          |           | mckesson. |
|           |           |         |          |           | kafka.con |
|           |           |         |          |           | nect.nett |
|           |           |         |          |           | ysource.D |
|           |           |         |          |           | efaultUdp |
|           |           |         |          |           | PipelineF |
|           |           |         |          |           | actory``. |
|           |           |         |          |           | See below |
|           |           |         |          |           | conf      |
|           |           |         |          |           | iguration |
|           |           |         |          |           | options   |
|           |           |         |          |           | for the   |
|           |           |         |          |           | factories |
+-----------+-----------+---------+----------+-----------+-----------+
| ports     | Listening | list    |          | medium    | same as   |
|           | ports     |         |          |           | ‘         |
|           |           |         |          |           | ``port``’ |
|           |           |         |          |           | but       |
|           |           |         |          |           | multiply  |
|           |           |         |          |           | ports can |
|           |           |         |          |           | be        |
|           |           |         |          |           | s         |
|           |           |         |          |           | pecified, |
|           |           |         |          |           | used if   |
|           |           |         |          |           | port is   |
|           |           |         |          |           | already   |
|           |           |         |          |           | in use    |
+-----------+-----------+---------+----------+-----------+-----------+
| h         | Enable    | boolean | false    | medium    | Enable    |
| ealthchec | he        |         |          |           | listening |
| k.enabled | althcheck |         |          |           | tcp port  |
|           | listener  |         |          |           | for       |
|           |           |         |          |           | he        |
|           |           |         |          |           | althcheck |
|           |           |         |          |           | purpose.  |
|           |           |         |          |           | Useful    |
|           |           |         |          |           | when      |
|           |           |         |          |           | ``transp  |
|           |           |         |          |           | ort.proto |
|           |           |         |          |           | col=udp`` |
|           |           |         |          |           | and       |
|           |           |         |          |           | loa       |
|           |           |         |          |           | dbalancer |
|           |           |         |          |           | c         |
|           |           |         |          |           | onfigured |
|           |           |         |          |           | in front  |
|           |           |         |          |           | of kafka  |
|           |           |         |          |           | connect.  |
+-----------+-----------+---------+----------+-----------+-----------+
| health    | Bind      | string  | 0.0.0.0  | medium    |           |
| check.bin | address   |         |          |           |           |
| d.address | for       |         |          |           |           |
|           | he        |         |          |           |           |
|           | althcheck |         |          |           |           |
+-----------+-----------+---------+----------+-----------+-----------+
| healthc   | Listening | int     |          | medium    |           |
| heck.port | port for  |         |          |           |           |
|           | he        |         |          |           |           |
|           | althcheck |         |          |           |           |
+-----------+-----------+---------+----------+-----------+-----------+
| healthch  | Listening | list    |          | medium    | same as   |
| eck.ports | ports for |         |          |           | ‘         |
|           | he        |         |          |           | ``port``’ |
|           | althcheck |         |          |           | but       |
|           |           |         |          |           | multiply  |
|           |           |         |          |           | ports can |
|           |           |         |          |           | be        |
|           |           |         |          |           | s         |
|           |           |         |          |           | pecified. |
|           |           |         |          |           | used if   |
|           |           |         |          |           | port is   |
|           |           |         |          |           | already   |
|           |           |         |          |           | in use    |
+-----------+-----------+---------+----------+-----------+-----------+
| ss        | Enable    | boolean | false    | medium    | can be    |
| l.enabled | SSL/TLS   |         |          |           | used for  |
|           |           |         |          |           | ``transp  |
|           |           |         |          |           | ort.proto |
|           |           |         |          |           | col=tcp`` |
|           |           |         |          |           | only. See |
|           |           |         |          |           | below for |
|           |           |         |          |           | the       |
|           |           |         |          |           | available |
|           |           |         |          |           | options   |
+-----------+-----------+---------+----------+-----------+-----------+

SSL configuration options
~~~~~~~~~~~~~~~~~~~~~~~~~

+------------+------------+--------+---------+------------+-------+
| Name       | D          | Type   | Default | Importance | Notes |
|            | escription |        |         |            |       |
+============+============+========+=========+============+=======+
| ss         | The SSL    | string | TLS     |            |       |
| l.protocol | protocol   |        |         |            |       |
|            | used to    |        |         |            |       |
|            | generate   |        |         |            |       |
|            | the        |        |         |            |       |
|            | S          |        |         |            |       |
|            | SLContext. |        |         |            |       |
+------------+------------+--------+---------+------------+-------+
| ssl.key    |            |        |         |            |       |
| store.type |            |        |         |            |       |
+------------+------------+--------+---------+------------+-------+
| s          |            |        |         |            |       |
| sl.keystor |            |        |         |            |       |
| e.location |            |        |         |            |       |
+------------+------------+--------+---------+------------+-------+
| s          |            |        |         |            |       |
| sl.keystor |            |        |         |            |       |
| e.password |            |        |         |            |       |
+------------+------------+--------+---------+------------+-------+
| ssl        | key alias  | string |         |            |       |
| .key.alias | for JKS    |        |         |            |       |
+------------+------------+--------+---------+------------+-------+
| ssl.ke     |            |        |         |            |       |
| y.password |            |        |         |            |       |
+------------+------------+--------+---------+------------+-------+
| ssl.trust  |            |        |         |            |       |
| store.type |            |        |         |            |       |
+------------+------------+--------+---------+------------+-------+
| ssl        |            |        |         |            |       |
| .truststor |            |        |         |            |       |
| e.location |            |        |         |            |       |
+------------+------------+--------+---------+------------+-------+
| ssl        |            |        |         |            |       |
| .truststor |            |        |         |            |       |
| e.password |            |        |         |            |       |
+------------+------------+--------+---------+------------+-------+

..

   see ``org.apache.kafka.common.config.SslConfigs`` for more
   comprehensive description of above params

PipelineFactory configuration options
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+------+
| Name |
+======+
+------+

