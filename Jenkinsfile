pipeline {
    
    agent {
        docker { image 'python3:3.7- alpine' }
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
