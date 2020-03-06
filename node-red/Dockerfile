FROM nodered/node-red:1.0.4-12-arm32v7

######### Changing to root as below commands should be run as root #############

USER root
# Following command installs node-red-admin which is needed if you want to create a hashed password 
# for the node-red editor.  For that run command "node-red-admin hash-pw" in a terminal window
# for the node-red service in the BalenaCloud dashboard.
RUN npm install -g --unsafe-perm node-red-admin

# installing sudo command
RUN set -ex && apk --no-cache add sudo

# following command should assure that user node-red can use sudo without requiring to enter a password.
RUN echo "node-red ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers

######### Changing back to node-red user #####################
USER node-red

COPY ./settings.js /data/settings.js
COPY ./entrypoint.sh .

# the below entrypoint replaces the entrypoint of the nodered/node-red
ENTRYPOINT ["bash","entrypoint.sh"]