pipeline {
    agent any 
    stages {
        stage('say hello') {
          echo 'Hello World'
        }
        stage('Cloning git') {
          steps {
            git 'https://github.com/a12d/simple-app.git'
          }
        }
    }
}
