pipeline {
    agent any
    
    // 1. Variables d'environnement (Page 4 du tutoriel)
    environment {
        MON_MESSAGE = 'Bonjour depuis GitHub et Jenkins'
    }

    stages {
        stage('1. Build') {
            steps {
                // Page 2 : Utilisation de "bat" pour Windows
                bat 'echo "Démarrage du build..."'
                // Page 3 : Utilisation de Docker
                bat 'docker run --rm python:3.14.7-alpine3.24 python --version'
            }
        }
        
        stage('2. Test') {
            steps {
                // Page 4 : Affichage de la variable
                bat 'echo "Le message est : %MON_MESSAGE%"'
            }
        }
        
        stage('3. Deploy') {
            steps {
                // Page 2 : Timeout et Retry
                timeout(time: 1, unit: 'MINUTES') {
                    retry(2) {
                        bat 'echo "Déploiement simulé..."'
                    }
                }
            }
        }
    }

    // 2. Post-traitement (Page 6 et 7 du tutoriel)
    post {
        always {
            echo 'Nettoyage final du pipeline (toujours exécuté).'
            // Page 6 : Nettoyage du dossier
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
