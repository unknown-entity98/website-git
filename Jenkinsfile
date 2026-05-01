pipeline {
    agent any

    environment {
        IMAGE_NAME = "mywebapp"
        CONTAINER_NAME = "webapp-container"
        PORT = "8083"
    }

    stages {

        stage('Build') {
            steps {
                echo "Building Docker image..."
                sh 'docker build -t $IMAGE_NAME .'
            }
        }

        stage('Test') {
            steps {
                echo "Running tests..."
                // Add real test commands here later
            }
        }

        stage('Deploy to Prod') {
            when {
                expression {
                    return env.GIT_BRANCH == 'origin/master'
                }
            }
            steps {
                echo "Deploying to production..."

                sh '''
                docker rm -f $CONTAINER_NAME || true
                docker run -d -p $PORT:80 --name $CONTAINER_NAME $IMAGE_NAME
                '''
            }
        }
    }

    post {
        success {
            echo "Pipeline completed successfully!"
        }
        failure {
            echo "Pipeline failed. Fix it."
        }
    }
}
