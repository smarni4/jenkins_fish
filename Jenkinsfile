pipeline {
    agent { label 'slave' }  // Runs on a specific Jenkins node with Python installed

    environment {
        VENV_DIR = 'venv' // Define the virtual environment directory
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Cloning repository...'
                checkout scm
            }
        }

        stage('Setup Python Environment') {
            steps {
                echo 'Creating and setting up virtual environment...'
                sh 'sudo apt install python3.12-venv'
		sh 'python3 -m venv ${VENV_DIR}'
                sh 'source ${VENV_DIR}/bin/activate && pip install -r requirements.txt'
            }
        }

        stage('Run app') {
            steps {
                echo 'Running app'
                sh 'source ${VENV_DIR}/bin/activate && python3 app.py'
            }
        }
    }
}


