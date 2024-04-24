pipeline {
  agent any
  stages {
    stage('git pull') {
      steps {
        // Git-URL will replace by sed command before RUN
        git url: 'https://github.com/cjone112/GitOps', branch: 'main'
      }
    }
    stage('k8s deploy'){
      steps {
        script {
        withKubeConfig([credentialsId: 'cjone-kube']) {
                         sh 'kubectl apply -f deployment.yaml'
        }
        }
      }
    }    
  }
}
