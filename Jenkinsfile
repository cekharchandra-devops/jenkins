pipeline {
    agent {
        label 'AGENT-1'
    }
    options{
        timeout(time: 10, unit: 'SECONDS') // job gets failed if it executes even after 10 secs
        disableConcurrentBuilds()
         retry(3)
    }
    stages {
        stage('Build') {
            steps {
                sh 'echo build..........'
                //sh 'sleep 10'
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
                error 'pipeline failed'
            }
        }
    }
     post { 
        always { 
            deleteDir()
            echo 'I will always say Hello again!'
        }
        success {
            echo 'succes::I will always say Hello again!'
        }
        failure {
            echo 'failure::I will always say Hello again!'
        }
    }
}