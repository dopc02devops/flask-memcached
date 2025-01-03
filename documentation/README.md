
############################
# Install
############################
- pip install flask pymemcache
- brew install  memcached
- start service
- memcached -d -m 64 -p 11211 -u memcache
- pip install -r src/requirements.txt
- pip freeze > src/requirements.txt
- source venv/bin/activate

############################
# Build the Docker Image
############################
- docker build -t python-memcached-app .  
- docker build --no-cache -t python-memcached-app .
- docker run -it --rm --name python-memcached-container -p 8090:8088 python-memcached-app
- docker run -it --rm --name python-memcached-container python-memcached-app
- docker run -it --rm -p 8095:8095 -e HOST=0.0.0.0 -e PORT=8095 --name python-memcached-container python-memcached-app
- docker run -it --rm -p 8095:8095 --name python-memcached-container python-memcached-app

############################
# Explanation:
############################
-it: Runs the container in interactive mode.
--rm: Automatically removes the container after it stops.
--name python-memcached-container: Names the container python-k8s-container.
python-memcached-app: Specifies the image to run.
-p 8090:8088: Maps port 8000 inside the container to port 8080 on the host.
8090: The port you’ll use to access the app on your host.
8088: The port your application is listening to inside the container.

##########################
# docker commands
##########################
- docker ps
- docker inspect f0a4e7e8ac76e0e6044240c8140106962c359a49571ec3879469050b968b45dd | grep "IPAddress"
- docker inspect f0a4e7e8ac76e0e6044240c8140106962c359a49571ec3879469050b968b45dd | grep "NetworkMode"
- docker logs f0a4e7e8ac76e0e6044240c8140106962c359a49571ec3879469050b968b45dd# flask-memcached

- TEST_TAG="home" docker-compose -f docker-compose.test.yml run --rm test-app
- TEST_TAG="home" docker-compose -f docker-compose.test.yml run --rm test-app /bin/bash
##########################
# Get ip
##########################
- curl ifconfig.me
- nslookup 13.40.154.147
##########################
# Add ssh key
##########################
- ssh-keygen -t rsa -b 4096 -C "terraform" -f ~/.ssh/id_kube_user_key
- ssh-keygen -t rsa -b 4096 -C "terraform" -f ~/.ssh/id_kube_user_key -N ""
- sudo ssh-keygen -t rsa -b 4096 -C "heketi" -f ~/.ssh/id_heketi_key -N ""
- ls -l ~/.ssh/id_gcp_key*
- ssh -i ~/.ssh/id_gcp_key kube_user@remote_ip to ssh into instance