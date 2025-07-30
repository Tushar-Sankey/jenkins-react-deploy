pipeline {
  agent any

  parameters {
    string(name: 'DEPLOY_VERSION', defaultValue: 'v1.0', description: 'Version to deploy')
    string(name: 'BRANCH_NAME', defaultValue: 'main', description: 'Branch to build')
    choice(name: 'ENV', choices: ['dev', 'staging', 'prod'], description: 'Target environment')
  }

  stages {
    stage('Echo Inputs') {
      steps {
        echo "Building version ${params.DEPLOY_VERSION}"
        echo "From branch ${params.BRANCH_NAME}"
        echo "For environment ${params.ENV}"
      }
    }
  }
}
