pipeline {
  agent {
    docker {
      image 'maven:alpine'
    }
    
  }
  stages {
    stage('Build') {
      steps {
        sh 'mvn validate'
      }
    }
    stage('Test Unitaires') {
      steps {
        parallel(
          "Test Unitaires": {
            sh 'mvn test'
            junit '**/*.xml'
            
          },
          "Test Fonctionnels": {
            sleep 20
            
          },
          "Test integration": {
            sleep 5
            
          }
        )
      }
    }
    stage('MEP ?') {
      steps {
        input(message: 'On va en prod ?', id: 'prod', ok: 'Yeah')
      }
    }
    stage('Mep') {
      steps {
        echo 'On est en prod'
      }
    }
  }
}