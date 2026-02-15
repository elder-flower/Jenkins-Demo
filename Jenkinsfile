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
        stage('Deploy to S3') {
            steps {
                sh '''
                    aws s3 cp index.html s3://my-test-bucket-jenkins-deploy/index.html
                '''
            }
        }
        stage('Test') {
            steps {
                echo 'Testing'
                script {
                    def url = 'http://my-test-bucket-jenkins-deploy.s3-website-ap-northeast-1.amazonaws.com/'
                    def response = sh(script: "curl -s -o /dev/null -w '%{http_code}' '$url'", returnStdout: true)

                    if (response == '200') {
                        echo 'Test OK'
                    } else {
                        echo response
                        error 'Test NG'
                    }
                }
            }
        }
        stage('Release') {
            steps {
                echo 'Releasing'
            }
        }
    }
}
