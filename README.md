# JBoss Windup Docker image

This is a Dockerfile with [JBoss Windup](http://windup.jboss.org/).

## Usage

To boot it

    docker run -it jboss/windup

To run it locally, clone this repository and move to the `windup` directory.
	
	docker build -t windup_img .

and then

	docker run --name windup_ins windup_img


## Image internals

This image extends the [`jboss/base-jdk:7`](https://github.com/JBoss-Dockerfiles/base-jdk/tree/jdk7) image which adds the OpenJDK distribution on top of the [`jboss/base`](https://github.com/JBoss-Dockerfiles/base) image. Please refer to the README.md for selected images for more info.

JBoss Windup is installed in the `/opt/jboss/windup` directory.

## Source

The source is [available on GitHub](https://github.com/JBoss-Dockerfiles/windup).

## Issues

Please report any issues on [JIRA](https://issues.jboss.org/browse/WINDUP).