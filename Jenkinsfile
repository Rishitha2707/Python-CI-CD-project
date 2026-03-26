pipeline {
    agent any

    environment {
        APP_NAME = "devops-app"
        PORT = "5000"
    }

    stages {

       stage('clone') {
           steps {
               git 'https://github.com/Rishitha2707/Python-CI-CD-project.git'
           }
       }

       stage('Build') {
           steps {
               sh 'docker build -t $APP_NAME .'
           }
       }

       stage('Test') {
           steps {
               sh 'docker run --rm $APP_NAME pytest'
           }
       }

       stage('Deploy') {
           steps {
               sh '''
               docker stop $APP_NAME || true
               docker rm $APP_NAME || true
               docker run -d -p $PORT:$PORT --name $APP_NAME $APPNAME
               '''
           }
        }
    }
}
