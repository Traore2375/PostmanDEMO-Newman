pipeline {
    agent any

    stages {

        stage('Run API Tests') {
            steps {
                bat '''
                newman run collection.json ^
                -e environment.json ^
                -d data.json ^
                -r cli,htmlextra ^
                --reporter-htmlextra-export newman-report.html
                '''
            }
        }
    }
}