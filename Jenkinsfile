

String registry = "dogandemir51"
String repository="parametrik deger"

pipeline {
    agent any
   
    environment{
        REGISTRY = "133897766177.dkr.ecr.ap-south-1.amazonaws.com"
        Image = "sample"
     }
     stages {
        stage('Build') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }
         stage("with mvn build project") {
         steps{
                                   echo "Java VERSION"
                                   sh 'java -version'
                                   echo "Maven VERSION"
                                   sh 'mvn -version'
                                   echo 'building project...'
                                  // sh "mvn compile"
                                  // sh "mvn package"
                                   //sh "mvn test"
                                   sh "mvn clean install"
         }
         }
         stage("docker build image"){
         steps{
          sh  ' docker build -f Dockerfile -t ${REGISTRY}/${Image}:v1 . '
          sh 'docker tag ${REGISTRY}/${Image}:v1'
         }

         }
       
         stage("Docker Push Image"){
         steps{
          sh  'docker push ${REGISTRY}/${Image}:v1'
         }

         }
       

     }
}
