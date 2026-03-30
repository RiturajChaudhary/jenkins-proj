pipeline {
    agent any

    stages {
        stage('Clone Git') {
            steps {
                // Remove old directory if exists
                sh 'rm -Rf jenkins-proj'

                // Clone your repo
                sh 'git clone https://github.com/RiturajChaudhary/jenkins-proj.git'
                sh 'echo "Cloned RiturajChaudhary/jenkins-proj"'

                // Verify
                sh 'pwd'
                sh 'ls -ltr'
                sh 'echo "End of Git Clone Stage"'
            }
        }

        stage('Docker commands') {
            steps {
                sh 'sudo docker ps'
                sh 'sudo docker images'
            }
        }
    }

    post {
        success {
            sh 'echo "Build succeeded!"'
            sh 'echo "Build succeeded at `date`" >> susigugh-01.log'
        }
        failure {
            sh 'echo "Build failed!"'
            sh 'echo "Build failed at `date`!" >> susigugh-01.log'
        }
    }
}
