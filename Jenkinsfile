pipeline {
    agent any 
    parameters {
      gitParameter branch: 'main', branchFilter: 'origin/(.*)', defaultValue: 'main', name: 'BRANCH', type: 'PT_BRANCH'
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
    }
}
