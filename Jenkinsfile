pipeline {
    agent any
    stages {
        stage("Secrets Detection") {
            steps {
                script {
                    //gitLeaksDetection()
                    sh (script: "ls -la")
                    teste = sh (
                        script: "horusec start -p .",
                        //script: "gitleaks detect --source . -v --redact --report-path=gitleaks-report.json", 
                        returnStdout:true)
                    //echo "${teste}"
                    sh (script: "ls -la")
                }
            }
            post {
                always {
                    script{
                        catchError() {
                            archiveArtifacts artifacts: 'gitleaks-report.json'
                        }
                    }
                }
            }
        }
    }
}
