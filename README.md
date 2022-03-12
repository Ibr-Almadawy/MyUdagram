# Deployment Process **Udagram** 

## Table of contents

    1. Project description.
    2. How to use.
    3. Project folders and files.
    4. Deploying process steps.
    5. Another specific files. 
    6. References.

## 1. Project description:
 Udagram is a project for deployment and hosting process training, it provide a lot of fundmentals for web hosting to the cloud using various technologies like Amazon web services (AWS), Circleci and Github.

## 2. How to use:
 Every one can use the web page Udagram through this [Udagram website link](http://udagram20030200.s3-website-us-east-1.amazonaws.com), This link can take you to the "home" page for the website, Which you can find a **Register** and **Log in** to access the site main function to post your favourite images.

 ## 3. Project folders and files:
 This project start with 2 main folders:
  - **udagram-api:**
   This folder contains all back-end files and provide the main files *server.ts* and *sequelize.ts* to setup server and connect database, also contains *config.ts* which contains the enviroment variables pulled from *.env* file, also contains the *package.json* which contains all the dependencies to build and run back-end code and all scripts to interact with back-end.
  - **udagram-frontend:**
   This folder contains the main *Angular* files for the front-end, also there is a files for testing *End To End testing* and *Unit testing, also there is the front-end *package.json* file which contains all the dependencies to build and run back-end code and all scripts to interact with front-end.
   - **Root level:**
   Main *package.json* provided in the root level (will discuss in "Deploing process steps" section), and *README.md* file (this file), and another important folder in the root level initiated *.circleci* (Also I will discuss in "Deploing process steps" section).

## 4. Deploying process steps:
  - **First** 
  Trying to setup project locally, After got a good time with the back-end code in *udagram-end* folder, I found that we need to initiate a Enviroment variables file *.env* inside the back-end root to let the *config.ts* file pull all this variabes to push it to back-end files and this variables are:

    1. POSTGRES_USERNAME
    2. POSTGRES_PASSWORD
    3. POSTGRES_DB
    4. POSTGRES_PORT
    5. POSTGRES_HOST
    6. PORT
    7. URL
    8. AWS_REGION
    9. AWS_PROFILE
    10. AWS_BUCKET
    11. AWS_ACCESS_KEY_ID
    12. AWS_SECRET_ACCESS_KEY
    13. JWT_SECRET
    
    I found that developer used same PORT variable for both database connection and setup server, For that I Declared POSTGRES_PORT variable to handle this error, after that added the needed variables to *config.ts* and change the sequelize string to connect to database inside *sequelize.ts*, by tring to run server it got successed on PORT **8080**. 

- **Second** 
Review the *package.json* file inside *udagram-api* folder and all scripts defined successfully but I add "deploy" script and also set its configuration, and review also all dependencies and devdeprndencies.

- **Third** 
Running all back-end scripts and all of it returns success after setup elastic beanstalk cli to run deploy script.

- **Fourth** 
Reviewing the front-end code inside *udagram-frontend* folder, starting by *package.json* and review all dependencies and devdeprndencies, and run all the scripts and all returns success, also tests run successfully, but also we define "deploy" script to run with aws cli, and creating a file containing the deploying script *deploy.sh*.

- **Fifth**
 Going to the root level to see *package.json* and define all this scripts:

  - **To install dependencies and devdeprndencies:**
    1. "front:install"
    2. "back:install"
  - **To build code into www folder:**
    1. "front:build"
    2. "back:build"
  - **To test front-end:**
    1. "front:test"
    2. "front:e2e"
  - **To deploy:**
    1. "front:deploy"
    2. "back:deploy"

 - **Sixth** 
 here we go to aws console to start our operations to:
 - Creating IAM user account:
  I created IAM user to get the aws needed **AWS_ACCESS_KEY_ID** and **AWS_SECRET_ACCESS_KEY** (will be needed to access aws from circleci dashboard).
 - **RDS service:**
  Setup a Postgres database instense.(Separate document attached *RDS.md*).
 - **Elastic beanstalk service:**
  Setup an enviroment inside elastic beanstalk.(Separate document attached *Enviroment.md*).
 - **S3 service:**
  Creating a bucket inside S3 dashboard. (Separate document attached *Bucket.md*).

 - **Sevnth** 
 Create an account on *Github.com* and setup Git in project folder to remote *Github* new repository with the local project folder on my own machine.

 - **Eighth** 
  Start by write down in a paper the pipeline structure and create *config.yml* file inside *.circlci* folder and write the structure.

 - **Ninth** 
I connected *Github* account to the created *circleci* accout to see my repository appears on *circleci* dashboard, before setup my project in *circleci*, I added the enviroment variable needed to run *circleci* process successfully, I set:
   * AWS_ACCESS_KEY_ID
   * AWS_SECRET_ACCESS_KEY  
   * AWS_DEFAULT_REGION

 - **Tenth** 
   Start setup project process in *circleci* with a error to test process and it failed and try to change a *config,yml* file and *push* to repository again to see the process started immediatilly on *circleci* dashboard automatically and completed successfully in all steps (Sreenshots attached inside root level *Screenshots* folder).

### Secrets configurations:
 All Secrets(Enviroment variables) in this project declared in 2 positions:
   1. ***Circleci*** (as discussed).
   2. ***Elastic beanstalk*** to connect to database.
   Screenshots attached inside root level *Screenshots* folder.

## 5. Another specific files:

  1. *RDS.md* (root/Docs).
  2. *Enviroment.md* (root/Docs).
  3. *Bucket.md* (root/Docs).
  4. *Screenshots* folder(root level).
  5. *Deployment flow.jpg* diagram (root/Docs/Diagram).

## 6. References:
  1. *circleci.com : Documentation*
  2. *aws.com : Documentation*
  3. *www.npmjs.com documentation* 
  4. *Udacity advanced full-stack web development course*
 



