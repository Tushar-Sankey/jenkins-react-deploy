pipeline {
  agent any

  parameters {
    string(name: 'DEPLOY_VERSION', defaultValue: 'v1.0', description: 'Deployment version')
    string(name: 'BRANCH_NAME', defaultValue: 'main', description: 'Git branch name to deploy')
    choice(name: 'ENV', choices: ['dev', 'staging', 'prod'], description: 'Target deployment environment')
  }

  tools {
    nodejs 'node20'  // adjust if your NodeJS tool is named differently
  }

  stages {
    stage('Clone Repo') {
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

    stage('Build') {
      steps {
        sh 'npm run build'
      }
    }

    // We'll add deploy + rollback stages later
  }
}
