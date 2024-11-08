pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                git url: 'https://github.com/JudahJacinth/simple-node-project-2.git', branch: 'main'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build("simple-node-project")
                }
            }
        }
        stage('Run Build Lifecycle') {
            steps {
                script {
                    dockerImage.inside('-p 3000:3000') {
                        sh 'npm install'
                        sh 'npm run build'
                        sh 'npm test'
                        sh 'npm start & sleep 10'
                    }
                }
            }
        }
    }
}
