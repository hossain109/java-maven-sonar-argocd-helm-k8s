pipeline {
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
      script {  
	   // Required for variable declarations and complex logic 
            def mvn = tool 'jenkins-maven'  // Get Maven tool
            withSonarQubeEnv('sonarqube server') {  
              // Use SonarQube environment
        sh "${mvn}/bin/mvn clean verify sonar:sonar -Dsonar.projectKey=java-spring -Dsonar.host.url=http://192.168.178.158:9000  -Dsonar.login=sqp_eef703f713b4590b036d0e8022a533305f5498d5" 
        }
        }
      }
  }
 }
}
