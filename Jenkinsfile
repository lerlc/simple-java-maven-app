pipeline {
    agent any
    tools{
        maven 'Maven 3.5.4'
    }
    stages {
        stage('Build') { 
            steps {
                sh 'mvn -B -DskipTests clean package -X' 
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage('Deliver') {
            steps {
                sh './jenkins/scripts/deliver.sh'
            }
        }
    }
}
