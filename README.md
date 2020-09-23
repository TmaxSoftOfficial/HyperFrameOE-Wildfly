# HyperFrameOE-Wildfly

This WildFly docker file is for HyperFrame Open Edition.

### Prerequisites

Docker 19.03.12 (Workspace version, recommended)

### Requirements

1) OS: Debian GNU/Linux 10 (Base OS of openjdk:8 in dockerhub)
2) JDK: OpenJDK 8 (build number 252) 
3) WildFly: WildFly 19.0.0 

### Directory Structure

```bash
{pwd}                                                                       
|- release-image                                             # image folder  
|   |- Dockerfile(lastest)                                   # Dockerfile for base wildfly image using openjdk:8 on dockerhub
|- usage                                                     # usage folder  
|   |- configuration                                         # configuration folders
|   |   |- application-roles.properties                     
|   |   |- application-users.properties                      
|   |   |- logging.properties                                
|   |   |- mgmt-groups.properties                            
|   |   |- mgmt-users.properties                             
|   |   |- standalone-full-ha.xml                            # Jakarta Full Platform certified configuration with high availability
|   |   |- standalone-full.xml                               # Jakarta Full Platform certified configuration including all the required technologies
|   |   |- standalone-load-balancer.xml                     
|   |   |- standalone-microprofile-ha.xml                    # A configuration oriented toward microservices, similar to standalone-microprofile.xml but with support for high availability web sessions and distributed Hibernate second level caching.
|   |   |- standalone-microprofile.xml                       # A configuration oriented toward microservices, providing our MicroProfile platform implementations combined with JAX-RS and technologies JAX-RS application’s commonly use to integrate with external services.
|   |   |- standalone.xml                                    # Jakarta web profile certified configuration with the required technologies plus those noted in the table above.
|   |- deployments                                           # deployments folder
|   |   |- README.txt                                        # README of deployments
|   |   |- sample.war                                        # sample.war for deploy
|   |- Dockerfile
|- README.md
|- wildfly-latest-src.tar.gz
|- wildfly-latest.tar.gz
```

### Installation Steps

#### 1. Download Dockerfile.

#### 2. To change the configuration/deployments, modify files under the configuration/deployments directory.

#### 3. Place the Dockerfile file and the configuration and deployments directories in the same path.

#### 4. Build a Docker Image.

```bash
$ docker build -t <create image_name>:<image_version> .
```

#### 5. Generate a Container from the Image.

```bash
$ docker run -d -p 8080:8080 <image_name>:<image_version>
```
-> gerneral command

```bash
$ docker run -d -p 8080:8080 -p 9990:9990 -it <image-name>:<image-version> /opt/jboss/wildfly/bin/standalone.sh -b 0.0.0.0 -bmanagement 0.0.0.0
```
-> If you want to use management mode, use above command and access 9990 port.

### License

Projects are licensed under the GNU Lesser General Public License Version 2.1 license.

### Version History

[HyperFrame OE, WildFly 19.0.0.Final](https://github.com/TmaxSoftOfficial/HyperFrameOE-Wildfly/blob/master/release-image/Dockerfile "dockerfile link") (latest)

### HyperFrameOE Service Level

[HyperFrameOE Service Level](https://github.com/TmaxSoftOfficial/HyperFrameOE-About/blob/master/ServiceLevel.md)
