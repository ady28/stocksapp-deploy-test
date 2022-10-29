pipeline {
    agent {
        node {
            label 'master'
        }
    }
    options {
        ansiColor('xterm')
    }
    environment {
        INTERNAL_REGISTRY = 'lnx1:5000'
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
                withCredentials([[$class: 'UsernamePasswordMultiBinding', credentialsId:'PrivateDockerCreds', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD']]) {
                    sh('echo $PASSWORD | docker login --username $USERNAME --password-stdin $INTERNAL_REGISTRY')
                    sh('docker stack deploy --compose-file docker-compose.yaml stocksapp --with-registry-auth')
                    sh('docker logout $INTERNAL_REGISTRY')
                }
            }
        }
    }
}