pipeline {
    agent any

    environment {
        // Install the Maven version configured as "M3" and add it to the path.
        KUBECONFIG = credentials('kubeconfig')
    }

    stages {
        stage('Build') {
            steps {
                sh "git clone https://github.com/shubhadaR/git-galaxy.git"

                // Run Maven on a Unix agent.
                sh "helm dependency update ./mychart"
                sh "helm lint ./mychart"
                sh "helm package ./mychart"
                sh "helm install mytry ./mychart"

                // To run Maven on a Windows agent, use
                // bat "mvn -Dmaven.test.failure.ignore=true clean package"
            }
         
         

            post {
                // If Maven was able to run the tests, even if some of the test
                // failed, record the test results and archive the jar file.
                success {
                     echo "..successfully done Congragulations.. "
                }
            }
        }
    }
}
