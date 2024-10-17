pipeline {
  agent {
    label 'agent2'
    }
  }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/yaohaihan/jenkins-demo.git', credentialsId: 'github-username-passwd'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
    }
}








