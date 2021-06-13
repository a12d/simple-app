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
            script {
              dockerImage = docker.build registry + ":$BUILD_NUMBER"
            }
          }
        }
        stage('Push image') {
steps {
script {
          docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {            
          app.push("${env.BUILD_NUMBER}")            
          app.push("latest")        
              }    
}
}
         }
    }
}
