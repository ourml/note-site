pipeline {
  agent {
    docker {
      image 'debian:buster'
    }

  }
  stages {
    stage('PreBuild') {
      steps {
        sh '''sudo apt update && \\
sudo apt install nodejs \\
sudo apt install git'''
        sh 'git submodule init'
        sh 'git submodule update'
        sh 'npm install -g hexo-server hexo'
        sh 'npm install'
        sh 'cp ./source/_data/next.yml ./config.yml'
      }
    }

    stage('Build') {
      steps {
        sh 'hexo clean'
        sh 'hexo generate'
        sh 'hexo s'
      }
    }

    stage('Deliver') {
      steps {
        sshPublisher(alwaysPublishFromMaster: true, continueOnError: true, failOnError: true, masterNodeName: 'master')
      }
    }

  }
}