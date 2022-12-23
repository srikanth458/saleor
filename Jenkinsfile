pipeline {
    agent {label 'NODE1'}
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
                sh 'docker image build -t srikanth458/images:DEV .'
            }
        }
        stage('push image to registry') {
            steps {
                sh 'docker push srikanth458/images:DEV'
            }
        }
        stage('terraform'){
            steps{
                git clone https://github.com/hashicorp/learn-terraform-provision-eks-cluster
                 sh 'terraform init'
                 sh  'terraform apply --auto-approve'
            
            }
        }
    }
}
