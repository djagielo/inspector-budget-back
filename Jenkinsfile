podTemplate(containers: [
    containerTemplate(name: 'jdk14', image: 'openjdk:14.0.2-jdk', ttyEnabled: true, command: 'cat')
  ],
  volumes: [hostPathVolume(hostPath: '/home/dariusz/.m2', mountPath: '/root/.m2')]
  ) {
    node(POD_LABEL) {
        stage('Compile') {
            container('jdk14') {
                stage('Build a Maven project') {
                    sh './mvnw clean compile'
                }
            }
        }

        stage('Test') {
            container('jdk14') {
                stage('Build a Maven project') {
                    sh './mvnw test'
                }
            }
        }
    }
}