pipeline {
    agent any

    stages {
        stage('Preconditions') {
            steps {
	       echo 'Executing Preconditions....'
               script {
                 def step1 = build job: 'TEST_AUTOMATION_ASTF', parameters: [string(name: 'testsystem', value: '01'), [$class: 'com.moded.extendedchoiceparameter.ExtendedChoiceParameterValue', name: 'website', value: 'Partner_01'], [$class: 'com.moded.extendedchoiceparameter.ExtendedChoiceParameterValue', name: 'phase', value: '00_Preconditions']], propagate:false
                 def result = step1.result
                 if (result.equals("SUCCESS") /*|| result.equals("UNSTABLE")*/) {
                   echo 'Set status to SUCCESS'
                   currentBuild.result = 'SUCCESS'
                 } else {
                   currentBuild.result = 'FAILURE'
                 }
               }
            }
        }
        stage('Phase 1 - Purchases') {
            steps {
                echo 'Executing Phase 1, Purchases'
                script {
  		            def step2 = build job: 'TEST_AUTOMATION_ASTF', parameters: [string(name: 'testsystem', value: '01'), [$class: 'com.moded.extendedchoiceparameter.ExtendedChoiceParameterValue', name: 'website', value: 'Partner_01'], [$class: 'com.moded.extendedchoiceparameter.ExtendedChoiceParameterValue', name: 'phase', value: '01_Phase_1']],  propagate:false
                  def result2 = step2.result
                  if (result2.equals("SUCCESS") || result2.equals("UNSTABLE")) {
                    currentBuild.result = 'SUCCESS'
                  } else {
                    currentBuild.result = 'FAILURE'
                  }
                }
            }
        }
        stage('Phase 2 - Prize Processing') {
            steps {
                script {
                  def step3 = build job: 'TEST_AUTOMATION_ASTF', parameters: [string(name: 'testsystem', value: '01'), [$class: 'com.moded.extendedchoiceparameter.ExtendedChoiceParameterValue', name: 'website', value: 'Partner_01'], [$class: 'com.moded.extendedchoiceparameter.ExtendedChoiceParameterValue', name: 'phase', value: '02_Phase_2']], propagate:false
                  def result3 = step3.result
                  if (result3.equals("SUCCESS") || result3.equals("UNSTABLE")) {
                    currentBuild.result = 'SUCCESS'
                  } else {
                    currentBuild.result = 'FAILURE'
                  }
                }
            }
        }
    }

}
