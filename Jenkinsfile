pipeline {
    agent any

    stages {

        stage('Run API Tests') {
            steps {
                bat '''
                newman run SimpleDemo.postman_collection.json ^
                -e QA.postman_environment.json ^
                -d data.json ^
                -r cli,htmlextra ^
                --reporter-htmlextra-export newman-report.html
                '''
            }
        }
    }
}