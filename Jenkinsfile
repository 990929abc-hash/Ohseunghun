pipeline {
    agent any

    stages {
        stage('HTML 보고서 생성') {
            steps {
                script {
                    writeFile file: 'reports/ItemGrant_Report.html',
                              text: '<html><body><h1>ItemGrant Report</h1><p>Test completed.</p></body></html>'

                    writeFile file: 'reports/Login_Report.html',
                              text: '<html><body><h1>Login Report</h1><p>Test completed.</p></body></html>'

                    writeFile file: 'reports/Ranking_Report.html',
                              text: '<html><body><h1>Ranking Report</h1><p>Test completed.</p></body></html>'
                }
            }
        }

        stage('HTML 보고서 게시') {
            steps {
                publishHTML(target: [
                    reportDir: 'reports',
                    reportFiles: 'ItemGrant_Report.html,Login_Report.html,Ranking_Report.html',
                    reportName: 'Newman Reports',
                    keepAll: true,
                    alwaysLinkToLastBuild: true,
                    allowMissing: false
                ])
            }
        }

        stage('Artifacts 저장') {
            steps {
                archiveArtifacts artifacts: 'reports/*.html',
                                 fingerprint: true
            }
        }
    }
}
