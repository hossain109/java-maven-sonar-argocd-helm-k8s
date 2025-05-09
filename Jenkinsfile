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
      steps {
        mvn clean verify sonar:sonar -Dsonar.projectKey=java-spring -Dsonar.host.url=http://192.168.178.158:9000  -Dsonar.login=sqp_eef703f713b4590b036d0e8022a533305f5498d5 
        }
      }
  }
}
 
}
