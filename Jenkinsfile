pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                sh 'docker build -t mywebapp .'
            }
        }

        stage('Test') {
            steps {
                echo "Running tests..."
            }
        }

        stage('Deploy to Prod') {
            when {
                branch 'master'
            }
            steps {
                sh 'docker run -d -p 8083:80 mywebapp'
            }
        }
    }
}
