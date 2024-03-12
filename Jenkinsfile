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
                // Install the required dependencies
              
                bat 'pip install -r requirements.txt'
            }
        }

        stage('Run tests') {
            steps {
                // Execute the tests
                bat 'pytest test.py'
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