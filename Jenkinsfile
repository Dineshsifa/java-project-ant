pipeline  {
   agent any
    
  stages {
     
     stage('unit Tests') {
      agent {
       label 'apache'
      }
      steps {
        sh 'ant -f test.xml -v'
        junit 'reports/result.xml'
       }
     }

    stage('build') {
     agent {
       label 'apache'
      }
  
     steps {
       sh 'ant -f build.xml -v'
       }
    
    }

    stage('deploy') {
      agent {
       label 'apache'
      }
    
      steps {
      sh "cp dist/rectangle_${env.BUILD_NUMBER}.jar /var/www/html/rectangles/all/" 
     }
   }
   stage("Running on centos") {
      steps {

        sh "wget http://zippyops/rectangles/all/rectangle_${env.BUILD_NUMBER}.jar"
        sh "java -jar rectangle_${env.BUILD_NUMBER}.jar 3 4"
        }
      }
     }
post {
     success {
        archiveArtifacts artifacts:'dist/*.jar', fingerprint: true
        }
      }
   }
