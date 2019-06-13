pipeline {
  agent any
  stages {
    stage('Integration of latest code') {
      parallel {
        stage('Integration of latest code') {
          steps {
            echo 'Integration of latest code'
          }
        }
        stage('Verifying the push') {
          steps {
            echo 'Push is verified'
            mail(subject: 'Integration', body: 'Integration', cc: 'aditya.madhira@synaptics.com', from: 'aditya.madhira@synaptics.com', replyTo: ' ', to: 'kmurray@cloudbees.com')
          }
        }
      }
    }
    stage('Generate release package') {
      parallel {
        stage('Generate release package') {
          steps {
            echo 'Generated release package'
          }
        }
        stage('Release stage') {
          steps {
            pwd(tmp: true)
          }
        }
      }
    }
    stage('Autobuild') {
      parallel {
        stage('Autobuild') {
          steps {
            echo 'Completed auto build'
          }
        }
        stage('Auto build') {
          steps {
            archiveArtifacts(artifacts: 'test', fingerprint: true)
          }
        }
        stage('Define node') {
          steps {
            node(label: 'cjoc-pod-maven')
          }
        }
      }
    }
    stage('Auto Test') {
      parallel {
        stage('Auto Test') {
          steps {
            echo 'Completed auto test'
          }
        }
        stage('') {
          steps {
            echo 'Test completed'
          }
        }
      }
    }
  }
}