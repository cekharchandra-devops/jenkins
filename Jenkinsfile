pipeline {
    agent any
    options{
        timeout(time: 10, unit: 'SECONDS')
        disableConcurrentBuilds()
    }
    stages {
        stage('Build') {
            steps {
                sh 'echo build..........'
                sh 'sleep 5'
            }
        }
        stage('Test') {
            steps {
                sh 'echo Test .............'
            }
        }
        stage('Deploy') {
            steps {
                sh 'echo Deploy..........'
            }
        }
    }
     post { 
        always { 
            echo 'I will always say Hello again!'
            deleteDir()
        }
    }
}