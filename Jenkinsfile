pipeline {
    agent any
    
    environment {
        GIT_REPO = 'https://github.com/sudeepa-sri/Aurotech.git' // 🔥 Your GitHub repo
        BRANCH = 'main' // 🔥 Your branch name
    }
    
    stages {
        // Step 1: Clone Repository
        stage('Clone Repo') {
            steps {
                git url: "${GIT_REPO}", branch: "${BRANCH}" // ✅ Fixed the git command
            }
        }
        
        // Step 2: Build (No actual build needed for static sites)
        stage('Build') {
            steps {
                script {
                    echo 'No build step required for static files.'
                }
            }
        }
        
        // Step 3: Deploy the Website
        stage('Deploy') {
            steps {
                script {
                    // Create a folder for the website files
                    sh 'sudo mkdir -p /var/www/html'
                    
                    // Copy website files to the server location
                    sh 'sudo cp -r * /var/www/html'
                    
                    // Start a simple HTTP server using Python
                    sh 'nohup python3 -m http.server 8000 --directory /var/www/html &'
                }
            }
        }
    }
}


