pipeline {
    agent any

    environment {
        SAUMYA_SSH_KEY = credentials('SAUMYA_SSH_KEY')
        // WEBLOGIC_VM_IP = 'weblogic_vm_ip'
        // SSH_USER = 'weblogic_user'
    }

    stages {
        stage('Run Ansible Playbook') {
            steps {
                script {
                    withCredentials([sshUserPrivateKey(credentialsId: 'SAUMYA_SSH_KEY', keyFileVariable: 'SSH_KEY')]) {
                        sh '''
                            ansible-playbook -i ansible_host/hosts playbook/nginx_install.yml --private-key=$SSH_KEY
                        '''
                    }
                }
            }
        }
    }
}
