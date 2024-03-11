pipeline {
    agent any

    environment {
        SSH_PASS = credentials('SSH_PASS')
    }

    stages {
        stage('Deploy to WebLogic') {
            steps {
                script {
                    sshagent(credentials: ['${SSH_PASS}']) {
                        sh 'ansible-playbook -i ../ansible_host/hosts install_nginx.yml'
                    }
                }
            }
        }
    }
}
