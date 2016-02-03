# Spark notebook for Hue

This repository contains instructions about how to enable Spark notebook in Hue.

Tested on:
* CDH 5.5.1 with parcels
* Hue 3.9
* Centos 6.6
* Livy Spark Server prebuilt for CDH 5.5.1


## Initial configuration

To enable Spark notebook in Hue some configuration lines should be added to `hue.ini` file and Livy Spark Server should be started. Here are the details how to do this:

* Add lines from [add-to-hue.ini](add-to-hue.ini) to *Hue Service Advanced Configuration Snippet (Safety Valve) for hue_safety_valve.ini* in Cloudera Manager and restart Hue service.
* Copy [livy-spark-server](livy-spark-server) to `/etc/init.d/` directory on the host there Livy Spark Server will be run.
* Run the below commands under `root` user (or use `sudo`) to correct permissions for script and enable it on boot:

```
chmod +x /etc/init.d/livy-spark-server
chkconfig --add livy-spark-server
chkconfig livy-spark-server on
```

*That is all! Now you should be able to start Spark Notebook in Hue!*

