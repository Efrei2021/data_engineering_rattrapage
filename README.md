# Data Engineering II Rattrapage
## **Twitter search web application** 

## Project Summary

As a part of the curriculum of the Master 2 (M2) course entitled “Data Engineering II”, each individual student 
will complete a project which combines all the skills collected throughout the entire course, 
and to provide a solid example of real-life application development in a DevOps environment.

The following sections provide necessary information about the description of the application  to be created.

For any further detail, please contact the instructor: **Khodor Hammoud**

## User Stories
* The application is an image search application, where the user inputs a search image, and 
the application returns the images which contain the same objects as in the search image. 
* For example, if one uploads an image of a chair, the application outputs all chair images 
available in the database.
* The application should have a web interface with an input form and a submit button, where 
users can upload their search image, and hit submit, then a list of the results is displayed.
* Functional parts of the application must be tested for proper functionality.
* The application must be able to handle 100 requests per minute.
* The application must be easily deployable.

# Technical Description
### 1. The Image Search
The students will use an ONNX Image classification model available at : 
[a link](https://github.com/onnx/models#image_classification) to do the image classification.
The application will have a database of images, each of which would have already been lableded, by
the ONNX model, according to what objects exist in it. For example, an image of a chair in the 
application database would be saved with the associated label “chaire”. Then, when a search image 
is provided, it is passed through the ONNX model to extract its lable, and that label is used to 
search for all images in the datases having a similar label.

### 2. The Web Interface
The students are free to choose whichever technology they know/like to create the web insterface. 
The end result should be a running application which the end user can access through a web 
browser, and start using immediately.

### 3. The Application Package
The final format of the application ready for distribution should be a Docker Image, which 
administrators can simply run Containers from. Students should provide a description file with their 
submitted application in which whey describe how to run their Docker image (like providing on 
which port does the application run by default…).

# Technical Requirements
The students are to use the following technologies and steps throughout their implementation:

### 1. Source Code Management
Each student is required to create a github repository containing their project, and use it as their version control. Each new task should have its own branch on the github repository. At every task completion, the student should merge her/his task’s branch to the master branch. The github repository should contain all your files, including the docker file and any meta data files (like the python requirements.txt if it exists).
Students must use the CD version control branching scheme, where the version control repository will contain a master branch, a develop branch, a feature branch (for every added feaure) and a release branch (for every version release).


### 3. Testing
Each student should provide unit, integration, end-to-end and stress tests to their final application.
- Unit tests are in the form of testing the functionality of each function of your program (when applicable).
- Integration testing will be testing combinations of functions, like clicking a button on the interface should trigger a submit function.
- End-to-end testing would be testing the entire functionality of the system, from frontend to backend.
- Stress testing will be writing a user simulation to prove that your application can handle 100 requests per minute.

### 4. Automation
The students are to use Jenkins for automating the building, testing, deployment and release (if applicable) of the application. At the end, each team is expected to have a Jenkins pipeline constructed which connects to the different github branches, and applies appropriate respective actions:
* build and run unit tests on feature branches.
* stress test and push to release on the develop branch
* wait for user acceptance on the release branch before pushing to master
* deploy on merging with master

**Note: as it might not be possible to have multiple development environments (develop, staging, live), relasing/deploying the code can be substituted with simple print statements.**

### 5. Containarization
The final application deliverable should be a Docker image, that contains the ONNX model as well 
as the application web interface. The images dataset should also be bundled with the application. 
Running a container off the delivered docker image should allow users to view a web interface on 
their browser and be able to immediately start running queries.
