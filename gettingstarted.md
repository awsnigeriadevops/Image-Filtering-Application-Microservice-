# Getting Started

### Prerequisites
    1. Install Git: https://git-scm.com/downloads
    2. Install NodeJS v12.14 or greater up to v14.15
    3. AWS CLI v2: https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html
    4. Configure AWS user (with Admin permissions) to terminal


 To run this project, you are expected to have:
 1. An S3 bucket 
	- The project uses an AWS S3 bucket to store the user-uploaded pictures.
	-  Create S3 buckt, Add bucket policy allowing other AWS services (Kubernetes) to access the bucket contents.
    - You can use the permissions below: 

                ``` {
                "Version":"2012-10-17",
                "Statement":[
                    {
                        "Sid":"Stmt1625306057759",
                        "Principal":"*",
                        "Action":"s3:*",
                        "Effect":"Allow",
                        "Resource":"arn:aws:s3:::[bucket-name]"
                    }
                ]
                } ```


 2. Add the CORS configuration to allow the application running outside of AWS to interact with your bucket. You can use the following configuration:

 ```
            [
            {
                "AllowedHeaders":[
                    "*"
                ],
                "AllowedMethods":[
                    "POST",
                    "GET",
                    "PUT",
                    "DELETE",
                    "HEAD"
                ],
                "AllowedOrigins":[
                    "*"
                ],
                "ExposeHeaders":[
                    
                ]
            }
        ]
 ```
 

 2. Creat A PostgreSQL database, make sure you have all configurations set and inbound security rules,
    make sure you can connect to the db using this command.

3. Set up the Environment variables to store sensitive information
    - Edit set_env.sh 