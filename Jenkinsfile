pipeline {
    agent any
    options {
      buildDiscarder logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '25', daysToKeepStr: '', numToKeepStr: '25')
      disableConcurrentBuilds()
    }
    stages{
        stage("Hello") {
            steps {
                echo 'Hello World'
            }
        }
    }
}
