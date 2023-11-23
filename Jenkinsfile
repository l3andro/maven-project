pipeline {
    agent any
    stages {
        stage("Secrets Detection") {
            steps {
                script {
                    //gitLeaksDetection()
                    sh (script: "ls -la")
                    teste = sh (
                        script: "gitleaks detect --path . -v --redact --report-format=sarif --report-path=gitleaks-report.sarif --log-level=debug", 
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
