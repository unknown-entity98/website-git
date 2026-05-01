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
                    expression {
        return env.GIT_BRANCH == 'origin/master'
    }
            }
            steps {
                sh 'docker run -d -p 8083:80 mywebapp'
            }
        }
    }
}
