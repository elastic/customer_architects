## Prerequisites

[Create an Elastic Cloud trial](https://www.elastic.co/cloud/cloud-trial-overview)

Please include an ML node in your trial.

1. Expand Advanced settings

![alt_text](images/image1.png "image_tooltip")

2. Under Machine Learning instances, click on + Add capacity

![alt_text](images/image2.png "image_tooltip")

3. You should see the following before clicking on Create deployment.

![alt_text](images/image3.png "image_tooltip")

4. Make sure you save the user Elastic and its corresponding password. 
5. Once the instance is up and running, please save your Cloud Id as well. 

![alt_text](images/image4.png "image_tooltip")

We are ready to begin our exercises. Please be prepared to share what you did. Please note, the documentations are not perfect. 

There are two exercises below. You can choose either. 

## Exercise 1 

### Collect Metrics from your local via System integration

Follow [these instructions](https://www.elastic.co/guide/en/fleet/current/install-fleet-managed-elastic-agent.html#elastic-agent-installation-steps) for Elastic Agent to collect metrics from your local machine.

* Disable log collection for your system integration
* Navigate to `Observability > Infrastructure > Hosts`  (You may need to enable this)
* [Create 2 alerts/rules](https://www.elastic.co/guide/en/observability/8.8/create-alerts.html#create-alerts-rules) 

    1. Send yourself an email when average `system.cpu.system.pct` is above 50% usage for the last 1 min 
    2. Send yourself an email when average `system.memory.used.pct` is above 85% for the last 1 min

* **Bonus point**: Customize alert subject and content

### Collect Logs using Logstash

* Please use the attached [apache access log file](data/apache-access.log)
* Here is the [quick start guide for Logstash](https://www.elastic.co/guide/en/logstash/current/getting-started-with-logstash.html)
* Please use the [Logstash file input](https://www.elastic.co/guide/en/logstash/current/plugins-inputs-file.html)
 and [Elasticsearch output](https://www.elastic.co/guide/en/logstash/current/connecting-to-cloud.html#connecting-to-cloud) In addition, please consult [Elasticsearch output for additional configurations](https://www.elastic.co/guide/en/logstash/current/plugins-outputs-elasticsearch.html) 
* You can use a [prebuilt Logstash grok pattern](https://github.com/hpcugent/logstash-patterns/blob/master/files/grok-patterns) or specify [your own](https://www.elastic.co/guide/en/logstash/current/plugins-filters-grok.html)
* Use [Kibana](https://www.elastic.co/guide/en/kibana/current/get-started.html#view-and-analyze-the-data) to create visualizations on a few points of possible interests with the Apache access log and gather them into a [Kibana dashboard](https://www.elastic.co/guide/en/kibana/current/dashboard.html)
* **Bonus point**: Create a [single metric anomaly detection job](https://www.elastic.co/guide/en/machine-learning/8.8/ml-ad-finding-anomalies.html) to detect excessive or low log rate. You may need to create a [data view](https://www.elastic.co/guide/en/kibana/current/data-views.html#data-views) first. 

## Collect APM traces

The application that we are monitoring is [Spring Pet Clinic](https://github.com/spring-projects/spring-petclinic). Please see intructions in the repo on how to [run Petclinic](https://github.com/spring-projects/spring-petclinic#running-petclinic-locally). It is a Java application so you would need 

1. JDK17
2. Set JAVA_HOME

* Follow [instructions to set up Elastic APM](https://www.elastic.co/guide/en/apm/guide/current/apm-quick-start.html#add-apm-integration)
* The APM Agents tab contains detailed instructions on how to instrument applications in various languages with Elastic APM agent. We are using a Java agent here.
* Go to `Observability > APM > Services` to see the instrumented application when complete

## Final Question

* How are the vitals of your local host while you are ingesting data? Any alerts triggered.

## Exercise 2 

## Benchmark Elasticsearch using ESRally**

* Beachmark with [ESRally](https://esrally.readthedocs.io/en/stable/quickstart.html) [using a remote cluster](https://esrally.readthedocs.io/en/stable/recipes.html#benchmarking-a-remote-cluster)
* Please come prepared to explain what track(s) you used and what are the race results.
* **Bonus Points** - Create your own [custom track](https://esrally.readthedocs.io/en/stable/adding_tracks.html) 


