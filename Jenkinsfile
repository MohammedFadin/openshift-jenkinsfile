/**
 * OpenShift runs containers with a custom UID, overridding the UID defined in docker images.
 * This is an example of how to run docker images from DockerHub in OpenShift. It comes with no warranty.
 *
 * Define HOME for containers running in OpenShift
 * Define user.home system property for maven as it relies on /etc/passwd to infer its value
 */
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
