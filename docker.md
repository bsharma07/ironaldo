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
