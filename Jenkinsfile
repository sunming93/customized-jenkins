pipeline {

    agent any

    stages {
        stage('Clone') {
            steps {
                checkout scm
            }
        }
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

}
