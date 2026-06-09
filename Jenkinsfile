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
              deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: '5e99610c-02ed-4dba-8322-12aae216beed', path: '', url: 'http://65.2.140.98:8085/')], contextPath: 'hello', war: '**/*.war'  
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
