pipeline {
    agent any
    environment {
        PATH = "$PATH:/usr/bin/python3:/usr/bin/pip"
        SUDO_PASSWORD = credentials('change')
    }
    stages {
        stage('Build') {
            steps {
                script {
                    // Mettre à jour et installer python3-venv en utilisant sudo avec le mot de passe
                    sh '''
                    echo $SUDO_PASSWORD | sudo -S apt update
                    echo $SUDO_PASSWORD | sudo -S apt install -y python3-venv
                    '''
                    // Créer et activer un environnement virtuel
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

