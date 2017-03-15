pipeline {
    agent any

    stages {
        stage('Preconditions') {
            steps {
	       echo 'Executing Preconditions....'
               build job: 'TEST_AUTOMATION_ASTF', parameters: [string(name: 'testsystem', value: '01'), [$class: 'com.moded.extendedchoiceparameter.ExtendedChoiceParameterValue', name: 'website', value: 'Partner_01'], [$class: 'com.moded.extendedchoiceparameter.ExtendedChoiceParameterValue', name: 'phase', value: '00_Preconditions']]
            }
        }
        stage('Phase 1 - Purchases') {
            steps {
                echo 'Executing Phase 1, Purchases'
		build job: 'TEST_AUTOMATION_ASTF', parameters: [string(name: 'testsystem', value: '01'), [$class: 'com.moded.extendedchoiceparameter.ExtendedChoiceParameterValue', name: 'website', value: 'Partner_01'], [$class: 'com.moded.extendedchoiceparameter.ExtendedChoiceParameterValue', name: 'phase', value: '01_Phase_1']]
            }
        }
        stage('Phase 2 - Prize Processing') {
            steps {
                build job: 'TEST_AUTOMATION_ASTF', parameters: [string(name: 'testsystem', value: '01'), [$class: 'com.moded.extendedchoiceparameter.ExtendedChoiceParameterValue', name: 'website', value: 'Partner_01'], [$class: 'com.moded.extendedchoiceparameter.ExtendedChoiceParameterValue', name: 'phase', value: '02_Phase_2']]
            }
        }
    }
   post {
        always {
            sh 'Automatic e2e tests execution is terminated...'
        }
        success {
            sh 'Successfull execution of e2e tests. No test has failed.'
        }
        failure {
            sh 'Build Marked as failed.'
        }
        unstable {
            sh 'This build is unstable'
        }
        changed {
            sh 'This will run only if the state of the Pipeline has changed'
            sh 'For example, the Pipeline was previously failing but is now successful'
        }
    }
}
