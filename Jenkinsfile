pipeline {
  agent any
  stages {
    stage('git pull') {
      steps {
        // Git-URL will replace by sed command before RUN
        git url: 'https://github.com/cjone112/GitOps', branch: 'main'
      }
    }
    stage('deploy kubernetes'){
      steps {
        sh  '''
         export KUBECONFIG=/var/lib/jenkins/cjone-kube-test_kubeconfig.yaml
         '''
        kubernetesDeploy(kubeconfigId: 'cjone-kube',
                         configs: '*.yaml')
      }
    }    
  }
}
