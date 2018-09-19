pipeline  {
   agent any
    
  stages {
     
     stage('unit Tests') {
      steps {
        sh 'ant -f test.xml -v'
        junit 'reports/result.xml'
       }
     }

    stage('build') {
  
     steps {
       sh 'ant -f build.xml -v'
       }
    post {
     success {
        archiveArtifacts artifacts:'dist/*.jar', fingerprint: true
        }
      }
    }

    stage('deploy') {
    
      steps {
      sh "cp dist/rectangle_${env.BUILD_NUMBER}.jar /var/www/html/rectangles/all/" 
     }
   }
   stage("Running on centos") {
      steps {

        sh "wget http://<hostname>/rectangles/all/rectangle_${env.BUILD_NUMBER}.jar"
        sh "java -jar rectangle_${env.BUILD_NUMBER}.jar 3 4"
        }
      }
     }
   }

