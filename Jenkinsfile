pipeline {
    agent any

    triggers {
        cron('H 8 * * *')
    }

    stages {
        stage('dependencies') {
            steps {
                sh 'npm i'
            }
        }
        stage('cypress parallel tests') {
            environment {
                CYPRESS_RECORD_KEY = credentials('cypress-e2e-automation-record-key')
                CYPRESS_PROJECT_ID = credentials('cypress-e2e-automation-project-id')
                CYPRESS_trashAssetsBeforeRuns = 'false'
            }

            parallel {
                stage('machine 1') {
                    steps {
                        sh "npm run cy:ci"
                    }
                }

                stage('machine 2') {
                    steps {
                        sh "npm run cy:ci"
                    }
                }
            }
        }
    }
}