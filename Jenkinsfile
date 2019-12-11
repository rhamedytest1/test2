pipeline {
    agent { docker { image 'maven:3.3.3' } }
    triggers {
        issueCommentTrigger('.*full test.*')
    }
    stages {
        stage('build') {
            steps {
                sh 'mvn --version'
                sh 'mvn -B -DskipTests clean package' 
                sh 'mvn test' 
            }
        }
    }
}
