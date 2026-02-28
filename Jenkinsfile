pipeline {
    agent {
        label 'gcc'  // Use agent-gcc 
    }
    
    environment {
        CC = 'gcc'
        CFLAGS = '-Wall -O2'
    }
    
    stages {
        stage('Checkout') {
            steps {
                echo '========================================='
                echo 'Stage 1: Checking out code from GitHub'
                echo '========================================='
                checkout scm
                echo 'Code checkout completed successfully!'
            }
        }
        
        stage('Build') {
            steps {
                echo '========================================='
                echo 'Stage 2: Compiling with GCC'
                echo '========================================='
                sh '''
                    ${CC} ${CFLAGS} -o hello src/hello.c
                    echo "Build completed successfully!"
                '''
            }
        }
        
        stage('Test') {
            steps {
                echo '========================================='
                echo 'Running the compiled program...'
                echo '========================================='
                sh '''
                    ./hello
                '''
            }
        }
        
        stage('Archive') {
            steps {
                echo '========================================='
                echo 'Archiving artifacts...'
                echo '========================================='
                archiveArtifacts artifacts: 'hello', fingerprint: true
            }
        }
    }
    
    post {
        success {
            echo '========================================='
            echo 'Pipeline completed successfully!'
            echo '========================================='
        }
        failure {
            echo '========================================='
            echo 'Pipeline failed. Please check the logs.'
            echo '========================================='
        }
    }
}