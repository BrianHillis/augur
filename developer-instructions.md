# Augur Group 19 Developer Instructions

## Step 1 

Follow the instructions on the augurlabs installation guide (http://augur.augurlabs.io/static/docs/dev-guide/2-install.html)  to get the requried dependencies for the machine you would like to run augur on

Then follow the instructions on the main github page of the chaoss augur repository to get your augur instance running (https://github.com/chaoss/augur/)

Instead of cloning the main chaoss augur repository, clone our version of augur at https://github.com/BrianHillis/augur.git

## Step 2

After running the "augur" command on your instance, an augur.config.json file will be created. 

In order to display multiple projects, this file needs to be edited. 

In the 'Facade" section of the file, there is an array that holds all the projects you would like to retrieve

Edit this list to reflect the projects you would like to see. 

## Step 3

Contact the database administrator to get a login to the Facade and GHTorrent databases and change the augur.config.json file to use each in their respective spots

## Step 4

Run a make install-dev and visit your instance to see multiple projects displayed 
