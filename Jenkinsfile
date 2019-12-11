pipeline {
    agent { docker { image 'maven:3.3.3' } }
    triggers {
        issueCommentTrigger('.*test this please.*')
    }
    stages {
        stage('build') {
            steps {
                sh 'mvn --version'
                sh 'mvn -B -DskipTests clean package' 
                sh 'mvn test' 
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml' 
                }
            }
        }
    }
}
