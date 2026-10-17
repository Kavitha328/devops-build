pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                sh 'docker build -t app-image .'
            }
        }

        stage('Push DEV') {

            when {
                branch 'dev'
            }

            steps {

                sh '''
                docker tag app-image mydockerhub/dev-repo:latest
                docker push mydockerhub/dev-repo:latest
                '''
            }
        }

        stage('Push PROD') {

            when {
                branch 'master'
            }

            steps {

                sh '''
                docker tag app-image mydockerhub/prod-repo:latest
                docker push mydockerhub/prod-repo:latest
                '''
            }
        }
    }
}
