pipeline{
  agent any
  environment{
    REPO_URL = 'https://github.com/Venu-GopalDR/JSP-gram.git'
    BRANCH = 'main'
    JAR_FLE = 'target/myapp.jar'
  }
  stages{
    stage('checkout git code'){
      steps{
        git branch: "${BRANCH}" , url: "${REPO_URL}"
      }
    }
    stage('Build with Maven'){
      steps{
        sh 'mvn clean package'
      }
    }
    stage('Deploy with ansible'){
      steps{
        sh 'ansible-playbook -i dev deploy_app.yml'
      }
    }
  }
  post{
    success{
      echo "Deployment success"
    }
    failure{
      echo "Deployment failed"
    }
  }
}
