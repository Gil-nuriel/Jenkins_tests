pipeline {
    agent any
    stages {
        stage('start') {
            steps {
                sh "echo changes detected"
            }
        }
        stage('--test--') {
            steps {
              sh "pwd"
              
            }
        }
        stage('test inside slave machine') {
            steps {
              sh "echo waiting for aprove from the QA"
              input "pass the test?"
              
            }
        }
        stage('deploy') {
            steps {
               sh "echo deploy for production"
            }
        }
    }
}
