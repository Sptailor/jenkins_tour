pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                sh 'echo "Hello World"'
                sh '''
                    echo "Multiline shell steps works too"
                    ls -lah
                '''
            }
        }
        stage('deploy') {
            steps {
                retry(3) {
                    sh 'echo "Deploying (retry up to 3 times)"'
                }
                timeout(time: 3, unit: 'MINUTES') {
                    sh 'echo "Health check (fails if over 3 minutes)"'
                }
            }
        }
    }
}
