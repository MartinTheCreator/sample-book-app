pipeline {
  agent any

  environment {
      PATH = "/usr/local/bin:/usr/bin:/bin:${env.PATH}"
  }

  stages {
    stage('build') {
      steps {
        script {
          build()
        }
      }
    }
    stage('deploy-dev') {
      steps {
        script {
          deploy("DEV")
        }
      }
    }
    stage('test-dev') {
      steps {
        script {
          test('DEV')
        }
      }
    }
    stage('deploy-stg') {
      steps {
        script {
          deploy("STG")
        }
      }
    }
    stage('test-stg') {
      steps {
        script {
          test('STG')
        }
      }
    }
    stage('deploy-prd') {
      steps {
        script {
          deploy("PRD")
        }
      }
    }
    stage('test-prd') {
      steps {
        script {
          test('PRD')
        }
      }
    }
  }
}

def build() {
  echo "Building of node application is starting..."
  sh "docker build -t mmatovski/sample-book-app ."

  echo "Pushing image to docker registry..."
  sh "docker push mmatovski/sample-book-app"
}

def deploy(String environment) {
  echo "Deployment of node application on ${environment} environment..."
}

def test(String environment) {
  echo "API test execution on ${environment} environment..."
}
