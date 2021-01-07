# J-JIG: Jenkins, JMeter, Influx & Grafana

This is based from the Ellen Huang repo: https://github.com/jlight99/docker-jig

## Description
A solution which dockerizes a Jenkins pipeline in order to trigger JMeter performance tests, stores the info into a Influx database and then helps visualizes it with Grafana.

## How to run:
- Clone the repo
- Open the `docker-compose` file and edit the JMeter environment variables:
  * JMETER_TEST=[load_test_name.jmx]
  * JMETER_RAMPUP=[#inSeconds]
  * JMETER_THREADS=[#inSeconds]
  * JMETER_DURATION=[#inSeconds]
  * JMETER_URL=[http://qa-api/]
- `docker-compose up` to run start the installation/execution and `docker-compose down` to stop it
- Open the Jenkins agent  `localhost:8080` configure the task and build it.
- Check the Grafana dashboard `localhost:3000`

## For the Jenkins Pipeline (TBD)

Note: This instructions will be included in the docker-compose as an optional configuration.

- Port: 8080
- Name tag: jenkins-master
-  URL: http://localhost:8080/jjig
-  Volume info: 
    * Local = /Users/[user]/Dev/docker/jjig/volumes/jenkins-master
    * Docker = /var/jenkins_home
- Admin pass: Within the `volumes/jenkins-master` (secrets/initialAdminPassword)
- Command: `docker run -p 8080:8080 -v  /Users/adn/Dev/docker/jjig/volumes/jenkins-master:/var/jenkins_home --name jenkins-master jenkins/jenkins:lts`
