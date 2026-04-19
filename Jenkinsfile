pipeline {
    agent any

    stages {

        stage('Prepare Folder') {
            steps {
                bat 'if not exist reports mkdir reports'
            }
        }

        stage('Run API Tests') {
            steps {
                bat '''
                newman run SimpleDemo.postman_collection.json ^
                -e QA.postman_environment.json ^
                -d data.json ^
                -r cli,htmlextra ^
                --reporter-htmlextra-export reports/newman-report.html
                '''
            }
        }

        stage('Publish Report') {
            steps {
                publishHTML([
                    reportDir: 'reports',
                    reportFiles: 'newman-report.html',
                    reportName: 'Newman API Report',
                    keepAll: true,
                    alwaysLinkToLastBuild: true
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