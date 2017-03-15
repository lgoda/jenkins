pipeline {
    agent any

    stages {
        stage('Preconditions') {
            steps {
                echo 'Building..'
		build './TEST_AUTOMATION_ASTF'
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
