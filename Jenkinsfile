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
    }
}

