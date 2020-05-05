pipeline {
    agent none
    options { skipDefaultCheckout() }
    environment{
        test = 'test/'
    }
    stages {
        stage('start') {
            agent {label 'master'}
            steps {
                dir('client'){
                sh "echo changes detected"
                sh test + 'something else'
                }
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
