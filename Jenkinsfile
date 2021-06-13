pipeline {
    agent any 
    parameters {
      gitParameter branch: 'main', branchFilter: 'origin/(.*)', defaultValue: 'main', name: 'BRANCH', type: 'PT_BRANCH'
    }
    environment { 
        imageName = "a12d/simple-app" 
        registryCredentialSet = 'dockerhub'
    }
    stages {
        stage('say hello') {
          steps {
            echo 'Hello World'
          }
        }
        stage('Cloning git') {
          steps {
            git  branch: "${params.BRANCH}", url: 'https://github.com/a12d/simple-app.git'
          }
        }
        stage('Building image') {
          steps {
            sh """
              docker build -t simple_app .
              """
          }
        }
        stage('Push image') {
steps {
sh """ 
docker tag simple-app localhost:5000/simple-app
docker push localhost:5000/simple-app
"""
}
    }
}
}
