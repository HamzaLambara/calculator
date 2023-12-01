pipeline {
    agent any
    stages {
        stage("Compilation") {
            steps {
                sh "./gradlew compileJava"
            }
        }
        
        stage("Test unitaire") {
            steps {
                sh "./gradlew test"
            }
        }
        
        stage("Couverture du code") {
            steps {
                sh "./gradlew jacocoTestReport"
                
                publishHTML(target: [
                    reportDir: 'build/reports/jacoco/test/html',
                    reportFiles: 'index.html',
                    reportName: 'JaCoCo Report'
                ])
                
                sh "./gradlew jacocoTestCoverageVerification"
            }
        }
        
        stage("Analyse statique du code") {
            steps {
                sh "./gradlew checkstyleMain -Pcheckstyle.config=file:/home/calculator/config/checkstyle/checkstyle.xml"
                
                publishHTML(target: [
                    reportDir: 'build/reports/checkstyle/main.xml',
                    reportFiles: 'checkstyle.html',
                    reportName: 'Checkstyle Report'
                ])
            }
        }
    }
}


