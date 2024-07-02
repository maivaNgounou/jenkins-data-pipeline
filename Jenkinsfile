pipeline {
    agent any
    environment {
        PATH = "$PATH:/usr/bin/python3:/usr/bin/pip"
        // le chemin d'accès doit inclure le chemin où 'python3' et 'pip' sont installés
    }
    stages {
        stage('Build') {
            steps {
                script {
                    // Créer et activer un environnement virtuel
                    sh 'sudo apt update && sudo apt install -y python3-venv'
                    sh 'python3 -m venv pythenv'
                    sh '. pythenv/bin/activate && pip install --upgrade pip'
                    // Installer les dépendances
                    sh '. pythenv/bin/activate && pip install pandas'
                    // Exécuter le script Python d'analyse de données
                    sh '. pythenv/bin/activate && python data_analysis.py'
                }
            }
        }
    }
}
