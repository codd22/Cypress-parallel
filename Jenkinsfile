pipeline {
  agent any

    tools {nodejs "node"}

  stages {
    stage('Dependencies') {
      steps {
        sh 'npm i'
      }
    }
    stage('e2e Tests') {
      parallel {
        stage('machine 1') {
          steps {
            sh 'npm run test "$(CI_NODE_INDEX=1 CI_NODE_TOTAL=2 node scripts/cypress-parallel.js)"'
          }
        }
        stage('machine 2') {
          steps {
            sh 'npm run test "$(CI_NODE_INDEX=2 CI_NODE_TOTAL=2 node scripts/cypress-parallel.js)"'
          }
        }
      }
    }
    stage('Deploy') {
      steps {
        echo 'Deploying....'
      }
    }
  }
}