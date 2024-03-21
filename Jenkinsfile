library('jenkins-pipeline-setup')

String webhooks = 'webhooks'
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
