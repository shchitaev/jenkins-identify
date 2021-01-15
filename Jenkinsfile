pipeline {
    agent { 
        docker { 
            image 'python:3.8.0' 
            args '-u root:root -p 8000:8000'
        } 
    }
    stages {
        stage('Git') {
            steps {
               git branch: 'main', url: 'https://github.com/shchitaev/jenkins-identify'
            }
        }
        stage('Build') {
            steps {
                sh 'python --version'
                sh 'python -c "import this"'
                sh '/usr/local/bin/python3 -m venv --clear /home'
                sh 'pip install --upgrade pip'
                sh 'pip install pytest'
                sh 'pip install -r requirements.txt'
            }
        }
        stage ('Test') {
            steps {
                sh 'cd app'
                sh 'pytest'
            }
        }
    }
}
