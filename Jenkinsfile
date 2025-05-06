pipeline {
  agent {
    docker {
      image 'sohrab109/java-maven-sonar-argocd-helm-k8s'
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
}
