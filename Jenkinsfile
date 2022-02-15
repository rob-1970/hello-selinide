pipeline {
    agent any
    stages {
        stage('Clean') {
            steps {
                sh './gradlew clean'
            }
        }

        stage('Test') {
            parallel{
                stage('test: chrome'){
                    steps {
                        sh './gradlew test'
                    }
                }
                stage('test: firefox'){
                    steps {
                        sh './gradlew testFirefox'
                    }
                }
            }
            post {
                always {
                    junit 'build/test-results/test/*.xml'
                }
            }
        }

        stage('Build') {
            steps {
                echo 'BUILDING . . . . . . . . .'
             }
        }

        stage('Deploy') {
            steps{
                echo 'Deploying . . . . . . . . .'
            }
        }

        stage('InfoTEAM')  {
            steps{
                echo 'Info TEAM about SUCCESS . . . . . . . . .'
            }
        }
    }
}