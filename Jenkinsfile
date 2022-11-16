pipeline {
agent any
stages {
stage ('Checkout') {
steps {
git branch:'master', url: 'https://github.com/IVIillionaire/Vulnerable-Web-Application.git'
}
}
stage('Code Quality Check via SonarQube') {
steps {
script {
def scannerHome = tool 'SonarQube';
withSonarQubeEnv('SonarQube') {
sh "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=OWASP -Dsonar.sources=. -Dsonar.host.url=http://172.18.0.4:9000 \
  -Dsonar.login=sqp_d0fe7e931a2218b9e8178830c425fcf406f8e153"
}
}
}
}
}
post {
always {
recordIssues enabledForFailure: true, tool: sonarQube()
}
}
}
