# quickwp
A docker-compose setup to clone any time you want a new install

Uses the visiblevc/wordpress-starter image.

## Initialization

### Prerequisites

* You'll need docker installed... google is your friend. Don't worry too much about learning docker at this point.
* You need git installed, again, google is your friend!


### Create a new project
`git clone https://github.com/mikesale/quickwp MyNewProjectName`

### Start up the container
CD into your MyNewProjectName and run the following command:

`docker-compose up -d`

You can see the status of the container with this command:
`docker ps`

It typically takes a minute or two to spin up everything depending on your machine and your internet connection.

## Access 

WP User: root
WP Password: root

DB Password: root
DB Connection Port: 9001

PhpMyAdmin Port: 22222

Finally access the site at:
http://localhost:8080

To get a command line in the container:

`docker exec -it $(docker ps -lq) /bin/bash`

WP-CLI is installed and you can run all the standard commands on a running container.

The ./app directory contains your WP install. You can copy files in after starting the container, etc. using your normal host OS/File manager, etc.

The ./plugins directory is where I put my local plugin zip files I want to install for this project. I can install them with the following command on a bash command line as noted above:

`wp plugin install /home/admin/plugins/myplugin.zip`

You can import a DB like this:


`docker-compose exec wordpress /bin/bash "wp db import $(find /data/*.sql | head -n 1) --allow-root"`
