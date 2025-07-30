pipeline {
  agent any

  tools {
    nodejs 'node20'   // Matches the name you gave in NodeJS tool config
  }

  stages {
    stage('Clone Repo') {
      steps {
        git credentialsId: 'github-token', url: 'https://github.com/Tushar-Sankey/jenkins-react-deploy.git', branch: 'main'
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

    stage('Post Build') {
      steps {
        echo '✅ React app build complete!'
      }
    }
  }
}
