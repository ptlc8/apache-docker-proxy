pipeline {
    agent any

    parameters {
        string(name: 'TOPDOMAIN', description: 'Top level domain')
        string(name: 'DEFAULT_REDIRECT_TO_TOPDOMAIN', description: 'Redirect other domains to top domain', defaultValue: 'false')
        string(name: 'REDIRECT_TO_SECURE', description: 'Redirect to secure protocol', defaultValue: 'false')
        string(name: 'HTTP_PORT', description: 'Port to listen on', defaultValue: '80')
    }

    stages {
        stage('Build') {
            steps {
                sh 'docker compose build'
            }
        }
        stage('Deploy') {
            steps {
                sh 'docker compose up -d --remove-orphans'
            }
        }
    }
}
