pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Compiling sysfo app'
        sh 'mvn compile'
      }
    }

    stage('test') {
      steps {
        echo 'runnig unit test..'
        sh 'mvn clean test'
      }
    }

    stage('package') {
      steps {
        echo 'packaging the app...'
        sh 'mvn package -DskipTests'
        archiveArtifacts '**/target/*.jar'
      }
    }

  }
  tools {
    maven 'Maven 3.6.3'
  }
  post {
    always {
      echo 'this pipeline has completed...'
    }

  }
}