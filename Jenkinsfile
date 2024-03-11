pipeline {
    agent any

    environment {
        SAUMYA_SSH_KEY = credentials('SAUMYA_SSH_KEY')
    }

    stages {
        stage('Deploy to WebLogic') {
            steps {
                script {
                    withCredentials([sshUserPrivateKey(credentialsId: 'SAUMYA_SSH_KEY', keyFileVariable: 'SSH_KEY')]) {
                        sh '''
                            ssh -i $SSH_KEY saumya@10.12.120.116 'ansible-playbook -i ansible_host/hosts playbook/nginx_install.yml'
                        '''
                    }
                }
            }
        }
    }
}
