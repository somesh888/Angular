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
            when { anyOf { branch 'dev*'; branch 'main'} }
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
        stage("change req stage") {
            when { changeRequest() 
                   branch 'dev-test' }
                steps {
                sh """echo "this stage is building only for pr to dev-test"
                """
        }
    }
}
}
