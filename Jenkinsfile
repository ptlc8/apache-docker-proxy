pipeline {
    agent any

    parameters {
        string(name: 'TOPDOMAIN', defaultValue: params.TOPDOMAIN ?: null, description: 'Top level domain')
        string(name: 'HTTP_PORT', defaultValue: params.HTTP_PORT ?: null, description: 'Port to listen on')
        string(name: 'HTDOCS_DIRECTORY', defaultValue: params.HTDOCS_DIRECTORY ?: null, description: 'Directory to serve files from')
        string(name: 'DEFAULT_REDIRECT_TO_TOPDOMAIN', defaultValue: params.DEFAULT_REDIRECT_TO_TOPDOMAIN ?: null, description: 'Redirect other domains to top domain')
        string(name: 'REDIRECT_TO_SECURE', defaultValue: params.REDIRECT_TO_SECURE ?: null, description: 'Redirect to secure protocol')
        string(name: 'IGNORE_PATHS', defaultValue: params.IGNORE_PATHS ?: null, description: 'Paths to ignore when proxying on top domain')
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
