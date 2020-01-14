pipeline {

    environment {
        OPENSHIFT_SERVER = 'https://192.168.64.2:8443/'
        OPENSHIFT_NAMESPACE = 'jenkins-metrics'
    }

    stage('Clone') {
        checkout scm
    }

    stages {
        stage('Create Jenkins') {
            steps {
                sh 'oc apply -f openshift/buildConfig.yaml'
                sh 'oc start-build custom-jenkins-build'
                sh 'oc process custom-jenkins | oc apply -f -'
            }
        }

        stage('Verify Jenkins') {
            steps {
                sh './verify-jenkins.sh'
            }
        }
    }

    post {
        always {
            onDebug {
                echo "Debugging commit, waiting 900 seconds"
                sh 'sleep 900'
            }
        }
        success {
            echo "Deleting Jenkins instance"
            sh './teardown.sh'
        }
        failure {
            echo "Build failed, not removing Jenkins"
        }
    }

}
