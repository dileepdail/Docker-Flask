# Docker-Flask
Simple Flask App with Docker container

Steps for creating project

1. Check Docker Version

-> docker -v

2. Now that docker is ready lets see if you have any running containers.

-> docker ps

3. You can also check to see if you have any containers even if they are not running.

-> docker images

4. Create app.py for flask appliaction

5. Create requirements.txt for all requirements

6. Create Dockerfile

Dockerfile - this is a comment. Sample Dockerfile.
FROM python:2.7
COPY . /app
WORKDIR /app
RUN pip install -r requirements.txt
ENTRYPOINT ["python"]
CMD ["app.py"]

7. Now we can build our docker image.

-> docker build -t my_docker_flask:latest .

8. Now we can see what we created.

-> docker images

9. Check is it running?

-> docker ps

10. Docker Run

-> docker run -d -p 5000:5000 my_docker_flask:latest

    First thing is -d which detatches from the run. This means you won’t see any output. 
    You can remove the -d if you would like to see the run process.
    -p which specifies the port it is going to run on

11. check again

-> docker ps

12. check if app is running

-> on http://127.0.0.1:5000/

13. Push Your Image To Docker Hub

-> docker login -u dileepdail

14. Now we re-tag the image with your username prefix, <username>/.

-> docker tag my_docker_flask dileepdail/my_docker_flask

-> docker push dileepdail/my_docker_flask


15. Pull Your Image From Docker Hub

First kill the running docker image

-> docker ps
-> docker kill d00c58e82697

Remove it from our local docker instance completely.

-> docker system prune -a

16. Docker pull the image you pushed.

-> docker pull dileepdail/my_docker_flask

17. Now run like before, but remember, we have a new name. It is now prefixed with <your_username>/.

-> docker run -d -p 5000:5000 dileepdail/my_docker_flask:latest
-> docker ps
