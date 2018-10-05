pipeline {
  agent {
    kubernetes {
      cloud 'kube-101'
      label 'mypod'
      // defaultContainer 'jnlp'
      yamlFile 'KubernetesPod.yaml'
    }
  }
  stages {
    stage('Build') {
      steps {
        echo 'TODO: Build'
        sh '''#!/bin/bash
# DEBUG
id
env | sort

# EOF'''
      }
    }
  }
}
