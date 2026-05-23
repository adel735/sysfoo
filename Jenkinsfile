pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Building...'
        sh 'mvn compile'
      }
    }

    stage('Test') {
      steps {
        echo 'Testing...'
        sh 'mvn clean test'
      }
    }

    stage('Deploy') {
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