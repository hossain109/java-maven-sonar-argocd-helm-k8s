pipeline {
  agent {
    docker {
      image 'maven:3.8.6-openjdk-11'
      args '--user root -v /var/run/docker.sock:/var/run/docker.sock' // mount Docker socket to access the host's Docker daemon
    }
  }
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
      }
      steps {
        withCredentials([string(credentialsId: '71d32368-39a5-4c32-ad18-8271fbc08452', variable: 'sonar_token')]) {
          sh 'mvn sonar:sonar -Dsonar.login=$sonar_token -Dsonar.host.url=${SONAR_URL}'
          sh ' sleep(time: 5, unit: 'SECONDS')' // Allow time for file write        
        }
      }
  }
}
 
}
