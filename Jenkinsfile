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
        /*stage('upload artifact to nexus') {
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
        stage('deploy to tomcat'){
            steps{
            sshagent(['c7f8eace-79f4-4de2-b211-fa1ae2f1fd38']) {
            sh "scp tomcat/target/wwp-1.0.0.war ubuntu@18.191.168.86:/apache-tomcat-9.0.78/webapps"
            }
}
        }*/
    }

}
