# DeepPhe-Viz v0.1.0

Visualization of cancer patient summaries as generated by the DeepPhe NLP tools.

## Prerequisites

You must have the following tools install to build this project:

- [Nodejs 8.11.3 (includes npm 5.6.0, but we suggest to use the latest npm)](https://nodejs.org/en/download/)
- [Neo4j 3.2.13](https://neo4j.com/) is used to store the graph output

Currently, we have been successfully using the [nvm](https://github.com/creationix/nvm) tool to configure and manage our NodeJS environment; nvm enables a user to associate a paritcular NodeJS and NPM version with their Unix shell, allowing for each switching between NodeJS versions across different projects.

## Getting Started

First download/clone the `DeepPhe-Viz` repo and enter the project directory/

````
git clone https://github.com/DeepPhe/DeepPhe-Viz.git
cd DeepPhe-Viz
````

## Installation 

Installing this package and all its depedencies can be done with a simple command in the package root directory with no arguments:

````
npm install
````

## Configuration

There are two configuration files under the `configs/` directory:

- `neo4j.josn`
- `server.json`

First you will need to put your neo4j database connection username and password in `neo4j.json`. This assumes that have a running neo4j server and you've loaded the DeepPhe NLP gerenated data (Breast cancer data or Melanoma cancer data) into your Neo4j database. If you have set `dbms.security.auth_enabled=false` for your neo4j installation, you can set the user name and passwords to be empty strings (or ignore them).

The `server.json` is where you can define the HTTP server host and port number.

## Starting the Neo4J Database Server

Put the DeepPhe NLP generated `deepphe.db` under your `NEO4J_ROOT/data/databases/` and configure the `NEO4J_ROOT/conf/neo4j.conf` to point to this database.

Then go to the `NEO4J_ROOT/bin` and start the database server by using `./neo4j start` command.


## Launching The Viz Server

Now you can start the node server with

````
node server.js
````

This will start the web server on port 8383 by default. You can go to http://localhost:8383/cohortAnalysis to see the result.

Note: you can type `lsof -i :8383` to see if port 8383 is being used. 

## Development Mode

During development, you don't want to restart the server with `node server.js` every time after you make changes in the source code. [Nodemon](https://github.com/remy/nodemon) is a utility that will monitor for any changes in your source and automatically restart your server. Perfect for development. To install, 

````
npm install -g nodemon
````

Then just use `nodemon` instead of `node` to run your code, and now your process will automatically restart when your code changes.

````
nodemon server.js
````
