library identifier: 'custom-lib@main', retriever: modernSCM(
  [$class: 'GitSCMSource',
   remote: 'https://github.com/hqzhang/sharedlibrarytest.git',
   credentialsId: ''])

properties([
    //pipelineTriggers([bitbucketPush()]),
    parameters([

            choice( name: 'Environment', description: '', choices: ['DEV','BAT'] ),
            [$class: 'CascadeChoiceParameter', choiceType: 'PT_SINGLE_SELECT', filterLength: 1, filterable: false,
               name: 'getBranchList', randomName: 'choice-parameter-16677189047440', referencedParameters: 'Environment', 
               script: [$class: 'GroovyScript', fallbackScript: [classpath: [], oldScript: '', sandbox: true, script: ''], 
               script: [classpath: [], oldScript: '', sandbox: true, 
               script: getBranchList(repo,brch) ]]],

])])

pipeline {
    agent any
    stages {
        stage('Create List') {
            steps {
                script {
                    echo "STAGE: create List..."
                    myMethods.greet("Alice")
                    echo "params======$params"
                    def z = new com.wavecloud.Zot()
                    z.checkOutFrom(repo)

                    log.info 'Starting'
                    log.warning 'Nothing to do!'
                   
    
                }

            }
        }
    }
  
}

