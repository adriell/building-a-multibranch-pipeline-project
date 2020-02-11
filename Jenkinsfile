pipeline {
    agent {
        docker {
            image 'node:6-alpine'
            args  '-p 3000:3000gi'
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
        stage{
            steps{
                sh './jenkins/scripts/test.sh'
            }
        }
    }
}
