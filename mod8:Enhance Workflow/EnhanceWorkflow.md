# Enhance the workflow

## Dangling images & volumes
---
Update makefile to remove dangling images during the clean target execution

Run the clean command
> `make clean`

Add LABEL to the base image and rebuild the image
> `docker build -t nileshgule/todobackend-base`

Commit the changes to github repo

Rebuild the test & release images
> `make test`

> `make build`

> `make release`

> `make clean`

Add -v flag to docker-compose rm command to remove the dangling volumes

Manually remove the dangling volumes by running command
>`docker volume rm $(docker volume ls -f dangling=true -q)`

Run the make test command
> `make test`

Run the make clean command
> `make clean`

## Improve user feedback
---
Add colourful messages to the output of make file to indicate the progress

## Make the workflow self contained
---
Add the copy command to ansible image to copy the probe.yml file

Rebuild the image
> `docker build -t nileshgule/ansible .`

Commit the changes to github repo

Modify the docker-compose in todobackend dev
 - Update the agent service by removing the volume mapping
 - Add the command to execute the probe.yml playbook from the /ansible working directory
 - Modify the builder service by replacing volume mapping with docker copy command
 - Modify the makefile to copy the artifacts using docker copy command

 Modify the docker-compose in todobackend release folder
 - Modify the agent service by removing volume maping & replacing with command invocation
 - Remove the volume mapping for todobackend.conf file in the nginx service
 - create a dockerfile from nginx image

 run the workflow
 > `make test`

 > `make build`

 > `make release`

## Producing test reports
---

## Handle errors
---

## Ensure consistency
---

## Tag & Publish
---

## Convert files to use Docker Compose V2 Specification
---