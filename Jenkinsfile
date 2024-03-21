library('jenkins-pipeline-setup')

String webhooks = 'webhooks'
String user = 'admin'
Script myScript

Map bindMap = [
  name: 'Prototype Load',
  containers: [webhooks]
]

podTemplate(yaml: podDef(bindMap)) {
  node(POD_LABEL) {
    container(webhooks) {
      stage('Prerequisites') {
        myScript = load "${env.WORKSPACE}/scripts/simple-function.groovy"
        echo "The function returned: ${myScript.meep()}"
      }
    }
  }
}



pipeline {
    agent any

    stages {
        stage('Load Script and Execute Function') {
            steps {
                script {
                    // Assuming 'groovyScripts' is a directory at the root of your repo
                    def myScript = load "${env.WORKSPACE}/groovyScripts/myScript.groovy"
                    myScript.myFunction()
                }
            }
        }
    }
}