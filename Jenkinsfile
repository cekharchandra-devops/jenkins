pipeline {
    agent {
        label 'AGENT-1'
    }
    options { 
        //timeout(time: 10, unit: 'SECONDS') // job gets failed if it executes even after 10 secs
        disableConcurrentBuilds()
        retry(3)  //job must be failed to see this feature executes added error statement in stage(Deploy)
        buildDiscarder(logRotator(numToKeepStr: '3')) //it keeps last three builds and deletes all the previously built builds
    }
    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')

        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')

        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')

        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')

        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }
    stages {
        stage('Build') {
            steps {
                sh 'echo build..........'
                sh 'sleep 10'
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
                //error 'pipeline failed'
               }
        }
        stage('Print Params'){
            steps{
                 echo "Hello ${params.PERSON}"
                echo "Biography: ${params.BIOGRAPHY}"
                echo "Toggle: ${params.TOGGLE}"
                echo "Choice: ${params.CHOICE}"
                echo "Password: ${params.PASSWORD}"
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

// pipeline {
//     // Define pipeline-level parameters
//     parameters {
//         string(name: 'BRANCH', defaultValue: 'main', description: 'Branch to build')
//         booleanParam(name: 'RUN_TESTS', defaultValue: true, description: 'Run unit tests')
//     }

//     // Define agent (where the pipeline runs)
//     agent {
//         label 'linux-node'
//     }

//     options {
//         // Keep logs for a specific duration
//         buildDiscarder(logRotator(numToKeepStr: '10'))
//         timeout(time: 30, unit: 'MINUTES') // Timeout for the pipeline
//     }

//     environment {
//         // Environment variables for all stages
//         JAVA_HOME = '/usr/lib/jvm/java-11'
//         PATH = "${JAVA_HOME}/bin:${env.PATH}"
//     }

//     triggers {
//         // Build triggers
//         pollSCM('H/5 * * * *') // Poll for changes every 5 minutes
//     }

//     stages {
//         stage('Pre-Build') {
//             steps {
//                 echo 'Pre-Build stage - Validating setup'
//                 script {
//                     // Example pre-build checks
//                     if (!fileExists('Jenkinsfile')) {
//                         error('Jenkinsfile not found!')
//                     }
//                 }
//             }
//         }

//         stage('Checkout Code') {
//             steps {
//                 git branch: params.BRANCH, url: 'https://github.com/example/repo.git'
//             }
//         }

//         stage('Build') {
//             steps {
//                 echo 'Building the application'
//                 sh './gradlew    ' // Example build command
//             }
//         }

//         stage('Run Tests') {
//             when {
//                 expression { params.RUN_TESTS }
//             }
//             steps {
//                 echo 'Running tests'
//                 sh './gradlew test'
//             }
//         }

//         stage('Deploy to Staging') {
//             steps {
//                 echo 'Deploying to staging environment'
//                 sh 'kubectl apply -f k8s/deployment.yaml'
//             }
//         }
//     }

//     post {
//         // Actions after pipeline completion
//         always {
//             echo 'Pipeline finished. Cleaning up workspace.'
//             deleteDir() // Clean workspace
//         }
//         success {
//             echo 'Pipeline succeeded!'
//             emailext(
//                 subject: 'Jenkins Build SUCCESS: Job ${env.JOB_NAME}',
//                 body: 'Good news! The build was successful.',
//                 to: 'team@example.com'
//             )
//         }
//         failure {
//             echo 'Pipeline failed!'
//             emailext(
//                 subject: 'Jenkins Build FAILURE: Job ${env.JOB_NAME}',
//                 body: 'The build has failed. Please check Jenkins for details.',
//                 to: 'team@example.com'
//             )
//         }
//     }
// }
