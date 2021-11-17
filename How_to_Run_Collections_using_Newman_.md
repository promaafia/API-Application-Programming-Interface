# How to Run Collections Using Newman

Another way to run a collection is via Newman. The main differences between Newman and Collection Runner are the following:

- Newman is an add-on for Postman. You will need to install it separately from the Native App.
- Newman uses the command line while Collection Runner has a GUI.
- Newman can be used for continuous integration.

To install Newman and run our collection from it, do the following:

#### Step 1
Install node js using this link: 

http://nodejs.org/download/

#### Step 2
Open the command line and enter

    npm install -g newman

Newman should now be installed on your computer.
#### Step 3 
Once Newman has been installed, let’s go back to our Postman workspace.In the Collections box, click on the three dots. Options should now appear. Select Export.
#### Step 4 
Choose Export Collection as Collection v2.1 (Recommended) then click Export.
#### Step 5 
Select your desired location then click Save. It is advisable to create a specific folder for your Postman tests. A collection should now be exported to your chosen local directory.
#### Step 6 
We will also need to export our environment. Click on the eye icon beside the environment dropdown in Global, select Download as JSON. Select your desired location then click Save. It is advisable that the environment should be in the same folder as your collection.
#### Step 7 
Environment should now be exported to the same local directory as Collection.
#### Step 8 
Now go back to the command line and change the directory to where you have saved the collection and environment.

cd C:\Users\Asus\Desktop\Postman Tutorial

#### Step 9
Run your collection using this command:

    Newman runs PostmanTestCollection.postman_collection.json -e Testing.postman_globals.json


 
For guide is a reference to some basic Newman codes for execution:

- **Run a collection only.** This can be used if there is no environment or test data file dependency.
- newman run <collection name> **Run a collection and environment.** The -e indicator is for the environment.
- newman run <collection name> -e <environment name> **Run a collection with desired no. of iterations.**
- newman run <collection name> -n <no.of iterations> **Run with data file.**
- newman run <collection name> --data <file name> -n <no.of iterations> -e <environment name> **Set delay time.** This is important as tests may fail if it is run without delay due to requests being started without the previous request completing processing on the endpoint server.

        newman run <collection name> -d <delay time>

