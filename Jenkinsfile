pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh '''
                    mkdir -p build/libs
                    echo "fake build output" > build/libs/app.jar
                '''
            }
        }
        stage('Test') {
            steps {
                sh '''
                    mkdir -p build/reports
                    cat > build/reports/test-results.xml <<'EOF'
<testsuite name="SampleTests" tests="2" failures="0" errors="0" skipped="0">
  <testcase classname="SampleTests" name="testAddition" time="0.01"/>
  <testcase classname="SampleTests" name="testSubtraction" time="0.01"/>
</testsuite>
EOF
                '''
            }
        }
    }

    post {
        always {
            junit 'build/reports/**/*.xml'
            archiveArtifacts artifacts: 'build/libs/**/*.jar', fingerprint: true
        }
    }
}
