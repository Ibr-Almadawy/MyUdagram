## Infrastructure descreption 

This project created using an infrastructure of:
  1. ***AWS RDS*** for the database.
  2. ***AWS ElasticBeanstalk*** for hosting server.
  3. ***AWS s3*** for web hosting.

### 1. AWS RDS: ***(db-1)***
  To create a database instense to interact with server, I created this instense by setting options through AWS RDS page:
   * Setting database to ***Postgres***.
   * Setting port to **5432**.
   * Setting database to ***public***.
   * Setting databse user to the default user ***postgres*** and confirm a password to this user.
   * Setting database name as ***mydb*** and postgres created a default one ***postgres***.
   * Setting inbound traffic in the security group to ***0.0.0.0*** to let database accessable from any IP.
   * Get the ***endpoint link*** after database set to ***avaiable*** to provide the elastic beanstalk with this endpoint link to set connectivity between database and server.
   * Sreenshots avaiable inside *screenshots* folder in the root level shows:
     + RDS database status available.
     + RDS database status and endpoint.
     + pgAdmin 4 connected to my RDS successfully.
     + Posrbird shows connecting and saving data successfully.

### 2. AWS ElasticBeanstalk: ***(udagram-env-1)***
  I created elastic beanstalk enviroment with this options:
   * Setting to ***Web server***.
   * Setting application name to ***Udagram***.
   * Setting enviroment name as above.
   * Setting platform to ***nodejs***.
   * upload my back-end compiled code inside "www" directory which was build compressed in *zip* format.
   * Setting all enviroment variables inside configuration inside software section:
      + POSTGRES_HOST
      + POSTGRES_DB
      + POSTGRES_USERNAME
      + POSTGRES_PASSWORD
      + POSTGRES_PORT
      + PORT
      + URL
      + JWT_SECRET
      (as shown in screenshots).
   * After a while enviroment gives status of ***ok***.
   * Sreenshots avaiable inside screenshots folder in the root level shows:
      + Start creating EB enviroment.
      + Setting enviroment variables in EB.
      + EB enviroment created with health status **ok**.

### 3. AWS S3  ***(udagram20030200)***
   * Start by setting the elastic beanstalk url to the url for the front-endresponse inside *enviroment.ts* in the local root of front-end folder.
   * create a new bucket and set the above name for it.
   * Allow all public access.
   * Set the bucket policy in premission as:

       ` {
                "Version": "2012-10-17",
                "Statement": [
                {
                    "Sid": "PublicReadGetObject",
                    "Effect": "Allow",
                    "Principal": "*",
                    "Action": "s3:GetObject",
                    "Resource": "arn:aws:s3:::udagram20030200/*"
                }
                             ]
        }`

   * Start to upload the front-end compiled code inside folder *www*.
   * obtain the url provided inside "Static website hosting" in properties section, can be accessed through this [link](http://udagram20030200.s3-website-us-east-1.amazonaws.com).
   * Sreenshots avaiable inside screenshots folder in the root level shows:
     + S3 provides the full working link.
     + Uploading Angular files to S3.
     + S3 created ,files uploaded.
     + web site hosted successfully.
    
     


