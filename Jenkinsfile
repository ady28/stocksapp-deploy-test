pipeline {
    agent {
        node {
            label 'master'
        }
    }
    options {
        ansiColor('xterm')
    }
    stages {
        stage('Check Docker Compose YAML file') {
            steps {
                sh 'docker-compose config > null'
            }
        }
        stage('DeployTest'){
            steps {
                echo "Deploying the stocks app for testing"
                sh('docker stack deploy --compose-file docker-compose.yaml stocksapp')
            }
        }
    }
}