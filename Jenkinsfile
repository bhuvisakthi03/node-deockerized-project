pipeline{
    agent any
    stages{
        stage("checkout"){
            steps{
                checkout scm
            }
        }

        stage("Test"){
            steps{
                sh ' npm install'
                sh 'npm test'
            }
        }

        stage('Build'){
            steps{
                sh 'npm run build'
            }
        }
        stage('Build Image'){
            steps{
                sh 'export DOCKER_BUILDKIT=1'
                sh 'docker build  -t my-node-app .'
            }
        }
         stage('Docker Push'){
            steps{
                withCredentials([usernamePassword(credentialsId: 'docker_cred', passwordVariable: 'DOCKERHUB_PASSWORD', usernameVariable: 'DOCKERHUB_USERNAME')]) {
                    sh 'docker login -u $DOCKERHUB_USERNAME -p $DOCKERHUB_PASSWORD'
                    sh 'docker tag my-node-app bhuvi03/my-node-app'
                    sh 'docker push bhuvi03/my-node-app:1.0'
                    sh 'docker logout'
                    
                }
            }
        }
    }
}
    
