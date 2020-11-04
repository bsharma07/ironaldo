rm -rf docker-jenkins
makdir docker-jenkins
cd docker-jenkins
cp /varlib/jenkins/QAPackage/target/addressbook.var

touch dockerfile

from tomcat
ADD addressbook.war /usr/local/tomcat/webapps
CMD "catalina.sh" "ruh"
EXPOSE 8080
EOT
sudo docker build =t devopstrainer/deploy:$Build_number
sudo docker run -itd --name container-$BUILD_NUMBER -P deveopsstrainer/deploy:$BUILd_NUMBER




node {
    for(int i=0; i <2; i++){
        
        
        stage "Stage 3" +i
        
        if(i =0)
        {
            git 'https://github.com/bsharma07/eShopOnContainers.git'
            echo 'Running on Stage #9'
        }
        else {
            
            build 'Declarative pipeline'
            echo 'Running on Stage #1'
        }
        }
    }
}
