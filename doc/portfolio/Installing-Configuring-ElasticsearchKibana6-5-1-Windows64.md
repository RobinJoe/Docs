# Kibana Quick Start Guide

This is an opinionated quickstart guide for installing and running
a local Elasticsearch node with a Kibana dashboard on Windows. This allows you to explore the
core functionality of Elasticsearch and Kibana on a local device.

## Prerequisites

**Elasticsearch and Kibana are designed for large scale, enterprise search combined with visual analysis. While
an Elasticsearch local node can run on most computers of average memory, disk size, and processing speed,
any production deployment requires more resources, and more planning and architecture.**  

### Hardware

* At least 4 - 6 GB or ram.
* An 2.0 - 3.0GHz CPU.
* 120GB HDD or equivalent.

### Software

* Windows 10.
* Windows Powershell and Command Prompt.
* An internet browser such as Firefox, Chrome, Opera, or Microsoft Edge.
* Matching versions of Kibana and Elasticsearch.

**Make sure that your version of Kibana matches your version of Elasticsearch.**

## Download Elasticsearch

1. Navigate to the [Elasticsearch downloads](https://www.elastic.co/downloads/elasticsearch) page.

2. Select the version of Elasticsearch for the Windows Operation System (the ``.zip`` format file).

**The only supported package for the Windows Operating System is the ``.zip`` format.**

3. Once the file has finished downloading, unzip the contents in the directory required for your Elasticsearch node.

## Configure Elasticsearch

1. Navigate into the ``.\elasticsearch-6.5.1\`` directory through the Windows Graphic User Interface (GUI) or
through Command Prompt.

2. Access the ``\config`` directory.

3. Access the jvm.options file

4. Confirm that the JVM heap size is set to the following:

```
-Xms1g
-Xmx1g
```

It is important to confirm the JVM heap sizes match, and are the right size for your available system memory.

5. Navigate to the ``\bin`` directory.

6. Start Elasticsearch by running the following command:

```
> elasticsearch.bat
```

7. Confirm that Elasticsearch is running by checking for the following output from the Command Prompt:

```
[2018-01-01T20:00:00,000][INFO ][o.e.n.Node               ] [<clustercode>] started
```

## Download Kibana

1. Make sure Elasticsearch is running.

2. Navigate to the [Kibana downloads](https://www.elastic.co/downloads/kibana) page.

3. Select the version of Kibana for the Windows Operation System (the ``.zip`` format).

**The only supported package for the Windows Operating System is the ``.zip`` format.**

  > Depending on your internet connection, the Kibana visualiser ``.zip`` file might take anywhere between 10 and 25 minutes to download.

## Configure Kibana

1. Once the file has finished downloading, unzip the ``.zip`` file in the target directory.

**The Zip file make take 10 to 20 minutes to extract all the available files**

2. Navigate to the Kibana/config file.

3. Adjust the ``.yml`` file depending on your needs. You can change the behaviour of the Kibana dashboard through the ``.yml`` file.

## Install and start Kibana

1. Open the Windows Command Prompt.

  a. Navigate to the Windows Cortana Search bar
  b. Type ``cmd``
  c. Click on the Command Prompt to open it

**You can navigate through the Windows Command Line repositories with the ``cd`` and ``DIR`` commands**

2. Ensure that your Elasticsearch node is running before you start your Kibana visualiser running.

3. Run the following command to start Kibana on Windows:

```
> ./bin/kibana.bat
```

4. Confirm that Kibana is running by checking for the following output from the Command Prompt:

```
 log   [13:03:39.054] [info][listening] Server running at http://localhost:5601
```

**Log timestamp and server address will vary depending on your region and hardware configuration**

5. Navigate to the localhost address to view the Kibana dashboard.


## Troubleshooting Elasticsearch

If you receive the following error:

``common was unexpected at this time``

You can resolve this error by navigating to the ``bin\elasticsearch-service.bat`` directory, and adjusting the following settings:

1. Open the ``elasticsearch-service.bat`` file.

2. locate the following entry:

```
for /F "usebackq delims=" %%a in (`"%JAVA% -cp "!ES_CLASSPATH!"
```

3. Change the values to the following:

```
for /F "usebackq delims=" %%a in (`"!JAVA! -cp "!ES_CLASSPATH!"
```

4. Save the file, and restart Elasticsearch.

