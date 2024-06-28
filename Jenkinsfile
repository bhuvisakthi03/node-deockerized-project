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
                sh 'apt-get npm install'
                sh 'npm test'
            }
        }

        stage('Build'){
            steps{
                sh 'npm run build'
            }
        }
    }
}
    
