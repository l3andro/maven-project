pipeline {
    agent any
    stages {
        stage("Secrets Detection") {
            steps {
                script {
                    //gitLeaksDetection()
                    sh (script: "ls -la")
                    teste = sh (
                        script: "gitleaks detect --source . -v --exit-code 0 --redact --report-format junit --report-path gitleaks-report.xml", 
                        returnStdout:true)
                    //echo "${teste}"
                    sh (script: "ls -la")
                }
            }
            post {
                always {
                    script{
                        catchError() {
                            junit 'gitleaks-report.xml'
                        }
                    }
                }
            }
        }
    }
}
