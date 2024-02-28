node{
  def gitcommit
  stage('checkout scm'){
    checkout scm
    sh 'git rev-parse --SHORT HEAD > .git/gitcommitid'
    gitcommit = readFile('.git/gitcommitid').trim()
  }
  
  stage('build only-dev & test'){
    nodejs(nodeJSInstallationName: 'nodejs'){
      sh 'npm install --only-dev'
      sh 'npm install'
    }
  }
  
  stage('docker build & push'){
    //docker.withRegistry('https://registry.hub.docker.com/','docker'){
     // def appimage = docker.build('macloujulian/nodejsapp:${gitcommit}','.')
    //  app.push()
   // }
    sh 'echo done!'
  }
}
