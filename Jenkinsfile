pipeline {
    agent none
    options { skipDefaultCheckout() }
    stages {
        stage('start') {
            agent {label 'master'}
            steps {
                sh "echo changes detected"
            }
        }
        stage('test inside slave machine') {
            agent {label 'slave_2'}
            steps {
              checkout scm
              sh "pwd"
              sh "javac HellowWorld.java"
              sh "java HellowWorld"
              cleanWs()
            }
        }
        stage('test on docker image') {
            agent {dockerfile true}
            steps {
            sh "mvn --version"
            }
        }
        stage('QA test') {
            agent {label 'master'}
            steps {
              sh "echo waiting for aprove from the QA"
              input "pass the test?"
              
            }
        }
        stage('deploy') {
             agent {label 'master'}
            steps {
               sh "echo deploy for production"
            }
        }
    }
}
