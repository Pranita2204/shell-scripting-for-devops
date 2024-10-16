#!/bin/bash

<<task
deploy a django app 
and handel the code for error
task
code_clone() {
        echo "cloning the django app"
        git clone https://github.com/LondheShubham153/django-notes-app.git
}


install_requirements() {
        echo "Installing dependencies"

        sudo apt-get install docker.io
        sudo apt install nginx

}

required_restarts() {
        sudo chown $USER /var/run/docker.sock
        sudo systemctl enable docker
        sudo systemctl enable nginx
        sudo systemctl restart docker
}

deploy() {
        docker build -t notes-app .
        #docker run -d -p 8001:8001 notes-app:latest

}

echo "***** DEPLOYMENT STARTED *****"

if ! code_clone; then
        echo "the code directory already exits"
        cd django-notes-app
fi

if ! install_requirements; then
        echo "Installation failed"
        exit 1
fi

if ! required_restarts; then
   echo "system fault identified"
        exit 1
fi

if ! deploy; then
        echo "Deployment failed, mailing the admin"
        # sendmail
        exit 1
fi

echo "***** DEPLOYMENT DONE *****"




