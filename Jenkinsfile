pipeline {
  agent {
    kubernetes {
          yaml '''
            apiVersion: v1
            kind: Pod
            metadata:
              namespace:jenkins
              labels:
                some-label: some-label-value
            spec:
              containers:
              - name: maven
                image: maven:3.9.9-eclipse-temurin-17
              - name: busybox
                image: busybox
              - name: jnlp
                image: jenkins/inbound-agent:latest
                args:
                - ${computer.jnlpmac}
                - ${computer.name}
            '''
          retries 2
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






