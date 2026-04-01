pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/RiturajChaudhary/jenkins-proj.git',
                    credentialsId: 'git-cred'
            }
        }

        stage('Check Files') {
            steps {
                sh 'ls -ltr'
                sh 'sudo docker ps'
            }
        }

        stage('Docker Login') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'docker-cred',
                    usernameVariable: 'DOCKER_USER',
                    passwordVariable: 'DOCKER_PASS'
                )]) {
                    sh '''
                    echo "$DOCKER_PASS" | sudo docker login -u "$DOCKER_USER" --password-stdin
                    '''
                }
            }
        }

        stage('Docker Verify') {
            steps {
                sh 'sudo docker info'
            }
        }
    }
}
