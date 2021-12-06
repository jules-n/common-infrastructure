pipeline {
    agent any
    stages {
        stage('mongo') {
            when {
                allOf {
                    branch comparator: 'REGEXP', pattern: 'main'
                    changeset 'mongo/**'
                }
            }
            steps {
                build job: "common-infrastructure-mongo/${BRANCH_NAME}", wait: false
            }
        }
        stage('kafka') {
            when {
                allOf {
                    branch comparator: 'REGEXP', pattern: 'main'
                    changeset 'kafka/**'
                }
            }
            steps {
                build job: "common-infrastructure-kafka/${BRANCH_NAME}", wait: false
            }
        }
    }
}
