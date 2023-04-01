pipeline {
    agent any
    
    options {
        buildDiscarder(logRotator(numToKeepStr: '10'))
    }

    stages {
        stage ('lint test') {
            steps {
                sh """
                echo 'lint-test'
                """
            }
        } 

        stage ('unit-test') {
            when { anyOf { branch 'dev*'; branch 'main';branch 'feature*' } }
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
                  branch 'master'  }
            steps {
                sh """echo "this is build stage for master only"
                """
            }
        }
    }
}
