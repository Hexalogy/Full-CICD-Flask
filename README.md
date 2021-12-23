
# Full-CICD-Flask

1x EC2 Micro for Flask

1x EC2 Micro for Jenkins


## Install Flask
### Install Docker


## Install Jenkins
### Setup GitHub Webhook
1. Create **New Item** from Jenkins home page
2. Fill in application name and choose pipeline.After that click OK. This will create a pipeline based job on jenkins.
3. Fill in the general details in jenkins like description and github URL.
4. Check  **GitHub hook trigger for GITScm polling**  This will take update of project whenever we do changes in project and push the code.
5. In pipeline section, write down the pipeline code.
6. 
pipeline:
```
node {
   stage('Get Source') {
      // copy source code from local file system and test
      // for a Dockerfile to build the Docker image
      git ('https://github.com/upasana-mittal/flask-dockerized-jenkins.git')
      if (!fileExists("Dockerfile")) {
         error('Dockerfile missing.')
      }
   }
   stage('Build Docker') {
       // build the docker image from the source code using the BUILD_ID parameter in image name
         sh "sudo docker build -t flask-app ."
   }
   stage("run docker container"){
        sh "sudo docker run -p 8000:8000 --name flask-app -d flask-app "
    }
}
```
In pipeline, we are

1.  Getting project from github. Here we are assuming that project is in private repository.
    
2.  Building docker image
    
3.  Running docker container.
    

After above steps, save the job and trigger the build
