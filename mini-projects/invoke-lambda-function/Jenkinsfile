pipeline {
    agent any

    stages {
        stage('Invoke Lambda') {
            steps {
               sh 'aws lambda invoke --function-name BucketLists response.json --region ap-northeast-1'
            }
        }
        stage('Display response') {
            steps {
               sh 'cat response.json'
            }
        }
        
    }
}
