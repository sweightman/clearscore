# clearscore
clearscore

# simple instructions
1. ensure vagrant, virtualbox and virtualbox guest additions are installed on your local machine
2. then run this ...
git clone https://github.com/sweightman/clearscore.git
3. then run this in the root of the repo ...
vagrant up
4. then goto these links in a browser to see the content ...
http://localhost:8080 (haproxy address which forwards onto nginx)
http://localhost:9080 (direct to nginx address)
5. if you then run this ...
vagrant ssh
sudo service nginx stop
6. then goto to both http links above you will now see requests are not being served as nginx is down
7. if you then run ...
vagrant ssh
sudo service nginx start
8. both http links will show content again as nginx is running
