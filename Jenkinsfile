pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                sh '''
                  rm -rf *
                  git clone https://github.com/priya027v/hello-world-war
                '''
            }
        }

        stage('Build') {
            steps {
                sh '''
                  cd hello-world-war
                  mvn clean package
                '''
            }
        }

        stage('Deploy to JFrog') {
        steps {
        withCredentials([
            usernamePassword(
                credentialsId: 'jfrog',
                usernameVariable: 'JFROG_USER',
                passwordVariable: 'JFROG_PASS'
            )
        ]) {
                sh '''
                  cd hello-world-war
                  mvn deploy
                '''
            }
        }
    }
  }
}
