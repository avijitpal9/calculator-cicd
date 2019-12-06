pipeline {
    
    agent {
        kubernetes {
        label "jenkins-slave"
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
                sh "python3 -m venv venv"
                sh ". venv/bin/activate"
                sh "pip install -r requirements.txt"

            }
        }

        stage("Run Test") {
            steps {
                echo "Run Test"
            }
        }
    }
}
