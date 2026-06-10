pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/ajaypasili/pet_shop.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Deploy') {
            steps {
                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: '7274cd61-f12b-479c-8e49-7718b719a801', path: '', url: 'http://13.220.129.213:8090/')], contextPath: 'petshop', war: '**/*.war'
            }
        }
    }

    post {
        success {
            echo 'Application deployed successfully'
        }

        failure {
            echo 'Pipeline failed'
        }
    }
}
