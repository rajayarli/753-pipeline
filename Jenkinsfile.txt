pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo "Building with Maven"
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo "Running tests with JUnit and Mockito"
            }
        }
        stage('Code Analysis') {
            steps {
                echo "Analyzing code with SonarQube"
            }
        }
        stage('Security Scan') {
            steps {
                echo "Scanning for vulnerabilities with OWASP ZAP"
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo "Deploying to AWS EC2 staging instance"
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo "Running integration tests in staging environment"
            }
        }
        stage('Deploy to Production') {
            steps {
                echo "Deploying to AWS EC2 production instance"
            }
        }
    }
    post {
        always {
            mail to: 'rajarameshy1@gmail.com',
                 subject: "Build ${currentBuild.fullDisplayName}",
                 body: "The result of build is: ${currentBuild.currentResult}"
        }
    }
}
