pipeline {
    agent any
    stages {
        stage('start') {
            steps {
                sh "echo changes detected"
            }
        }
        stage('test inside slave machine') {
            agent {label 'slave_2'}
            steps {
                sh "pwd"
            }
            steps {
              sh "javac HellowWorld.java"
              sh "java HellowWorld"
            }
        }
        stage('QA test') {
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
