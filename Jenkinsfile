pipeline {
  agent {
    dockerfile {
      label 'docker'
      filename './Dockerfile'
    }
  }
  stages {
    stage('Test') {
      parallel {
        stage('Jekyll') {
          steps {
            // sh './ci/jekyll'
            echo 'Commented out as the Jekyll tests are a little broken at the moment.'
          }
        }
        stage('RSpec') {
          steps {
            sh 'rspec -fd'
          }
        }
        stage('SASS') {
          steps {
            sh './ci/sass_lint'
          }
        }
      }
    }
    stage('Review') {
      when {
        not { branch 'master' }
      }
      parallel {
        stage('Browser Tests') {
          stages {
            stage ('Chrome') {
              steps {
                echo 'Hello world'
              }
            }
            stage ('Safari') {
              steps {
                echo 'Hello world'
              }
            }
            stage ('Firefox') {
              steps {
                echo 'Hello world'
              }
            }
          }
        }
        stage('Percy') {
          when {
            not { branch 'master' }
          }
          steps {
            // timeout(time: 10, unit: 'MINUTES') {
            //   input 'Ready to review the styleguide?'
            // }
            echo 'This step only runs in Codeship builds at the moment: https://app.codeship.com/projects/246808'
          }
        }
        stage('Staging') {
          steps {
            echo 'Hello world'
          }
        }
      }
    }
    stage('Deploy') {
      when { branch 'master' }
      parallel {
        stage('Update Percy') {
          steps {
            echo 'This step only runs in Codeship builds at the moment: https://app.codeship.com/projects/246808'
          }
        }
        stage('RubyGems') {
          steps {
            echo 'This step only runs in Travis CI builds at the moment: https://travis-ci.org/codeship/shipyard'
          }
        }
        stage('GitHub Pages') {
          steps {
            echo 'This step only runs in Codeship builds at the moment: https://app.codeship.com/projects/246808'
          }
        }
      }
    }
  }
}
