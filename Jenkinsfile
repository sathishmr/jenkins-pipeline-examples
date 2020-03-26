#!groovy

pipeline {
options { disableConcurrentBuilds() }
  agent any

  environment {
    git_commit_message = ''
    git_commit_diff = ''
    git_commit_author = ''
    git_commit_author_name = ''
    git_commit_author_email = ''
 }

  stages {
     stage("read vault key") {
            steps {
              withCredentials([usernamePassword(credentialsId: 'mylogin', passwordVariable: 'pass', usernameVariable: 'user')]) {
    // some block
}
                echo "${user}"
                 echo "${pass}"
            }
        }

    // Build
    stage('Build') {
      agent {
        label 'master'
      }
      steps {
        deleteDir()
        checkout scm
      }
    }

    // Static Code Analysis
    stage('Static Code Analysis') {
      agent {
        label 'master'
      }
      steps {
        deleteDir()
        checkout scm
        sh "echo 'Run Static Code Analysis'"
      }
    }

    // Unit Tests
    stage('Unit Tests') {
      agent {
        label 'master'
      }
      steps {
        deleteDir()
        checkout scm
        sh "echo 'Run Unit Tests'"
      }
    }

    // Acceptance Tests
    stage('Acceptance Tests') {
      agent {
        label 'master'
      }
      steps {
        deleteDir()
        checkout scm
        sh "echo 'Run Acceptance Tests'"
      }
    }

  }
 
}
