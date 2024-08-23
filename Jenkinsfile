pipeline {
agent {
    label 'linux'
}

tools {
    // Install the Maven version configured as "M3" and add it to the path.
    maven "MVN3"
}

stages {
    stage('pull') {
        steps {
            // Get some code from a GitHub repository
            git branch: 'main', credentialsId: 'github', url: 'git@github.com:sathishbob/java-docs-spring-hello-world.git'
        }
    }
    
    stage('build') {
        steps {
            sh "mvn -Dmaven.test.failure.ignore=true clean install"
        }
    }
    
    stage('publish') {
        steps {
            junit 'target/surefire-reports/*.xml'
            archiveArtifacts 'target/*.jar'
        }
    }

    stage('print'){
        steps{
            sh "echo hello"
        }
    }
}
}              
          
