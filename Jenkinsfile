pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building the signup page branch...'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing the signup page branch...'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying the signup page branch...'
                sh '''
                # Create the deployment directory
                mkdir -p /tmp/deployment_directory_signup

                # Copy the signup.html file from the Jenkins workspace
                cp ${WORKSPACE}/Registration_Form/Form.html /tmp/deployment_directory_signup/

                # Start the Python HTTP server on port 9292
                nohup python3 -m http.server 9292 --directory /tmp/deployment_directory_signup > /tmp/server_signup.log 2>&1 &
                '''
                echo "Signup page is being served on http://localhost:9292"
            }
        }
        stage('Archive HTML') {
            steps {
                archiveArtifacts artifacts: '*.html', fingerprint: true
            }
        }
    }
}
