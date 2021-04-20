## My CEG3120 Project4 Documentation

### Project Overivew
### Run Dockerize website and test Locally
- Install Docker for Windows/Dependencies
    - WSL2
    - source to install WSL2:
    https://docs.microsoft.com/en-us/windows/wsl/install-win10#step-4---download-the-linux-kernel-update-package
- Build & Run the container
    - run `docker run -d -p 80:80 docker/getting -started`
    - `docker ps` to see running container
    - `docker kill my_container_ID` to kill running container
    - create a `html` folder inside repo, create a `index.html` inside html folder.
    - create a `Dockerfile` inside repo
        - `FROM httpd:2.4` version of appache base
        - `COPY ./html/ /usr/local/apache2/htdocs/` where from are your machine and where to on the container
    - run the command to build and run the Docker image
        - `$ docker build -t my_image-name .`
        - `docker run -d -p 5000:80 my_image_name`
    - source:
    https://hub.docker.com/_/httpd
    https://www.docker.com/sites/default/files/d8/2019-09/docker-cheat-sheet.pdf
- Screenshoot of dockerized website
    - Open a browser and access the port via 127.0.0.1:5000 in this case
![milestone1screenshot](CEG3120Project4DockerizeWebsite.PNG)

### Configure AWS CLI
- How to Install
    - Pick an OS (I am install on WSL2)
    - Use commands: 
        - `curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"` - the current version of the AWS CLI
        - `unzip awscliv2.zip` - Unzip the installer
        - `sudo ./aws/install` - Run the install program
- How to Configure
    -  Use `aws configure` to enter the following information
        - in ` ~/.aws/credentials`, store the Secrets
            - `[default]` - references a "user"
            - `aws_access_key_id=`
            - `aws_secret_access_key=`
        - in `~/.aws/config`
            - `[default]`
            - `region=us-east-1`
            - `output=json`

### Create ECR in AWS CLI
- use command `aws ecr create-repository --repository-name ceg3120/w###aaa --region us-east-1`
    - Replace `w###aaa` with my `w###aaa`
    - `--repository-name ceg3120/w###aaa` - my repository name
    - `--region us-east-1` - my AWS region

### Configure Github Secrets
- My repository -> Settings -> Secrets
- Click New repository secret to add new secret
- Click Update to update secrets

### Configure Github Workflow
- In my repository, create `.github/workflows` directory.
- Viewing the results of a workflow
    - Actions -> click workflow -> click the run you want to see
    - Click the job you want to see
    - View the results of each step
- source for workflow template: https://docs.github.com/en/actions/guides/deploying-to-amazon-elastic-container-service
 
 

