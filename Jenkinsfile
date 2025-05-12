// Jenkinsfile content
pipeline {
  agent any

  stages {
    stage('Clone Repo') {
      steps {
        echo 'Cloning repo...'
        git 'https://github.com/harjit23/hello-world-test.git'
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

    stage('Docker Build') {
      steps {
        sh 'docker build -t react-hello-world .'
      }
    }

    stage('Docker Run') {
      steps {
        sh 'docker run -d -p 3000:80 react-hello-world'
      }
    }
  }
}
