pipeline {

  agent { label 'kubepod' }

  stages {

    stage('Checkout Source') {
      steps {
        git url:'https://github.com/vineetjain999/AccountsAPI.git', branch:'master'
      }
    }

    stage('Deploy App') {
      steps {
        script {
          kubernetesDeploy(configs: "AccountsMongoVolume.yaml", kubeconfigId: "mykubeconfig");
          kubernetesDeploy(configs: "AccountsMongoVolumeClaim.yaml", kubeconfigId: "mykubeconfig");
          kubernetesDeploy(configs: "AccountsMongo.yaml", kubeconfigId: "mykubeconfig");
          kubernetesDeploy(configs: "AccountsMongoService.yaml", kubeconfigId: "mykubeconfig");
          kubernetesDeploy(configs: "AccountsApp.yaml", kubeconfigId: "mykubeconfig");
          kubernetesDeploy(configs: "AccountsAppService.yaml", kubeconfigId: "mykubeconfig");
        }
      }
    }
  }
}
