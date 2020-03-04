pipeline {
  agent none 
  options {
    buildDiscarder(logRotator(numToKeepStr: '2'))
    skipDefaultCheckout true
  }
  stages {
    stage('Test') {
      agent { 
        kubernetes{
          label 'nodejs-app-pod'
          yaml 'nodejs-pod.yaml' 
        }
      }
      steps {
         checkout scm
         container('nodejs') {
          echo 'Hello World!'
          sh 'node --version'
      }
    }
   }
   stage('build and push image') {
     when {
       beforeAgent true
       branch 'master'
     }
     steps {
        echo "TODO - build and push image"
  }
}
}
}
