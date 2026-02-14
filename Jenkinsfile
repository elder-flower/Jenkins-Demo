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
        stage('Contents'){
            steps{
                sh 'ls -la'
                echo 'Building'
            }
        }
    }
}
