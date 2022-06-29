pipeline {
    environment {
        registry = "docker_hub_account/repository_name"
        registryCredential = ‘dockerhub’
        dockerImage = ''
    agent any

    stages {
        stage('Build image') {
            steps {
                echo 'Building docker image..'
                script{
                    dockerImage = docker.build registry + ":$BUILD_NUMBER"
                
                }    
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy.. push image to docker registry') {
            steps {
                echo 'Deploying....pushing image to docker registry'
                script {
                    docker.withRegistry( '', registryCredential ) {
                    dockerImage.push("$BUILD_NUMBER")
                    dockerImage.push('latest')
}
            }
        }
    }
}
