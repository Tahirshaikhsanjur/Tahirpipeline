pipeline {
    agent any

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
       // maven "M3"
        //withEnv( ["D:\college\devlop practicals\maven-experiment\apache-maven-3.6.3-bin\apache-maven-3.6.3=${tool mvn_version}/bin"] )
        def mvn_version = 'M3'
        withEnv( ["PATH+MAVEN=${tool mvn_version}/bin"] )
    }

    stages {
        stage('Build') {
            steps {
                // Get some code from a GitHub repository
                git 'https://github.com/jglick/simple-maven-project-with-tests.git'

               

                // To run Maven on a Windows agent, use
                // bat "mvn -Dmaven.test.failure.ignore=true clean package"
            }

            post {
                // If Maven was able to run the tests, even if some of the test
                // failed, record the test results and archive the jar file.
                success {
                    junit '**/target/surefire-reports/TEST-*.xml'
                    archiveArtifacts 'target/*.jar'
                }
            }
        }
    }
}
