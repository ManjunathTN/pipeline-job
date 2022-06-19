pipeline {
    agent { docker 'public.ecr.aws/docker/library/golang:latest' }
    environment {
      GOCACHE = "${env.WORKSPACE}/.build_cache"
    }
    stages {
        stage('Source') {
            steps {
                bat 'which go'
                bat 'go version'
                git branch: 'stable',
                    url: 'https://github.com/ManjunathTN/pipeline-job.git'
            }
        }
        stage('Build') {
            steps {
                bat "go build --tags extended"
            }
        }
        stage('Test') {
            steps {
                bat './hugo env'
            }
        }
    }
}
