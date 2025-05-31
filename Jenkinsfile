pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Savreetkaur1/8.2CDevSecOps.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'npm install'
            }
        }

        stage('Generate Coverage Report') {
            steps {
                bat 'npm run coverage'
            }
        }

        stage('NPM Audit (Security Scan)') {
            steps {
                script {
                    def auditStatus = bat(script: 'npm audit --json > audit-results.json', returnStatus: true)
                    echo "npm audit exit code: ${auditStatus} (ignored for build failure)"
                }
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: 'audit-results.json', fingerprint: true
        }

        failure {
            mail to: 'savreet454@example.com',
                 subject: "Build Failed: ${env.JOB_NAME}",
                 body: "Build ${env.BUILD_NUMBER} failed. Check console output."
        }
    }
}
