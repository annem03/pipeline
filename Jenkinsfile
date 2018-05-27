pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean packag'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
                sh 'sleep 180'
            }
            post {
                always {
                    junit '/var/lib/jenkins/workspace/pipeline-test/single-module/target/surefire-reports/*.xml'
                }
            }
        }
    }
}
