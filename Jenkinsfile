// Sample script for batch install using manifest default file with default name: now_batch_manifest.json
// ServiceNow API: POST /sn_cicd/app/batch/install

pipeline {
    agent any

    parameters {
            snParam(
                description: "ServiceNow Parameters",
                credentialsForPublishedApp: "7b4ca59e-8486-486c-895e-f044a5297447",
                instanceForPublishedAppUrl: "https://chiarngqdemoauthor.service-now.com",
                credentialsForInstalledApp:"7b4ca59e-8486-486c-895e-f044a5297447",
                instanceForInstalledAppUrl:"https://chiarngqdemoclient.service-now.com",
                sysId:'',
                appScope: "x_fxi_afioristore2",
                publishedAppVersion: '4.3.10',
                rollbackAppVersion: '',
                progressCheckInterval: null
            )
    }

    stages {
        stage('configuration') {
            steps {
                echo "ServiceNow Parameters: ${params.snParam}"
                echo "Check workspace: ${env.WORKSPACE}"
            }
        }
        stage('install-batch') {
             steps {
                 snBatchInstall(
                     url: 'https://chiarngqdemoclient.service-now.com'
                    ,credentialsId: '7b4ca59e-8486-486c-895e-f044a5297447'
                    ,useFile: true
                    //,file: 'now_batch_manifest.json' // not required if this is default file name
                    )

                echo "ServiceNow Parameters after Batch Install: ${params.snParam}"
             }
        }
        
    }
}
