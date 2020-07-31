# HyperFrameOE-Wildfly

This is a group of WildFly Docker files with versions for HyperFrame Open Edition.

### Prerequisites

Docker 19.03.12 (This is a workspace's version, other versions might be compatiable with this.)

### Set up Info

1) OS : Debian GNU/Linux 10 (Base OS of openjdk:8 in dockerhub)
2) JDK : Openjdk 8 (build number 252) 
3) WildFly : WildFly 19.0.0.Final

### Directory layout

```bash
{pwd}                                                                       
|- release-image                                     #   
|   |- Dockerfile                                        # Dockerfile for base wildfly image using openjdk:8 on dockerhub
|- usage                                             #   
|   |- configuration                                     # 
|   |   |- application-roles.properties                      # 
|   |   |- application-users.properties                      # 
|   |   |- logging.properties                                # 
|   |   |- mgmt-groups.properties                            # 
|   |   |- mgmt-users.properties                             # 
|   |   |- standalone-full-ha.xml                            # Jakarta Full Platform certified configuration with high availability
|   |   |- standalone-full.xml                               # Jakarta Full Platform certified configuration including all the required technologies
|   |   |- standalone-ha.xml                                 # Jakarta web profile certified configuration with high availability
|   |   |- standalone-load-balancer.xml                      # 
|   |   |- standalone-microprofile-ha.xml                    # A configuration oriented toward microservices, similar to standalone-microprofile.xml but with support for high availability web sessions and distributed Hibernate second level caching.
|   |   |- standalone-microprofile.xml                       # A configuration oriented toward microservices, providing our MicroProfile platform implementations combined with JAX-RS and technologies JAX-RS application’s commonly use to integrate with external services.
|   |   |- standalone.xml                                    # Jakarta web profile certified configuration with the required technologies plus those noted in the table above.
|   |- deployments                                       # 
|   |   |- README.txt                                        # README of deployments
|   |   |- sample.war                                        # 
|- README.md
```

### Installing

#### 1. Download the release-image, usage directory.

#### 2. Build an 'Dockerfile' in release-image directory to make a base wildfly image.

```bash
$ docker build -t <hyperframeoe-wildfly> .
```

#### 3. If you want to modify server configuration or web application configuration, change files in usage/configuration/, usage/deployments directory.

#### 4. Place 'Dockerfile' of usage directory, 'configuration', 'deployments' directory in the same path.

#### 5. Build an 'Dockerfile' in usage directory to make a user setting image.

```bash
$ docker build -t <create image_name>:<image_version> .
```

#### 6. Generate a container using the image created in #5.

```bash
$ docker run -d -p 8080:8080 <image_name>:<image_version>
```
-> gerneral command

```bash
$ docker run -d -p 8080:8080 -p 9990:9990 -it <image-name>:<image-version> /opt/jboss/wildfly/bin/standalone.sh -b 0.0.0.0 -bmanagement 0.0.0.0
```
-> If you want to use management mode, use above command and access 9990 port.

### License

This project is licensed under the GNU Lesser General Public License Version 2.1
