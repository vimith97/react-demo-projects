pipeline {
    agent any
    
    environment {
        // Define environment variables
        REPO_URL = 'https://github.com/your-username/xyz-repo.git'
        BRANCH = 'master' // Change this to the desired branch
        BUILD_DIR = 'build'
        DEPLOY_DIR = '/var/www/html' // Change this to your deployment directory
    }

    stages {
        stage('Install Dependencies') {
            steps {
                // Install Node.js and dependencies
                sh 'cd /root/.jenkins/workspace/react-project/Password\ Generator/'
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                // Build the React.js project
                sh 'npm run build'
            }
        }

        stage('Deploy') {
    steps {
        // Remove the default Nginx welcome page
        sh 'sudo rm -rf /usr/share/nginx/html/*'
        
        // Deploy the built React application to the Nginx server
        sh "sudo cp -r $BUILD_DIR/* /usr/share/nginx/html/"

        // Reload Nginx to apply the changes
        sh 'sudo systemctl reload nginx'
    }
}
    }

    post {
        success {
            // Additional actions upon successful deployment
            echo 'Deployment successful!'
        }
        failure {
            // Additional actions upon deployment failure
            echo 'Deployment failed!'
        }
    }
}
