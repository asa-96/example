pipeline {
    agent any
    stages {
        stage('Checkout SCM') {
            steps {
                script {
                    // Explicitly checkout the source branch from the specified repository
                    checkout([$class: 'GitSCM', 
                             branches: [[name: env.SOURCE_BRANCH]], 
                             userRemoteConfigs: [[url: 'https://github.com/asa-96/example.git']]])
                }
            }
        }
    }
}
