pipeline {
    agent any

    tools {
        nodejs "node16"  // Must match the name given in Global Tool Config
    }

    environment {
        IMAGE_NAME = "192.168.29.254:5000/react-app"
    }

    stages {
        stage('Clone Repo') {
            steps {
                echo "Cloning repository..."
                git branch: 'main', url: 'https://github.com/harjit23/cicd-test-react.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build React App') {
            steps {
                sh 'npm run build'
            }
        }

        stage('Docker Build & Push') {
            steps {
                sh """
                    docker build -t $IMAGE_NAME:latest .
                    docker push $IMAGE_NAME:latest
                """
            }
        }

        stage('Deploy Container') {
            steps {
                sh """
                    docker rm -f react-app || true
                    docker run -d -p 3000:80 --name react-app $IMAGE_NAME:latest
                """
            }
        }
    }
}
