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
        stage('Build'){
            steps{
                sh 'ls -la'
                echo 'Building'
            }
        }
    }
    stage('Deploy to S3') {
        steps {
            sh '''
                aws s3 cp index.html s3://my-test-bucket-jenkins-deploy/index.html
            '''
        }
    }
}
