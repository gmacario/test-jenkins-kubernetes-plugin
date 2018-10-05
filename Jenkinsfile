pipeline {
  agent {
    kubernetes {
      cloud 'kube-101'
      label 'mypod'
      defaultContainer 'jnlp'
      yamlFile 'KubernetesPod.yaml'
    }
  }
  stages {
      ...
  }
}
