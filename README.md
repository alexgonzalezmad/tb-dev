CREATE BUILD
============

sudo apt-get update
sudo apt install openjdk-8-jdk
sudo apt-get install libpng-dev
sudo apt-get install maven
sudo apt install nodejs
sudo apt install npm
git clone https://github.com/thingsboard/thingsboard.git
cd thingsboard
git checkout release-2.4. | OR FOR 2.5 git checkout release-2.5
sudo npm install -g pkg
mvn clean install -DskipTests

BUILD LOGOTIPO
===============


SOLLUTION 1 INFORMATION:
------------------------

There can be 2 issues:

Either your SVG is not proper. This happened with me. I created a custom SVG using Inkscape, and it was not backwards compatible with SVG v1.1. You can read more about this issue on this question here.
You're not clearing out the old build files. When building the project afresh with new SVG files, first clear out the old files. This can be done easily using this git command:
git clean -fdx

SOLUTION INFORMATION 2:    MAS AJUSTADA 
-----------------------

0

Try this web: https://www.aconvert.com/image/png-to-svg/ to convert your png to svg. And download svg file, and place it to folder in ui/src/svg of thingsboard.

And then change the top of the file with this, i give attachment of picture to change it. Especially change the svg id.

https://i.stack.imgur.com/EW0kf.png 
https://i.stack.imgur.com/4O0AS.png


LINKS
=====

https://github.com/thingsboard/thingsboard/issues/1952
https://github.com/thingsboard/thingsboard/issues/1923
https://github.com/thingsboard/thingsboard/issues/1923

MODIFICAR LOGOTIPO
==================
https://stackoverflow.com/questions/44382732/custom-logo-not-updating-on-thingsboard-ui-after-custom-build


