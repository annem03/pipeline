pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
                sh 'echo testing'
            }
        }
        stage('Test') {
            input {
                message "should i continue"
                ok "ok"
                submitter "admin"
            }
            steps {
                sh 'mvn test'
                sh 'sleep 60'
                sh 'echo testing123'
            }
            post {
                always {
                    junit '/var/lib/jenkins/workspace/pipeline-test/single-module/target/surefire-reports/*.xml'
                }
            }
        }
    }
}
