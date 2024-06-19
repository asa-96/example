// pipeline {
//     agent any

//     triggers {
//         GenericTrigger(
//             genericVariables: [
//                 [key: 'action', value: '$.action'],
//                 [key: 'source_branch', value: '$.pull_request.head.ref'],
//                 [key: 'target_branch', value: '$.pull_request.base.ref']
//             ],
//             causeString: 'Triggered by PR from ${source_branch} to ${target_branch}',
//             token: 'demo', // Ensure this token matches the one configured in the webhook
//             printContributedVariables: false,
//             printPostContent: true,
//             regexpFilterText: '''${action}\n${source_branch}\n${target_branch}''',
//             regexpFilterExpression: '^opened\n.*\nmain$'
//         )
//     }

//     stages {
//         stage('Checkout') {
//             steps {
//                 // Custom checkout step with scmGit
//                 script {
//                     checkout([
//                         $class: 'GitSCM', 
//                         branches: [[name: "*/${source_branch}"]], 
//                         extensions: [], 
//                         userRemoteConfigs: [[url: 'https://github.com/asa-96/example.git']]
//                     ])
//                 }
//             }
//         }
//     }
// }

pipeline {
    agent any

    triggers {
        GenericTrigger(
            genericVariables: [
                [key: 'action', value: '$.action'],
                [key: 'source_branch', value: '$.pull_request.head.ref'],
                [key: 'target_branch', value: '$.pull_request.base.ref']
            ],
            causeString: 'Triggered by PR from ${source_branch} to ${target_branch}',
            token: 'demo', // Ensure this token matches the one configured in the webhook
            printContributedVariables: false,
            printPostContent: true,
            regexpFilterText: '''${action}\n${source_branch}\n${target_branch}''',
            regexpFilterExpression: '^opened\n.*\nmain$'
        )
    }

    stages {
        stage('Checkout') {
            steps {
                script {
                    def branch = source_branch
                    echo "Checking out branch: ${branch}"
                    checkout([
                        $class: 'GitSCM', 
                        branches: [[name: "refs/heads/${branch}"]], // Use "refs/heads/${branch}" for the correct refspec
                        doGenerateSubmoduleConfigurations: false,
                        extensions: [],
                        submoduleCfg: [],
                        userRemoteConfigs: [[url: 'https://github.com/asa-96/example.git']]
                    ])
                }
            }
        }
    }
}

