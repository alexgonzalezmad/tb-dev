CREATE BUILD
============

sudo apt-get update
sudo apt install openjdk-8-jdk
sudo apt-get install libpng-dev
sudo apt-get install maven
sudo apt install nodejs instalar la 11 ver link en este documento:  https://geekflare.com/nodejs11-installation-guide/. 
sudo apt install npm
git clone https://github.com/thingsboard/thingsboard.git
cd thingsboard
git checkout release-2.4. | OR FOR 2.5 git checkout release-2.5

within thingsboard directory and outside:

first, npm install -g
sudo npm install -g pkg

CLEAN ENV

git clean -fdx
mvn clean install -DskipTests

BUILD LOGOTIPO
===============
To replace Thingsboard logo, you will need to build Thingsboard from source code.
The logo is defined in : thingsboard-src/ui/src/svg/logo_title_white.svg
You will need to replace this logo with your logo, but still using the same file name. Pay attention to the size (width and length) of original logo file, make sure your own logo has the same size.
My approach is to generate a PNG logo, with size similar to the original Thingsboard Logo. And then I use Inkscape(https://inkscape.org/) to convert the PNG file to SVG.
IMPORTANT : You have to remove the XML Tag in the SVG file you have just generated using Inkscape. Use text editor [ vim or nano] to delete the first line of the SVG file.
Now, you need to build or compile Thingsboard source code. Make sure the source code is clean. [ sudo git clean -fdx]. And build!


SOLLUTION 1 INFORMATION:
------------------------

There can be 2 issues:

Either your SVG is not proper. This happened with me. I created a custom SVG using Inkscape, and it was not backwards compatible with SVG v1.1. You can read more about this issue on this question here.
You're not clearing out the old build files. When building the project afresh with new SVG files, first clear out the old files. This can be done easily using this git command:
git clean -fdx

SOLUTION INFORMATION 2:    MAS AJUSTADA 
-----------------------

Try this web: https://www.aconvert.com/image/png-to-svg/ to convert your png to svg. And download svg file, and place it to folder in ui/src/svg of thingsboard.

And then change the top of the file with this, i give attachment of picture to change it. Especially change the svg id.

https://i.stack.imgur.com/EW0kf.png 
https://i.stack.imgur.com/4O0AS.png

LINKS
=====

https://github.com/thingsboard/thingsboard/issues/1952
https://github.com/thingsboard/thingsboard/issues/1923
https://github.com/thingsboard/thingsboard/issues/1923
https://geekflare.com/nodejs11-installation-guide/.           install nodejs11 punto importante
npm config set registry https://registry.npmjs.org/
https://www.javahelps.com/2015/04/install-intellij-idea-on-ubuntu.html.    install intelljs idea

MODIFICAR LOGOTIPO
==================
https://stackoverflow.com/questions/44382732/custom-logo-not-updating-on-thingsboard-ui-after-custom-build

NEW WAY UPDATE
==============
https://github.com/thingsboard/thingsboard/issues/1952


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

The next steps (database, demo, start) as in thingsboard document.
Hope this help you.


