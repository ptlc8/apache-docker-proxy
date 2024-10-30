pipeline {
    agent any

    parameters {
        string(name: 'TOPDOMAIN', description: 'Top level domain')
    }

    stages {
        stage('Build') {
            steps {
                sh 'docker compose build'
            }
        }
        stage('Deploy') {
            steps {
                sh 'docker compose down --remove-orphans'
                sh 'docker compose up -d'
            }
        }
    }
}
