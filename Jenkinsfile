node{
      stage('Clone') {
          checkout scm
      }
      stage('Connexion ssh'){
            
        sh 'apk add sshpass'
        sh 'rm -fr /root/.ssh/*'
        sh 'ssh-keygen -q -t rsa -N \'\' -f "/root/.ssh/id_rsa"'
        sh 'sshpass -p \'P@ss4ing\' ssh-copy-id  -o stricthostkeychecking=no "root@app-salaire.dimitri.form"'
        
            
      }
      stage('Playbook') {
        ansiblePlaybook (
            colorized: true,          
            playbook: 'playbook.yml',
            inventory: 'hosts.yml'
        )
      }
  }
