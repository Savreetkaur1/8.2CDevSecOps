pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Savreetkaur1/8.2CDevSecOps.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'npm test'
            }
        }

        stage('Generate Coverage Report') {
            steps {
                bat 'npm run coverage'
            }
        }

        stage('NPM Audit (Security Scan)') {
            steps {
                bat 'npm audit --json > audit-results.json'
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: 'audit-results.json', fingerprint: true
        }

        failure {
            mail to: 'YOUR_EMAIL@gmail.com',
                 subject: "Jenkins Build Failed: ${env.JOB_NAME}",
                 body: "Build ${env.BUILD_NUMBER} has failed. Please check the Jenkins console for more information."
        }
    }
}
