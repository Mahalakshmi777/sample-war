pipeline {
    agent any

    environment {
        TOMCAT_WEBAPPS = '/opt/tomcat/webapps'  // Adjust path if needed
    }

    stages {
        stage('Checkout Source Code') {
            steps {
                git 'https://github.com/YOUR_USERNAME/sample-war.git'
            }
        }

        stage('Build with Maven') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                sh 'cp target/*.war $TOMCAT_WEBAPPS/sample.war'
                sh 'sudo systemctl restart tomcat'
            }
        }

        stage('Show Name in Output') {
            steps {
                echo 'Deployment Done by YOUR_NAME'
            }
        }
    }
}
