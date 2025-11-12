pipeline {
  agent none
  stages {
    stage('Build') {
      agent {
        docker {
          image 'maven:3.9.6-eclipse-temurin-17-alpine'
        }

      }
      steps {
        echo 'Compiling sysfo app'
        sh 'mvn compile'
      }
    }

    stage('test') {
      agent {
        docker {
          image 'maven:3.9.6-eclipse-temurin-17-alpine'
        }

      }
      steps {
        echo 'runnig unit test..'
        sh 'mvn clean test'
      }
    }

    stage('package') {
      steps {
        echo 'packaging the app...'
        sh '''# Truncate the GIT_COMMIT to the first 7 characters
GIT_SHORT_COMMIT=$(echo $GIT_COMMIT | cut -c 1-7)

# Set the version using Maven
mvn versions:set -DnewVersion="$GIT_SHORT_COMMIT"
mvn versions:commit
'''
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