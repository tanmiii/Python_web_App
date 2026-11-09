pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo "Build Docker Image"
                bat "wsl docker build -t mypythonflaskapp.py ."
            }
        }
        stage('Run') {
            steps {
                echo "Run application in Docker Container"
                bat "wsl docker rm -f mycontainer || exit 0"
                bat "wsl docker run -d -p 5000:5000 --name mycontainer mypythonflaskapp"
            }
        }
    }
    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Please check the logs.'
        }
    }
}
