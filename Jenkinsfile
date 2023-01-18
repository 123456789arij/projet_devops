pipeline {
    agent none
    environment {
        DOCKERHUB_CREDENTIALS = credentials('dh_cred')
    }
    stages {
         stage('Checkout'){
            agent any
            steps{
                //Changez avec votre lien github
                git branch: 'main', url: 'https://github.com/123456789arij/projet_devops.git'
            }
        }
        stage('Init'){
            agent any
            steps{
            sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }


   stage('Build backend') {
            agent any
            steps {
                dir('ELearningManagement - backend'){
                    sh 'docker build -t arijabid/backend:$BUILD_ID .'
                    sh 'docker push arijabid/backend:$BUILD_ID'
                    sh 'docker rmi arijabid/backend:$BUILD_ID'
                    sh 'docker logout'
                }
            }
        }



         stage('Build frontend') {
            agent any

            steps {
                dir('ELearningManagement - fontend'){
                    sh 'docker build -t arijabid/frontend:$BUILD_ID .'
                    sh 'docker push arijabid/frontend:$BUILD_ID'
                    sh 'docker rmi arijabid/frontend:$BUILD_ID'
                    sh 'docker logout'
                }
            }
        }
     
    }
}