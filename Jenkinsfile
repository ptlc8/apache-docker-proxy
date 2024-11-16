pipeline {
    agent any

    parameters {
        string(name: 'TOPDOMAIN', description: 'Top level domain')
    }

    stages {
        stage('Deploy') {
            steps {
                sh 'docker compose up -d --remove-orphans'
            }
        }
    }
}
