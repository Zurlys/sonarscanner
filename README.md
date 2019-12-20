# sonarscanner

To analyse the project located in `/path/to/project`, execute:

```
docker run -e SONAR_HOST_URL=http://foo.acme:9000 -it -v "/path/to/project:/usr/src" zurlys/sonarscanner
```

To analyse the project in the current directory, execute:

```
docker run -e SONAR_HOST_URL=http://foo.acme:9000 -it -v "$(pwd):/usr/src" zurlys/sonarscanner
```

## Supported environment variables

### SonarQube host and authentication

* `SONAR_HOST_URL`: URL to the SonarQube instance the scanner should connect to (default=`http://localhost:9000`)
* `SONAR_TOKEN`: the prefered way to authenticate to SonarQube is to use a token. Use this environment variable to pass it to the scanner
* `SONAR_PROJECT_KEY`: Project key in SonarQube
* `SONAR_LOGIN` and `SONAR_PASSWORD`: alternatively, you can provide the SonarQube username and password for the scanner to use using these two variables

### Project mounting point

By default, the scanner analyses the project in directory `/usr/src`.

If you can't mount the project into this directory (eg. in Gitlab CI), use `SONAR_PROJECT_BASE_DIR` to specify another location in the container.

```
-e SONAR_PROJECT_BASE_DIR=/build
```
