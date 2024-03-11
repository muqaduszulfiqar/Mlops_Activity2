pipeline {
    agent any

    stages {
        stage('Clone repository') {
            steps {
                checkout scm
            }
        }

        stage('Install dependencies') {
            steps {
                sh 'pip install --upgrade pip'
                sh 'pip install -r requirements.txt'
            }
        }

        stage('Run tests') {
            steps {
                sh 'pytest test.py'
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
      
    } else if (branchName == 'dev') {
        echo "Deploying to UAT"
       
    } else {
        echo "Deploying to a non-production/non-UAT branch: ${branchName}"
      
    }
}
