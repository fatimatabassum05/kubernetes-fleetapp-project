pipeline {
  agent {label 'docker'}
  stages {
    stage('checkout') {
      steps {
        git branch: 'main', url: 'https://github.com/fatimatabassum05/kubernetes-fleetapp-project.git'
      }
    }
    stage('deploy') {
      steps {
        withCredentials([aws(credentialsId: "awsCred", region: "ap-south-1")]) {
        sh 'aws eks --region ap-south-1 update-kubeconfig --name eks-cluster'
        sh 'helm upgrade --install queue ./helm -n dev'
      }
    }
  }
}
