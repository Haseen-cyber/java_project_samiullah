pipeline {
    agent any
    
    tools {
        maven "maven"
    }
    stages {
        stage("Test") {
            steps{
                sh "mvn test"
            }
        }
        stage("Build") {
            steps {
                sh "mvn package"
                echo "Building..."
            }
        }
        stage("Deploy on Test") {
            steps {
                //deploy to containers
                deploy adapters: [tomcat9(credentialsId: 'Tomcat_credential', path: '', url: 'http://44.203.67.218:8090/')], contextPath: null, war: '**/*.war'
            }
        }        
    }

}
