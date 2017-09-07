pipeline {
    //agent is none so no executors are preserved
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
        }
    }

    stage('Deploy to staging') {
        agent any
        steps {
            lock(resource: 'staging-server', inversePrecedence: true) {
                milestone 2
                echo "staging"
            }
        }
    }

    stage('Deploy to production?') {
        agent none
        steps {
            milestone 3
            input 'Continue'
        }
    }

    stage('Deploy to production') {
        agent any
        steps {
            lock(resource: 'production-server', inversePrecedence: true) {
                milestone 4
                echo "production"
            }
        }
    }
  }
     
}
