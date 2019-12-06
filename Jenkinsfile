pipeline {
    
    agent {
        kubernetes {
        label "jenkins-slave"
        defaultContainer "python3"
        yaml """
                kind: Pod
                metadata:
                  name: jenkins-slave
                spec:
                  containers:
                  - name: python3
                    image: python:3.7-alpine
                    imagePullPolicy: Always
                    command:
                    - /bin/sh
                    tty: true
            """
   }
    }

    stages {
        stage("Setup ENV") {
            steps {
                sh "python -m venv venv"
                sh ". venv/bin/activate"
                sh "pip install -r requirements.txt"

            }
        }

        stage("Linting") {
            steps {
                sh ". venv/bin/activate"
                sh "flake8 --exclude=venv* --statistics"
            }
        }

        stage("Run Test") {
            steps {
                sh ". venv/bin/activate"
                sh "pytest -v --cov=calculator"
            }
        }
    }
}
