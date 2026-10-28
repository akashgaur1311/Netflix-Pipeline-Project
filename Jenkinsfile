
pipeline {
    agent any

    tools {
        jdk 'JDK17'
        maven 'maven s/w'
    }

    stages {
        stage('Clone the Code') {
            steps {
                git 'https://github.com/akashgaur1311/Netflix-Pipeline-Project.git'
            }
        }

        stage('Maven Build') {
            steps {
                sh 'mvn clean package -T 1C -DskipTests'
            }
        }

        stage('Deployment Stage') {
            steps {
                script {
                    // Verify the generated WAR file
                    sh 'ls -l target'

                    // Deploy the WAR file to Tomcat
                    sh 'sudo cp target/NETFLIX-1.2.4.war /root/apache-tomcat-9.0.123/webapps/'
                }
            }
        }
    }

    post {
        always {
            echo 'Cleaning up after build...'
            cleanWs()
        }
    }
}
