# Useful Docker Commands

## List all running containers
~~~
docker ps
~~~

## List all running and stopped containers
~~~
docker ps -a
~~~

## Build and tag an image ready for storage in ECR
~~~
docker build -t appname:1.2.4 ./misp --tag 000000000000.dkr.ecr.ap-southeast-2.amazonaws.com/appname:1.2.4
~~~
note: replace 000000000000 with AWS account number and change region if required

## Push image to ECR
~~~
docker push 000000000000.dkr.ecr.ap-southeast-2.amazonaws.com/appname:1.2.4
~~~

## Terminate and re-deploy Elastic Beanstalk application using saved config
~~~
eb terminate --force && eb create appname -cfg appname
~~~

## Clear all saved images and containers locally
~~~
docker rm -f $(docker ps -a -q)
docker rmi -f $(docker images -q)
~~~

### Check it worked
~~~
docker ps -a
docker images
~~~

## Stop containers
~~~
docker sigterm
~~~
Terminate gracefully

~~~
docker sigkill
~~~
Terminate immediately

~~~
docker sigstop
~~~
Pause container

~~~
docker sigcont
~~~
Resume from pause
