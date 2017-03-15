pipeline {
    agent any

    stages {
        stage('Preconditions') {
            steps {
                echo 'Building..'
		build job: 'TEST_AUTOMATION_ASTF' 
		parameters: [string(name: 'testsystem', value: '01'), [$class: 'ExtendedChoiceParameterValue', name: 'website', value: 'Partner_01'], [$class: 'ExtendedChoiceParameterValue', name:'phase', value: '00_Preconditions']]
            }
        }
        stage('Phase 1 - Purchases') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Phase 2 - Prize Processing') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
