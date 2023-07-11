pipeline {
    agent any
    tools {
        maven 'maven'
    }
    options {
        timeout(10)
        buildDiscarder logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '5', numToKeepStr: '5')
    }
    stages {
        stage('Build') {
            steps {
                sh "mvn clean install"
            }
        }
        stage('upload artifact to nexus') {
            steps {
                nexusArtifactUploader artifacts: [
                    [
                        artifactId: 'wwp', 
                        classifier: '', 
                        file: 'target/wwp-1.0.0.war', 
                        type: 'war'
                    ]
                ], 
                    credentialsId: 'nexus3', 
                    groupId: 'koddas.web.war', 
                    nexusUrl: '10.0.0.91:8081', 
                    nexusVersion: 'nexus3', 
                    protocol: 'http', 
                    repository: 'samplerepo', 
                    version: '1.0.0'
            }
        }
    }

        post{
                success{
                        emailext attachLog: true, body: 'pipeline success', recipientProviders: [buildUser()], subject: 'success', to: 'samhithaaluri@gmail.com'
                }
                failure{
                        emailext attachLog: true, body: 'pipeline failed', recipientProviders: [buildUser()], subject: 'failed', to: 'samhithaaluri@gmail.com'
                }
        }
}
