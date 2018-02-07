pipeline {
  agent any
  stages {
    stage('Jekyll') {
      parallel {
        stage('Jekyll') {
          steps {
            sh './ci/jekyll'
          }
        }
        stage('RSpec') {
          steps {
            sh 'bundle exec rspec'
          }
        }
        stage('SASS') {
          steps {
            sh './ci/sass_lint'
          }
        }
      }
    }
  }
}
