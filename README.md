![HTML to PDF as a service](http://imgur.com/2LHbx9b.png)

HTML to PDF as a service *(H2PAAS)* it's a microservice in **nodeJS** created like option for developers that have some problems with PDF libraries like `wkhtmltopdf`.  

We create that the most generic as possible, but the library it's totally open source and you can contribute with what you need/want! We are waiting your PR :heart:  

## Running

You can running the project easily following the steps

```

git clone <this-repo-url>
cmhd +x configure_lc.sh && ./configure_lc

# For integration with AWS S3 export:
# export AWS_ACCESS_KEY_ID=<Your Access Key Id Here>
# export AWS_SECRET_ACCESS_KEY=<Your Secret Access Key Here>

npm install
npm start

```

If you want we have a `Dockerfile` to create a container for you :) 
```

docker build -t h2paas `pwd`
# For integration with AWS S3 add that before `pwd`
# --build-arg aws_keyid=<Your Access Key Id Here> --build-arg aws_secret_key=<Your Secret Access Key Here>
# If you change the ports in settings js you need pass --build-env port=<The Port>

docker run -i -t -p 3000:3000 h2paas
# Not forget to change 3000:3000 in case of change ports :)

```

### ALERT
**Don't commit your KEYS!**, we are using that like enviroment variables for some motive :) Be in alert to publicate your images into Dockerhub with your secret keys!

## Settings
Inside `/app` we have a `settings.js` file with some configurations that may you want to change :)

- **ALLOW_ORIGIN** *(array<string>)* will tell us the domains that can access your service
- **DEFAULT_BUCKET** *(string)* the default AWS Bucket 
- **ACL_DEFAULT** *(string)* the default AWS acl for the file
- **AWS_REGION** *(string)* the AWS region of your s3
- **S3_API_VERSION** *(string)* the version of S3 API
- **PORT** *(number)* the application port
- **HOST** *(string)* the application host