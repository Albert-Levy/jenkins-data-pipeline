pipeline {
    agent any
    
    environment {
        PYTHON_PATH = 'C:\\Users\\Albert\\AppData\\Local\\Programs\\Python\\Python312\\python.exe'
        PIP_PATH = 'C:\\Users\\Albert\\AppData\\Local\\Programs\\Python\\Python312\\Scripts\\pip.exe'
    }
    
    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/Albert-Levy/jenkins-data-pipeline.git', branch: 'main'
            }
        }
        
        stage('Install Pip') {
            steps {
                script {
                    def pipInstalled = bat(script: "${PYTHON_PATH} -m ensurepip", returnStatus: true)
                    if (pipInstalled != 0) {
                        error "Pip installation failed"
                    }
                }
            }
        }
        
        stage('Install Dependencies') {
            steps {
                script {
                    def pandasInstalled = bat(script: "${PIP_PATH} install pandas", returnStatus: true)
                    if (pandasInstalled != 0) {
                        error "Pandas installation failed"
                    }
                }
            }
        }
        
        stage('Run Data Analysis') {
            steps {
                bat "${PYTHON_PATH} data_analysis.py"
            }
        }
    }
}
