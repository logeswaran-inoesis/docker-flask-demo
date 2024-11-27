pipeline {
    agent any 
    environment {
    DOCKERHUB_CREDENTIALS = credentials('logeswaran1-dockerhub')
    }
    stages { 

        stage('Build docker image') {
            steps {  
                sh 'docker build -t ylmt/flaskapp:$BUILD_NUMBER .'
            }
        }
        stage('login to dockerhub') {
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('push image') {
            steps{
                sh 'docker push ylmt/flaska:2'
            }
        }
}
post {
        always {
            sh 'docker logout'
        }
    }
}
