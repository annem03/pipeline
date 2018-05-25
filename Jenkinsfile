pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
                sh 'sleep 60'
            }
            post {
                always {
                    junit '/var/lib/jenkins/workspace/pipeline-test/single-module/target/surefire-reports/*.xml'
                }
            }
        }
    }
}
