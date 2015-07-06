# JBoss Windup Docker image

This is a Dockerfile with [JBoss Windup](http://windup.jboss.org/).

## Usage

- To boot it

```
    docker run -it -v /path/to/your/app:/opt/jboss/application:rw jboss/windup
```

- This will mount the host directory, `/path/to/your/app`, into the container at `/opt/jboss/application`.

- To run it locally, clone [this repository](https://github.com/jboss-dockerfiles/windup) and move to the `windup` directory.

```	
	docker build -t windup_img .
```
- Then run

```
	docker run -it -v /path/to/your/app:/opt/jboss/application:rw --name windup_ins windup_img
```

- Once Windup starts and the command shell is prompted, the command `windup-migrate-app` is available, also your application will be available at `/opt/jboss/application`. This path will have `read/write` permission due to the `rw` parameter used, so you can create a folder called `output-report` inside (e.g `/opt/jboss/application/output-report`) to be the `--output` parameter that Windup uses to save the generated report.

- After report have been generated, you can access it also from the host by checking the path you mounted locally. Note you will see that the `output-report` folder was created locally as well, and the report is inside it.   

## Image internals

This image extends the [`jboss/base-jdk:7`](https://github.com/JBoss-Dockerfiles/base-jdk/tree/jdk7) image which adds the OpenJDK distribution on top of the [`jboss/base`](https://github.com/JBoss-Dockerfiles/base) image. Please refer to the README.md for selected images for more info.

JBoss Windup is installed in the `/opt/jboss/windup` directory.

## Source

The source is [available on GitHub](https://github.com/JBoss-Dockerfiles/windup).

## Issues

Please report any issues on [JIRA](https://issues.jboss.org/browse/WINDUP).