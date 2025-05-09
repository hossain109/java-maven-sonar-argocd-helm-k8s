pipeline {
 // agent {
   // docker {
     // image 'maven:3.8.6-openjdk-11'
     // args '--user root -v /var/run/docker.sock:/var/run/docker.sock' // mount Docker socket to access the host's Docker daemon
    //}
	
  //}
  agent any
  stages {
    stage('Checkout') {
      steps {
        sh 'echo passed'
        git branch: 'main', url: 'https://github.com/hossain109/java-maven-sonar-argocd-helm-k8s.git'
      }
    }
    stage('Build and Test') {
      steps {
        sh 'ls -ltr'
        // build the project and create a JAR file
        sh ' mvn clean package'
      }
    }
        stage('SonarQube Analysis') {
        environment {
        SONAR_URL = "http://192.168.178.158:9000"
      
	def mvn = tool 'jenkins-maven'  // Get Maven tool
	}
      steps {
        withCredentials([string(credentialsId: '71d32368-39a5-4c32-ad18-8271fbc08452', variable: 'SONAR_TOKEN')]) {
          sh '${mvn}/bin/mvn clean verify  sonar:sonar -Dsonar.login=$SONAR_TOKEN -Dsonar.host.url=${SONAR_URL}' 
        }
      }
  }
}
 
}
