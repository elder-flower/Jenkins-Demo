pipeline {
    agent any
    options {
        buildDiscarder logRotator(
            artifactDaysToKeepStr: '10',
            artifactNumToKeepStr: '5',
            daysToKeepStr: '30',
            numToKeepStr: '5'
        )
    }
    stages {
        stage('Checkout') {
            steps {
                git url: 'git@github.com:elder-flower/Jenkins-Demo.git',
                    credentialsId: 'github-ssh-key',
                    branch: 'main'
            }
        }
        stage('Contents'){
            steps{
                sh 'ls -la'
            }
        }
    }
}
