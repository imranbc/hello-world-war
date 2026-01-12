pipeline {
stages {
stage('checkout') {
steps {
sh "rm -rf"
sh 'git clone https://github.com/imranbc/hello-world-war.git'
}
}
stage ('Build') {
steps {
sh '''
ls
pwd
cd helo-world-war
echo $pwd
ls
mvn clean package
echo "build completed"
'''
}
}
stage ('Deploy') {
steps {
sh '''
echo "Deploying war to tomcat"
sudo cp hello-world-war/target/*.war /opt/tomcat/webapps/
sudo /opt/tomcat/bin/shutdown.sh || true
sleep 5
sud /opt/tomcat/bin/startup.sh 
echo "Deployment Completed"
'''
}
}
}
}
