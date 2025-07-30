pipeline {
  agent any

  tools {
    nodejs 'node20' // Use your configured NodeJS tool
  }

  parameters {
    string(name: 'DEPLOY_VERSION', defaultValue: 'v1.0', description: 'Deployment version tag')
    string(name: 'BRANCH_NAME', defaultValue: 'main', description: 'Git branch to deploy')
    choice(name: 'ENV', choices: ['dev', 'staging', 'prod'], description: 'Deployment environment')
  }

  stages {
    stage('Checkout Code') {
      steps {
        git credentialsId: 'github-token',
            url: 'https://github.com/Tushar-Sankey/jenkins-react-deploy.git',
            branch: "${params.BRANCH_NAME}"
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

    stage('Version Info') {
      steps {
        echo "✅ Deploying version: ${params.DEPLOY_VERSION} to environment: ${params.ENV}"
      }
    }
  }

  post {
    success {
      echo "✅ Build and version tagging complete!"
    }
    failure {
      echo "❌ Build failed — rollback logic will go here later"
    }
  }
}
