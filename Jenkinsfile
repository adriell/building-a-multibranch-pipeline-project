pipeline {
    agent {
        docker {
            image 'node:6-alpine'
            args  '-p 3000:3000'
        }
    }
    environment{
        CI = 'true'
    }
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
        stage('Test'){
            steps{
                sh './jenkins/scripts/test.sh'
            }
        }
        stage('Deliver for Development'){
            steps{
                sh './jenkins/deliver-for-development.sh'
                input 'Deploy para ambiente de desenvolvimento?'
                sh './jenkins/script/kill.sh'
            }
        }
        stage('Deliver for Production'){
            steps{
                sh './jenkins/deliver-for-production.sh'
                input 'Deploy para ambiente de produção?'
                sh './jenkins/script/kill.sh'
            }
        }
    }
}
