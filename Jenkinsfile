pipeline {
  agent any
  stages {
    stage('Development') {
      steps {
        echo 'This is development'
        sleep 2
      }
    }

    stage('Smoke Test') {
      steps {
        echo 'Smoke UI Tests'
        echo 'Smoke Tests (API)'
      }
    }

    stage('Deploy to QA') {
      parallel {
        stage('Deploy to QA') {
          steps {
            echo 'Deploy to AWS QA Server'
          }
        }

        stage('Sleep at partitioning of QA stage') {
          steps {
            sleep 5
          }
        }

        stage('Nested QA stage') {
          steps {
            echo 'Nested stage of QA team'
          }
        }

      }
    }

    stage('Integration Test') {
      parallel {
        stage('Integration Test (UI)') {
          steps {
            echo 'Run Full Selenium Tests'
          }
        }

        stage('Integration Test (API)') {
          steps {
            echo 'Run All API Tests'
          }
        }

        stage('Performance Testing') {
          steps {
            echo 'Run All Performance Tests'
          }
        }

      }
    }

    stage('Deploy to UAT') {
      steps {
        echo 'UAT test scripts execution'
      }
    }

    stage('Certify') {
      steps {
        echo 'Manual Certification Using Inputs'
        input(message: 'Do you like to certify?', id: 'Certify', ok: 'Yes')
      }
    }

    stage('Deploy to Prod') {
      post {
        always {
          echo 'Send Email'
        }

      }
      steps {
        echo 'Deploy to Prod'
        jiraComment(issueKey: 'VPTS-1751', body: 'This is a comment regarding the quality of the response.')
      }
    }

  }
  environment {
    Name = 'HARINATH ANNAVARAPU'
  }
}