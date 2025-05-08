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
    stage('Build and Test') {
      steps {
        sh 'ls -ltr'
        // build the project and create a JAR file
        sh ' mvn clean package'
      }
    }
        stage('SonarQube Analysis') {
            steps {
                script {  // Required for variable declarations and complex logic 
                    def mvn = tool 'jenkins-maven'  // Get Maven tool
                    withSonarQubeEnv('sonarqube server') {  // Use SonarQube environment
                        sh "${mvn}/bin/mvn clean verify sonar:sonar -Dsonar.projectKey=java-spring -Dsonar.host.url=http://192.168.178.158:9000 -Dsonar.login=sqp_8d7dbd5f2cad8177f430bcdcf831efae4ad7ce9d"
                    }
                }
            }
  }
}
 
}
