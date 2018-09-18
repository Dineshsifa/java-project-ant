pipeline {
         agent any
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
