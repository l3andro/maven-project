pipeline {
    agent any
    stages {
        stage("Secrets Detection") {
            steps {
                script {
                    //gitLeaksDetection()
                    teste = sh (
                        script: "horusec start -p . -D --enable-git-history --log-level debug -o sonarqube -O gitleaks-report.json",
                        //script: "gitleaks detect --source . -v --redact --report-path=gitleaks-report.json", 
                        returnStdout:true)
                    //echo "${teste}"
                    sh (script: "cat gitleaks-report.json")
                }
            }
            // post {
            //     always {
            //         script{
            //             catchError() {
            //                 archiveArtifacts artifacts: 'gitleaks-report.json'
            //             }
            //         }
            //     }
            // }
        }
    }
}
