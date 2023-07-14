pipeline {
    agent any
    tools {
        maven 'maven'
    }
    /*options {
        timeout(10)
        buildDiscarder logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '5', numToKeepStr: '5')
    }*/
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
deploy adapters: [tomcat9(credentialsId: '23871fd7-3efa-4e83-a34f-786ce42e5415', path: '', url: 'http://3.144.235.243:8080/')], contextPath: null, war: '**/*.war'
    }
}
}

    }
