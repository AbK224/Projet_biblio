pipeline {
    agent any

    environment {
        COMPOSE_FILE = "docker-compose.yaml"
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build containers') {
            steps {
                sh 'docker compose -f ${COMPOSE_FILE} build'
            }
        }

        stage('Start containers') {
            steps {
                sh 'docker compose -f ${COMPOSE_FILE} up -d'
            }
        }

        stage('Backend dependencies') {
            steps {
                sh 'docker compose -f ${COMPOSE_FILE} exec -T backend composer install --no-interaction --prefer-dist --optimize-autoloader'
            }
        }

        stage('Laravel setup') {
            steps {
                sh 'docker compose -f ${COMPOSE_FILE} exec -T backend php artisan key:generate --force'
                sh 'docker compose -f ${COMPOSE_FILE} exec -T backend php artisan migrate --force'
            }
        }

        stage('Frontend dependencies') {
            steps {
                sh 'docker compose -f ${COMPOSE_FILE} exec -T frontend npm install'
            }
        }

        stage('Tests') {
            steps {
                sh 'docker compose -f ${COMPOSE_FILE} exec -T backend php artisan test'
            }
        }
    }

    post {
        success {
            echo 'Pipeline exécuté avec succès.'
        }
        failure {
            echo 'Le pipeline a échoué.'
        }
        always {
            sh 'docker compose -f ${COMPOSE_FILE} ps'
        }
    }
}