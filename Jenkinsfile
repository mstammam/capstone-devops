pipeline {
  agent any
  stages {
    stage("Lint HTML") {
      steps {
        sh 'tidy -q -e ./web/*.html'  
      }
    }
    
    stage("Build Docker image") {
      steps {
        sh 'docker build -t html-server-image:v1 .'  
      }
    }

    stage("Push Dcoker image") {
      steps {
        withDockerRegistry([url: "", credentialsId: "dockerhub"]) {
          sh 'docker login'  
          sh 'docker tag html-server-image:v1 mtammam/capstone'  
          sh 'docker push mtammam/capstone'  
        }
      }
    }

    stage('Deploy Container') {
      steps {
        withAWS(region:'us-east-2',credentials:'aws-devops-credentials') {
          sh 'aws eks update-kubeconfig --name tammam-capstone-cluster'
          sh 'kubectl config use-context arn:aws:eks:us-east-2:796848775042:cluster/tammam-capstone-cluster'
          sh 'kubectl apply -f deployment/deployment.yml'

        }
      }
    }

  }
}