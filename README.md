# JBoss Windup Docker image

This is a Dockerfile with [JBoss Windup](http://windup.jboss.org/).

## Usage

- To boot it

```
    docker run -it -v /path/to/your/app:/opt/jboss/application:rw jboss/windup
```

- This will mount the host directory, `/path/to/your/app`, into the container at `/opt/jboss/application`, and show the help usage print out. 

- If you need to provide more Windup CLI arguments add them after Docker image name.

- To run it locally, clone [this repository](https://github.com/jboss-dockerfiles/windup) and move to the `windup` directory.

```	
	docker build -t windup_img .
```
- Then run

```
	docker run -it -v /path/to/your/app:/opt/jboss/application:rw --name windup_ins windup_img
```

- Once Windup starts and the command show as processing, your application will be available at `/opt/jboss/application`. This path will have `read/write` permission due to the `rw` parameter used, so Windup can create a folder called `<application_name>.report` inside (e.g `/opt/jboss`) to be the `--output` parameter that Windup uses to save the generated report.

- After report have been generated, you can access it also from the host by checking the path you mounted locally. Note you will see that the `<application_name>.report` folder was created locally as well, and the report is inside it.   

## Image internals

This image extends the [`jboss/base-jdk:8`](https://github.com/JBoss-Dockerfiles/base-jdk/tree/jdk8) image which adds the OpenJDK distribution on top of the [`jboss/base`](https://github.com/JBoss-Dockerfiles/base) image. Be aware that the `jboss/base` assume your user and group id on host system is 1000. If your user is different you can have problems with *Permission Denied Error Messages*. Please refer to the README.md for selected images for more info.

JBoss Windup is installed in the `/opt/jboss/windup` directory.

## Source

The source is [available on GitHub](https://github.com/JBoss-Dockerfiles/windup).

## Issues

Please report any issues on [JIRA](https://issues.jboss.org/browse/WINDUP).
