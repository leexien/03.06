pipeline {
    agent any

    triggers {
        GenericTrigger(
            genericVariables: [
                [ key: 'action', value: '$.action' ],
                [ key: 'base_ref', value: '$.pull_request.base.ref' ],
                [ key: 'head_ref', value: '$.pull_request.head.ref' ]
            ],
            causeString: 'Triggered by GitHub webhook',
            printContributedVariables: false,
            token: https:
        )
    }

    stages {
        stage('Build') {
            steps {
                echo 'hello capybara'
            }
        }
        stage('Test') {
            when {
                expression {
                    return env.action == 'closed' && env.base_ref == 'dev' && env.head_ref == 'ft/test'
                }
            }
            steps {
                echo 'Running tests...'
            }
        }
    }
}
