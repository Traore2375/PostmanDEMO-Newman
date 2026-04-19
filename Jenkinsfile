pipeline {
    agent any

    stages {

        stage('Clean & Prepare') {
            steps {
                bat 'if exist reports rmdir /s /q reports'
                bat 'mkdir reports'
            }
        }

        stage('Run API Tests') {
            steps {
                bat '''
                newman run SimpleDemo.postman_collection.json ^
                -e QA.postman_environment.json ^
                -d data.json ^
                -r cli,htmlextra ^
                --reporter-htmlextra-export reports\\newman-report.html
                '''
            }
        }

        stage('Debug Files') {
            steps {
                bat 'dir'
                bat 'dir reports'
            }
        }

        stage('Publish Report') {
            steps {
                publishHTML([
                    reportDir: 'reports',
                    reportFiles: 'newman-report.html',
                    reportName: 'Newman Report',
                    keepAll: true,
                    alwaysLinkToLastBuild: true,
                    allowMissing: false
                ])
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: 'reports/**'
        }
    }
}