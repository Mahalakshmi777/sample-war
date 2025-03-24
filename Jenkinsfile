pipeline {
    agent any

    environment {
        // Define Tomcat path and WAR file name
        TOMCAT_HOME = '/opt/tomcat'  // Replace with your actual Tomcat path
        TOMCAT_PORT = '8080'
        WAR_FILE = 'sample-war.war'  // The name of the WAR file to be deployed
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout the repository from GitHub
                git 'https://github.com/<your-username>/sample-war.git'
            }
        }

        stage('Build with Maven') {
            steps {
                script {
                    // Build the project using Maven to generate the WAR file
                    sh 'mvn clean package'
                }
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                script {
                    // Copy the WAR file to Tomcat's webapps directory
                    sh """
                        cp target/${WAR_FILE} ${TOMCAT_HOME}/webapps/
                    """
                }
            }
        }

        stage('Verify Deployment') {
            steps {
                script {
                    // Verify if the WAR file is deployed and accessible
                    echo "Check your browser at http://localhost:${TOMCAT_PORT}/sample-war"
                }
            }
        }
    }

    post {
        always {
            // Clean up or notification logic (optional)
            echo "Pipeline completed"
        }
    }
}
