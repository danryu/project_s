# project_s
Minimal Go application deployment example using Vagrant, Ansible, Docker, docker-compose.

The deployment consists of 2 x Go application servers (derived from the official Docker golang image) and 1 x nginx load-balancer (in round-robin configuration, derived from official Nginx image).

In general, the absolute minimum configuration code has been applied, to demonstrate the efficiency of the tools being used. (Only around 100 lines of code is needed to implement all the above.)

## Requirements
Only one requirement: Vagrant 1.8+

## Installation
Clone the project:
`# git clone https://github.com/danryu/project_s.git`

## Invocation

Change directory to project clone directory and execute:

`# vagrant up`

## Operation

From project clone directory on host:

`# vagrant ssh`

You will now be logged in as user "vagrant".

Check the operation of the Go nodes and the Nginx round-robin load-balancer:

`# curl localhost`

And repeat to see the server node alternate.

## Automated deployment of changes

The ansible and docker configurations are made with idempotency in mind. After making edits to the sampleHi directory, a simple 

`# vagrant provision`

run from the Vagrant host (in the project clone dir) will restart the Docker containers with the new code applied.

