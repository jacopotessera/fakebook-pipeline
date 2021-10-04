podTemplate(containers: [
    containerTemplate(name: 'maven', image: 'maven:3.8.1-jdk-11', command: 'sleep', args: '99d')
  ]) {

    node(POD_LABEL) {
        stage('Get a Maven project') {
            git 'https://github.com/jacopotessera/fakebook.git'
            container('maven') {
                stage('Build a Maven project') {
                    sh 'mvn test'
                    junit 'target/surefire-reports/TEST-io.next.fakebook.FakebookApplicationTest.xml
                }
            }
        }
    }
}
