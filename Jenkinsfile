node{
  def gitcommit
  agent any
  
  stage('checkout scm'){
    scm checkout
    sh 'git rev-parse --SHORT HEAD > .git/gitcommitid'
    gitcommit = readfile('.git/gitcommitid').trim()
  }
  
  stage('build only-dev & test'){
    nodejs(nodejsInstallation: 'nodejs'){
      sh 'npm install --only-dev'
      sh 'npm install'
    }
  }
  
  stage('docker build & push'){
    docker.withRegistry('https://registry.hub.docker.com/','docker')
    def image = docker.build('faustoobama/nodejsapp:${gitcommit}','.')
    app.push()
  }
}
