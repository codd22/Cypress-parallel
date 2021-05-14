pipeline {
    agent any

    tools {nodejs "node"}

    stages {
        stage('Dependencies') {
            steps {
                sh 'npm i'
            }
        }
        stage('cypress verify') {
            steps {
                sh 'npm run cy:verify'
            }
        }
        stage('e2e Tests') {
            steps {
                sh 'npm run test'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
