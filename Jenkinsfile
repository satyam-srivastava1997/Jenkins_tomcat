pipeline {
    agent any
    stages {
        stage('Build Application') {
            steps {
		build job: 'Package_Application'
        }
        stage('Deploy in Staging Environment'){
            steps{
                build job: 'Deploy_App_staging_ENV'

            }
            
        }
        stage('Deploy to Production'){
            steps{
                timeout(time:5, unit:'DAYS'){
                    input message:'Approve PRODUCTION Deployment?'
                }
                build job: 'Deploy_App_Prod_env'
            }
        }
    }
}
