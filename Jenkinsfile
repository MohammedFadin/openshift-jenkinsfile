podTemplate(cloud: "openshift", yaml:'''
spec:
  containers:
  - name: dotnet
    image: docker-registry.default.svc:5000/devops/demo:latest
    command: ['cat']
    tty: true
''') {
  node(POD_LABEL) {
    stage('Build Fadin Project') {
      container('dotnet') {
        sh "Underworld!"
      }
    }
  }
}
