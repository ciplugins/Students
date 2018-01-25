pipeline {
  agent any
  stages {
    stage('Checkout') {
      parallel {
        stage('Checkout') {
          steps {
            echo 'Checking out...'
            echo 'Checked out'
          }
        }
        stage('Clone') {
          steps {
            git(url: 'https://github.com/ciplugins/Students.git', branch: 'master')
          }
        }
      }
    }
    stage('Build') {
      steps {
        sh 'echo "Compile"'
      }
    }
    stage('Qualify Build') {
      parallel {
        stage('Qualify Build') {
          steps {
            sh 'echo "Start Qualifying it"'
          }
        }
        stage('Unit Tests') {
          steps {
            sh 'echo "Run Unit Tests"'
          }
        }
        stage('Static Code Analysis') {
          steps {
            sh 'echo "Static Code Analysis"'
          }
        }
        stage('Security Vulnerability') {
          steps {
            sh 'echo "Security Vulnerability Testing"'
          }
        }
      }
    }
    stage('Repo Creation') {
      steps {
        sh 'echo "Creating and Deploying Artifact"'
      }
    }
    stage('QA Environment') {
      parallel {
        stage('QA Environment') {
          steps {
            sh 'echo "Promote to QA"'
          }
        }
        stage('Acceptance Tests') {
          steps {
            sh 'echo "Running acceptance tests"'
          }
        }
        stage('Regression Tests') {
          steps {
            sh 'echo "Running regression tests"'
          }
        }
      }
    }
    stage('Qualify QA') {
      steps {
        sh 'echo "Qualifying QA Environment"'
      }
    }
  }
}