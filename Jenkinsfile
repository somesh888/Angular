pipeline {
    agent any
    
    options {
        buildDiscarder(logRotator(numToKeepStr: '10'))
    }

    stages {
        stage ('lint test') {
            when { anyOf { branch 'dev*'; branch 'main'; branch 'PR-*'; branch 'feature*'} }
            steps {
                sh """
                echo 'lint-test'
                """
            }
        } 

        stage ('unit-test') {
            when { anyOf { branch 'dev*'; branch 'main'; branch 'PR-*'} }
            steps {
                script {
                    sh """
                    echo 'unit test '
                    """ 
                }
            }
        }
        stage("build stage") {
            when {
                  branch 'main'  }
            steps {
                sh """echo "this is build stage for master only"
                """
            }
        }
}
}
