pipeline {
    agent any
    tools { 
        maven 'Maven' 
        jdk 'Java'
    }
    stages {
        stage ('Initialize') {
            steps {
                sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                '''
            }
        }

        stage ('Build') {
            steps {
                sh  'mvn package'
                sh  'java -cp target/my-app-1.0-SNAPSHOT.jar com.mycompany.app.App'
            }
            post {
                success {
                    sh 'mvn clean --quiet'
                }
            }
        }
    }
}
