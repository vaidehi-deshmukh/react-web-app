pipeline
{
 agent any
  
 tools
  {
   nodejs 'node'
  }
  
  stages
  {
   stage('Build')
    {
      steps
      {
       script
        {
         cleanWs()
         checkout changelog: false, poll: false, scm: [$class: 'GitSCM', branches: [[name: '${RepoBranch}']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/vaidehi-deshmukh/react-web-app.git']]]
         sh '''
         ls -ltr
         npm install
         npm run build
         ls -ltr
         cd build/
         ls -ltr
         tar -cvf frontend-${BUILD_NUMBER}.tar *
         ls -ltr
         '''
        }
      }
    }
  }
}
