pipeline {
    agent any
    
    environment {
        MON_MESSAGE = 'Bonjour depuis GitHub et Jenkins'
    }

    stages {
        stage('1. Build') {
            steps {
                bat 'echo "Démarrage du build..."'
                bat 'docker run --rm python:3.14.7-alpine3.24 python --version'
            }
        }
        
        stage('2. Test') {
            steps {
                bat 'echo "Le message est : %MON_MESSAGE%"'
            }
        }
        
        stage('3. Sanity Check (Validation)') {
            steps {
                input message: "Est-ce que le build est bon pour un déploiement ?", ok: "Oui, déployer !"
            }
        }
        
        stage('4. Deploy') {
            steps {
                timeout(time: 1, unit: 'MINUTES') {
                    retry(2) {
                        bat 'echo "Déploiement simulé..."'
                    }
                }
            }
        }
    }

    post {
        always {
            echo 'Nettoyage final du pipeline (toujours exécuté).'
            deleteDir() 
        }
        success {
            echo 'Le pipeline a réussi ! (succès)'
        }
        failure {
            echo 'Le pipeline a échoué... (échec)'
        }
    }
}
