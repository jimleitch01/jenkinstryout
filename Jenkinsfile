properties([
    parameters([
	    choice(name: 'MANIFEST', choices: ['develop'], description: 'Choose manifest for default image versions.'),
        [ name: 'NAMESPACE',
            description: 'NAMESPACE',
            $class: 'ExtensibleChoiceParameterDefinition',
            editable: false,
            choiceListProvider: [
                $class: 'FilenameChoiceListProvider',
                baseDirPath: '/var/lib/jenkins/DROPDOWNS/namespaces',
				includePattern: '*',
				excludePattern: '',
				scanType: 'Directory',
				reverseOrder: false,
				emptyChoiceType: 'AtTop',
            ],
        ],
		[ name: 'TAG_FINMIGRATOR',
            description: 'TAG_FINMIGRATOR',
            $class: 'ExtensibleChoiceParameterDefinition',
            editable: false,
            choiceListProvider: [
                $class: 'FilenameChoiceListProvider',
                baseDirPath: '/var/lib/jenkins/DROPDOWNS/apps/finmigrator',
				includePattern: '*',
				excludePattern: '',
				scanType: 'Directory',
				reverseOrder: false,
				emptyChoiceType: 'AtTop',
            ],
        ],
  ])
])



parameters {
                  activeChoiceParam('choice1') {
                      description('select your choice')
                      choiceType('RADIO')
                      groovyScript {
                          script("return['aaa','bbb']")
                          fallbackScript('return ["error"]')
                      }
                  }
                  activeChoiceReactiveParam('choice2') {
                      description('select your choice')
                      choiceType('RADIO')
                      groovyScript {
                          script("if(choice1.equals("aaa")){return ['a', 'b']} else {return ['aaaaaa','fffffff']}")
                          fallbackScript('return ["error"]')
                      }
                      referencedParameter('choice1')
                  }







pipeline {

    // agent {
    //     node {
    //       label 'docker'
    //     }
    // }
    agent any

    options { 
        buildDiscarder(logRotator(numToKeepStr: '5')) 
    }

    environment {
        appName        = 'ted-be'
        acrName        = 'testifi'
        subscriptionId = 'xxxxxxxxx'
        aksCluster     = 'ted-aks'
        resourceGroup  = 'ted-rg'

    }
    stages {
        stage('INIT Stage') {
            steps {
                sh 'echo ##############################'
                sh 'echo BRANCH_NAME is ${BRANCH_NAME}'
                sh 'echo ##############################'
        }}


    }
    post {
        always {
            echo 'Build Complete'          
        }
        success {
            echo 'Build succeeded 8-)'
            echo 'UPDATING JIRA with Access information'
        }
        unstable {
            echo 'Build unstable 8-/'
        }
        failure {
            echo 'Build failed 8-('
        }
        changed {
            echo 'Build changed sincel last build'
        }
    }
}


