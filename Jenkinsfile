pipeline {  
    environment {
    registry = "abhilashup/calculator"
    registryCredential = 'dockerhub'
  }  
  agent any  
  stages {
    stage('Build') {
      steps{
        script {
          dockerImage = docker.build registry + ":latest"
        }
      }
    }
    stage('Test'){
        steps {
            bat 'python test_calc.py'
        }
    }
    stage('Archive'){
        steps{
            script {
                docker.withRegistry( '', registryCredential){
                dockerImage.push()
                }
            }
        }
    }
  }
}
