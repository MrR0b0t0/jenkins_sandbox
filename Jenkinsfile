pipeline {
    agent any
    options {
      buildDiscarder logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '25', daysToKeepStr: '', numToKeepStr: '25')
      disableConcurrentBuilds()
    }
    stages {
        stage('GIT Pull') {
            steps {
                cd /home/rbendik/dockerbuilds/repos/jenkins_sandbox
                git pull'
            }
        }
        stage('Execute Ansible') {
            steps {
                ansiblePlaybook( 
                    playbook: '/opt/home/madden/p4/tools/ansible/DL/madden/2023/deploy_conf/verify_blaze_service.yml',
                    inventory: '/opt/home/madden/p4/tools/ansible/DL/madden/2023/deploy_conf/inventory/local', 
                    credentialsId: 'ea-madden-ssh',
                    colorized: true)
            }
        }
        stage('Notify sucess') {
            emailext(
                to: 'rbendik@ea.com',
                subject: "${buildStatus}: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
                body: "details",
                recipientProviders: [[$class: 'DevelopersRecipientProvider']])
                }
        }
    
    }

}

