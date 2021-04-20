// Sample script for /sn_cicd/app_repo/install for app customization feature
// without ServiceNow Parameters (snParams).

pipeline {
    agent any

    parameters {
            string(name: "myParam", defaultValue: 'test')

            snParam(
                description: "ServiceNow Parameters",
                credentialsForPublishedApp: "f15c53d0-25d0-41ab-adce-3f60e6bc9217",
                instanceForPublishedAppUrl: "https://chiarngqdemoauthor.service-now.com",
                credentialsForInstalledApp:"f15c53d0-25d0-41ab-adce-3f60e6bc9217",
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
                echo "Test param: ${params.myParam}"

                echo "ServiceNow Parameters: ${params.snParam}"
            }
        }
        stage('publishing') {
            steps {
                snPublishApp(
                    url: "https://chiarngqdemoauthor.service-now.com",
                    credentialsId: "f15c53d0-25d0-41ab-adce-3f60e6bc9217",
                    appScope: "x_fxi_afioristore2",
                    obtainVersionAutomatically: true)

                echo "ServiceNow Parameters after publishing stage: ${params.snParam}"
            }
        }
        stage('installation') {
            steps {
                snInstallApp(
                    url: "https://chiarngqdemoclient.service-now.com",
                    credentialsId: "f15c53d0-25d0-41ab-adce-3f60e6bc9217",
                    appScope: "x_fxi_afioristore2",
                    appVersion: "4.3.11",
                    baseAppAutoUpgrade: false)

                echo "ServiceNow Parameters after installation stage: ${params.snParam}"
            }
        }
        stage('revert-changes') {
            steps {
                snRollbackApp(
                    url: "https://chiarngqdemoclient.service-now.com",
                    credentialsId: "f15c53d0-25d0-41ab-adce-3f60e6bc9217",
                    appScope: "x_fxi_afioristore2"
                )
            }
        }
    }
}
