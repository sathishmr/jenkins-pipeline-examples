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
    SECRET = vault path: 'secrets', key: 'jenkins', vaultUrl: 'http://localhost:8200/', credentialsId: 'jenkins', engineVersion: "2"
  }

  stages {
     stage("read vault key") {
            steps {
                echo "${SECRET}"
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
  post {
    success {
      sh "echo 'Send mail on success'"
      // mail to:"me@example.com", subject:"SUCCESS: ${currentBuild.fullDisplayName}", body: "Yay, we passed."
    }
    failure {
      sh "echo 'Send mail on failure'"
      // mail to:"me@example.com", subject:"FAILURE: ${currentBuild.fullDisplayName}", body: "Boo, we failed."
    }
  }
}
