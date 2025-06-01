pipeline {
  agent any

  environment {
      PATH = "/usr/local/bin:/usr/bin:/bin:${env.PATH}"
  }

  stages {
    stage('build') {
      steps {
        build()
      }
    }
    stage('deploy-dev') {
      steps {
        deploy("DEV")
      }
    }
    stage('test-dev') {
      steps {
        test('DEV')
      }
    }
    stage('deploy-stg') {
      steps {
        deploy("STG")
      }
    }
    stage('test-stg') {
      steps {
        test('STG')
      }
    }
    stage('deploy-prd') {
      steps {
        deploy("PRD")
      }
    }
    stage('test-prd') {
      steps {
        test('PRD')
      }
    }
  }
}

def build() {
  echo "Building of node application is starting..."
  sh "docker --version"
}

def deploy(String environment) {
  echo "Deployment of node application on ${environment} environment..."
}

def test(String environment) {
  echo "API test execution on ${environment} environment..."
}
