pipeline {
    agent any
    triggers {
        pollSCM('* * * * *')
    }
    stages {
        stage('vcs') {
            steps {
                git branch: 'main', url: 'https://github.com/WorkshopsByKhaja/saleor-dashboard.git'
            }
        }
        stage('docker image build') {
            steps {
                sh 'docker image build -t srikanth458/images:DEV .'
            }
        }
        stage('push image to registry') {
            steps {
                sh 'docker image push srikanth458/images:DEV'
            }
        }
    }
}
