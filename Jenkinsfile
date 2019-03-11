properties([
    parameters([
	    choice(name: 'MANIFEST', choices: ['develop'], description: 'Choose manifest for default image versions.'),
  		[ name: 'MY_VALUE',
            description: 'TAG_FINMIGRATOR',
            $class: 'ExtensibleChoiceParameterDefinition',
            editable: false,
            choiceListProvider: [
                $class: 'FilenameChoiceListProvider',
                baseDirPath: '/tmp',
				includePattern: '*',
				excludePattern: '',
				scanType: 'Directory',
				reverseOrder: false,
				emptyChoiceType: 'AtTop',
            ],
        ],
  ])
])

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
                sh 'echo MY_VALUE is ${MY_VALUE}'
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


