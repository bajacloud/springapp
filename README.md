# Spring4Shell Exploit POC

Exploit a Spring Application vulnerable to the Spring4Shell vulnerability. Read more about Spring4shell on our [blog](https://fourcore.vision/blogs/spring4shell-spring-core-0day).

## Usage

Requirements: [Docker](https://docs.docker.com/engine/install/) and [docker-compose](https://docs.docker.com/compose/install/)

```
$ ./exploit.sh 
```

[![asciicast](https://asciinema.org/a/INYFtvNtAahfzJpJVAgTTI9EW.svg)](https://asciinema.org/a/INYFtvNtAahfzJpJVAgTTI9EW)

## Vulnerable Spring Application

The vulnerable Spring application contains a GET and POST request handler for `/helloworld/greeting`. The `exploit.sh` script starts the app container running Tomcat 9.0 with the application packaged as a WAR and uses `curl` to write a webshell to `http://localhost:8080/shell.jsp`. The shell is used to grab the flag present at `/flag` inside the container's filesystem.

## CVE-2022-22965

The **CVE-2022-22965** with a **CVSS** score of **9.8** has been to the vulnerability in Spring Core allowing Remote Code Execution. The exploit is easy to achieve and hence the high CVSS score, pre-requisites for the exploit are:

- JDK version 9+
- Application built on Spring Or derived frameworks
- Running Tomcat with WAR deployment

## Resources

- [Spring Blog Early Announcement](https://spring.io/blog/2022/03/31/spring-framework-rce-early-announcement)
- [Lunasec blog](https://www.lunasec.io/docs/blog/spring-rce-vulnerabilities/)
- [English translation of chinese researcher's original report](https://github.com/tweedge/springcore-0day-en)

## Credits

Based on the exploit and application by [reznok](https://github.com/reznok/Spring4Shell-POC).
