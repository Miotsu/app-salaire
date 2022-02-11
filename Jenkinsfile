  node{
      stage('Deploiement') {
          checkout scm
      }
      stage('test') {
       apk add ansible  sshpass
       rm -rf /root/.ssh
       ssh-keygen -q -t rsa -N '' -f /root/.ssh/id_rsa
       sshpass -p 'isoadmin' ssh-copy-id -o stricthostkeychecking=no root@192.168.11.103
      }
      
    
      stage('Ansible') {
        ansiblePlaybook (
            colorized: true,          
            playbook: 'playbook.yml',
            inventory: 'hosts.yml'
        )
      }
  }
