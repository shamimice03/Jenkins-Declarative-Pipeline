# jenkins

## Jenkfkins file template

```groovy
pipeline {
  agent any

  stages {
    stage('Clone repo') {
      steps {
        echo 'Cloning...'
        checkout scmGit(branches: [
          [name: '*/main']
        ], extensions: [], userRemoteConfigs: [
          [url: 'https://github.com/shamimice03/jenkins-hands-on.git']
        ])
        sh 'ls -la'
      }
    }
    stage('Run commands') {
      steps {
        sh 'pwd'
      }
    }
    stage('Run multiple commands...') {
      steps {
        sh ""
        "
        cd~/.ssh
        ls - la ""
        "
      }
    }
    stage('Run multiple commands inline') {
      steps {
        sh 'cd ~/.ssh; ls -la'
      }
    }
    stage('Manual permission to proceed') {
      steps {
        input message: 'Click Procced'
      }
    }
  }
}
```
