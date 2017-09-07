pipeline {
    agent none
  stages {
    stage('Deploy to test') {
      agent any
      steps {
        echo "test"
      }
    }
    
    stage('Deploy to staging?') {
        agent none
        steps {
            milestone 1
            input 'Continue'
            milestone 2
        }
    }

    stage('Deploy to staging') {
        agent any
        steps {
            lock(resource: 'staging-server', inversePrecedence: true) {
                    milestone 3
                    echo "staging"
            }
        }
    }

    stage('Deploy to production?') {
        agent none
        steps {
            milestone 4
            input 'Continue'
            milestone 5
        }
    }

    stage('Deploy to production') {
        agent any
        steps {
            lock(resource: 'production-server', inversePrecedence: true) {
                    milestone 6
                    echo "production"
            }
        }
    }
  }
  

    
}
