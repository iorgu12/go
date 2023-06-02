pipeline {
    agent any
 

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/iorgu12/go.git'
            }
        }
        
        stage('Test') {
            steps {
                bat 'go test'
            }
        }
        

        stage('Build') {
            steps {
                bat 'go build -o prog.exe prog.go'
            }
        }
        

         stage('Deploy') {
    steps {
        echo 'Deploying....'
        bat '''
            pscp -scp -i SSH_KEY path-to-main-module/prog.exe user@192.168.81.129:/home/iorgu/lab
            plink -ssh -i SSH_KEY user@192.168.81.129 "chmod +x /home/iorgu/lab/prog.exe && /home/iorgu/lab/prog.exe"
        '''
    }
}

    }
}

