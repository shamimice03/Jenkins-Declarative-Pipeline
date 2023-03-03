```
pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                sh 'hostname'
            } 
        }
    }
 post {
        always {
            echo 'Always'
        }
        success {
            echo 'Only on SUCCESS'
        }
        failure {
            echo 'Only on Failure'
        }
        unstable {
            echo 'Only if run is unstable'
        }
        changed {
            echo 'Only if status changed from Success to Failure or vice versa based on the last run.'
        }
    }
}
```