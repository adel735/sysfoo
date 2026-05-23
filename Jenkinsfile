pipeline {
  agent none
  stages {
    stage('Build') {
      agent {
        docker {
          image 'maven:3.9.6-eclipse-temurin-17-alpaine'
        }

      }
      steps {
        echo 'Building...'
        sh 'mvn compile'
      }
    }

    stage('Test') {
      agent {
        docker {
          image 'maven:3.9.6-eclipse-temurin-17-alpaine'
        }

      }
      steps {
        echo 'Testing...'
        sh 'mvn clean test'
      }
    }

    stage('Deploy') {
      agent {
        docker {
          image 'maven:3.9.6-eclipse-temurin-17-alpaine'
        }

      }
      steps {
        echo 'Deploying...'
        sh '''GIT_SHORT_COMMIT=$(echo $GIT_COMMIT | cut -c 1-7)

mvn versions:set -DnewVersion="$GIT_SHORT_COMMIT"
mvn versions:commit'''
        sh 'mvn package -DskipTests'
        archiveArtifacts '**/target/*.jar'
      }
    }

  }
  tools {
    maven 'maven'
  }
}