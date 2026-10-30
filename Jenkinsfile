pipeline {
    agent any
    stages {
        stage('Run Python in Docker') {
            steps {
                bat 'docker run --rm python:3.14.7-alpine3.24 python --version'
            }
        }
    }
}
