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
        }*/
        stage('deploy to tomcat'){
        steps{
deploy adapters: [tomcat10(credentialsId: 'fb27284f-7d67-4c9a-8cd0-1450df47fd64', path: '', url: 'http://3.144.235.243:8080/')], contextPath: null, war: '**/*.war'
    }
}
}

    }

}
