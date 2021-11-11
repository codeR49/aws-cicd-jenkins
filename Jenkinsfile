pipeline {
     agent any
     stages {
         stage('Build') {
              steps {
                  sh 'echo Building...'
              }
         }
         stage('Lint App.py') {
            steps {
                sh 'tidy -q -e *.py'
            }
        }
         stage('Build Docker Image') {
              steps {
                  sh 'docker build -t hello-flask-app .'
              }
         }
         stage('Push Docker Image') {
              steps {
                  withDockerRegistry([url: "", credentialsId: "dockerhub"]) {
                      sh "docker tag hello-flask-app mydocker49/hello-flask-app"
                      sh 'docker push mydocker49/hello-flask-app'
                  }
              }
         }
     }
}