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
                sh 'cp -r /root/var/lib/jenkins/workspace/pipe_line peoject/target/petshop.war /root/var/lib/tomcat10/webapps/'
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
