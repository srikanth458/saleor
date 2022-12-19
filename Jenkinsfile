pipeline {
    agent any
    triggers {
        pollSCM('* * * * *')
    }
    stages {
        stage('vcs') {
            steps {
                git branch: 'main', url: 'https://github.com/srikanth458/saleor.git'
            }
        }
        stage('docker image build') {
            steps {
                sh 'docker image build -t srikanth458/jenkins:DEV .'
            }
        }
        stage('push image to registry') {
            steps {
                sh 'docker push srikanth458/jenkins:DEV'
            }
        }
    }
}
