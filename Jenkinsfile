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
        //git branch: 'main', url: 'https://github.com/sunitabachhav2007/Jenkins-Zero-To-Hero.git'
      }
    }
  }
    stage('Build and Test') {
      steps {
        sh 'ls -ltr'
        // build the project and create a JAR file
        sh 'cd java-maven-sonar-argocd-helm-k8s && mvn clean package'
      }
    }
}
