node{
      stage('Clone') {
          checkout scm
      }
      stage('Connexion ssh'){
        
        sh "apk add ansible sshpass"
        sh "rm -rf /root/.ssh"
        sh "echo "192.168.158.132 app-salaire.dimitri.form" > /etc/hosts"
        sh "ssh-keygen -q -t rsa -N '' -f ~/.ssh/id_rsa"
        sh "sshpass -p 'P@ss4ing' ssh-copy-id -o stricthostkeychecking=no root@app-salaire.dimitri.form"
            
      }
      stage('Playbook') {
        ansiblePlaybook (
            colorized: true,          
            playbook: 'playbook.yml',
            inventory: 'hosts.yml'
        )
      }
  }
