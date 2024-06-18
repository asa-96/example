pipeline {
    agent any
    environment {
        // Environment variables to capture webhook parameters
        ACTION = "${action}"
        BASE_BRANCH = "${base_branch}"
        TARGET_BRANCH = "${target_branch}"
    }

    stages {
        stage('Checkout Code') {
            when {
                allOf {
                    expression { return env.ACTION == 'opened' }
                    expression { return env.BASE_BRANCH == 'main' }
                }
            }
            steps {
                echo 'PR opened to main branch. Checking out code...'
                checkout([$class: 'GitSCM', branches: [[name: "*/${TARGET_BRANCH}"]],
                          userRemoteConfigs: [[url: 'https://github.com/asa-96/example.git']]])
                // Replace the URL with your repository URL
                echo 'Code checked out successfully.'
            }
        }
    }
}
