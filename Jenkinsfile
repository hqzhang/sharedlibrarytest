/////////////use library defination//////////////
library identifier: 'custom-lib@main', retriever: modernSCM(
  [$class: 'GitSCMSource',
   remote: 'https://github.com/hqzhang/sharedlibrarytest.git',
   credentialsId: ''])
def repo=scm.getUserRemoteConfigs().toString()
def brch='main'
/////////////use resources defination//////////////

def request=libraryResource 'com/wavecloud/request.json'
println request
/////////////use var defination//////////////
log('Starting')
log.info('Ending')
sayHello.sayHello()

String getBranchList(String repo, String dft ){
   def ret=[]
   def out = "git ls-remote --heads ${repo}".execute().text
   out = out.readLines().collect { it.split()[1].replaceAll('refs/heads/', '') }
   out.each{ if( it.contains(dft) ){ ret.add(0,'"'+it+'"') } else { ret.add('"'+it+'"') } }
   return """ return ${ret} """
}
properties([
    //pipelineTriggers([bitbucketPush()]),
    parameters([
            choice( name: 'Environment', description: '', choices: ['DEV','BAT'] ),

            [$class: 'CascadeChoiceParameter', choiceType: 'PT_SINGLE_SELECT', filterLength: 1, filterable: false,
               name: 'getBranchList', randomName: 'choice-parameter-16677189047440', referencedParameters: 'Environment', 
               script: [$class: 'GroovyScript', fallbackScript: [classpath: [], oldScript: '', sandbox: true, script: ''], 
               script: [classpath: [], oldScript: '', sandbox: true, 
               script: getBranchList(repo,'main') ]]],

])])

pipeline {
    agent any
    stages {
        stage('Create List') {
            steps {
                script {
                    echo "STAGE: create List..."
                   
                    echo "params======$params"
                    //def z = new com.wavecloud.Zot()
                    //z.checkOutFrom(repo)
                    sh ' echo Hello world'
                    log.info 'Starting'
                    log.warning 'Nothing to do!'
                }

            }
        }
    }
  
}