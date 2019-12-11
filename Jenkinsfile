pipeline {
    agent { docker { image 'maven:3.3.3' } }
    triggers {
        issueCommentTrigger('.*test this please.*')
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn --version'
            }
            steps {
                sh 'mvn -B -DskipTests clean package' 
            }
            steps {
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
