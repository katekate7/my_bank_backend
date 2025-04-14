pipeline {
    agent {
        node {
            label 'jenkins_agent_composer'
        }
    }

    stages {
         stage('CI') {
            steps {
                git branch: 'main', url: 'https://github.com/katekate7/BankBank.git'
                sh '''
                    cd mon-projet
                    composer install
                    php bin/phpunit
                '''
            }
        }
    }
}