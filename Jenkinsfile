pipeline {
    agent any
    stages {
        stage('Setup') {
            steps {
                script {
                    // Créer et activer un environnement virtuel
                    sh 'python -m venv venv'
                    sh '. venv/bin/activate'
                    // Installer pandas
                    sh 'pip install pandas'
                }
            }
        }
        stage('Run Script') {
            steps {
                script {
                    // Activer l'environnement virtuel et exécuter le script Python
                    sh '. venv/bin/activate && python data_analysis.py'
                }
            }
        }
    }
}

