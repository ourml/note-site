pipeline {
  agent {
    docker {
      image 'node:10.13.0-alpine'
      args '-p 4000:4000'
    }

  }
  stages {
    stage('PreBuild') {
      steps {
        sh 'git submodule init'
        sh 'git submodule update'
        sh 'npm install'
        sh 'cp ./source/_data/next.yml ./config.yml'
      }
    }

    stage('Build') {
      steps {
        sh 'hexo clean'
        sh 'hexo generate'
      }
    }

  }
}