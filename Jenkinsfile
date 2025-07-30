pipeline {
  agent any

  tools {
    nodejs 'node20'  // Node.js tool name you configured in Jenkins
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

    stage('Build') {
      steps {
        sh 'npm run build'
      }
    }

    // Optional: Add Deploy stage next
  }
}
