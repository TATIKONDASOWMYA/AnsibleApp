pipeline{
agent any
tools{
maven 'Maven'
}
environment{
LANG='en_US.UTF-8'
LC_ALL='en_US.UTF-8'
}
stages{
stage('CheckOut'){
steps{
git branch: 'master', url:'https://github.com/TATIKONDASOWMYA/AnsibleApp.git'
}
}
stage('build'){

steps{
sh 'mvn clean package'
}
}

stage('archive')
{

steps{
archiveArtifacts artifacts:'target/*.war', fingerprint:true
}
}
stage('Deploy'){
steps{
sh 'mvn clean package'

sh 'ansible-playbook ansible/playbook.yml -i ansible/hosts.ini'
}
}
}
post{
success{
echo 'success'
}
failure{
echo 'failed'
}
}
}
