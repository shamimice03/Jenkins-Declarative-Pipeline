Suppose, we have two `pipeline` job. Let's named that `inital-pipeline` and `linked-pipeline`. 
Following is the way to trigger `linked-pipeline` from `inital-pipeline`.

### Jenkinsfile for `inital-pipeline`
```
pipeline {
    agent any

    stages {
        stage('Start') {
            steps {
                echo 'Hello World From Initial Pipeline'
            }
        }
        stage('Trigger Linked Task') {
            steps {
               build job: 'linked-pipeline', parameters: [string(name: 'BUILDNUMBER', value: env.BUILD_NUMBER )]
            }
        }
    }
}
```
### Jenkinsfile for `linked-pipeline`
```
pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello From Linked Task'
            }
        }
        stage('Build_number') {
            steps {
                echo "${BUILDNUMBER}"
            }
        }
    }
}
```
