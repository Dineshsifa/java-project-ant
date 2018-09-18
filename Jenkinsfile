pipeline {
         agent any
options {
buildDiscards(logRotator(numTokeepstr: '2'. artifactNumTokeepstr: '1'))
}
         stages {
                 stage('build') {
                 steps {
                   sh 'ant -f build.xml'
}}

stage('unit Test'){
steps {
sh 'ant -f test.xml'
junit 'reports/results.xml'
}}}
post {
 always {
      archiveArtifacts artifacts: 'dist/*.jar', fingerprint: true
}
}
}
