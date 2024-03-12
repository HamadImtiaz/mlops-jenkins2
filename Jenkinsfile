pipeline {
    agent any

    stages {
        stage('Clone repository') {
            steps {
                // Clone the repository
                checkout scm
            }
        }

        stage('Install dependencies') {
            steps {
                // Create a virtual environment
                bat 'python -m venv venv'
                // Activate the virtual environment and install dependencies
                bat '.\\venv\\Scripts\\activate && pip install -r requirements.txt'
            }
        }

        stage('Run tests') {
            steps {
                // Execute the tests
                bat '.\\venv\\Scripts\\activate && pytest test.py'
            }
        }

        stage('Deploy') {
            steps {
                script {
                    deploy(env.BRANCH_NAME)
                }
            }
        }
    }
}

def deploy(String branchName) {
    if (branchName == 'main') {
        echo "Deploying to production"
       // deploy
    } else {
        echo "Deploying to UAT"
    }
    // else {
    //     echo "Deploying to a non-production/non-UAT branch: ${branchName}"
    //    //deploy
    // }
}
