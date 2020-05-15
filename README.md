# tb-dev
things dev
You can test these steps. I used it on my server which is also ubuntu 18.04:
cd
sudo rm -r .m2
sudo rm -r .maven
#Install maven 3.6.1
wget https://archive.apache.org/dist/maven/maven-3/3.6.1/binaries/apache-maven-3.6.1-bin.zip
unzip apache-maven-3.6.1-bin.zip
sudo mv apache-maven-3.6.1 /opt/maven
sudo nano /etc/profile.d/mavenenv.sh
#add the 2 lines below into mavenenv.sh
export M2_HOME=/opt/maven
export PATH=${M2_HOME}/bin:${PATH}

sudo chmod +x /etc/profile.d/mavenenv.sh
source /etc/profile.d/mavenenv.sh
#Check version to ensure you installed 3.6.1
mvn --version
#Install nodejs and other things
sudo apt install nodejs nodejs-dev node-gyp libssl1.0-dev -y
sudo apt install npm -y
sudo apt install openjdk-8-jdk
#Change java to jdk8
sudo update-alternatives --config java
#Check java version
java -version
#Very important: ensure JAVA_HOME is pointed to jdk8
export JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64
#Clone 2.4 release
git clone -b release-2.4 --single-branch https://github.com/thingsboard/thingsboard.git
cd thingsboard
git checkout -b release-2.4
sudo git clean -fdx
mvn clean install -DskipTests
sudo dpkg -i application/target/thingsboard.deb

https://github.com/thingsboard/thingsboard/issues/1952
