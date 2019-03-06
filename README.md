# CommunityStarter

This Maven project is a Spring boot implementation of a community [Broadleaf Commerce](http://www.broadleafcommerce.org) application. It has many sensible defaults set up along with examples of how a fully functioning eCommerce site based on Broadleaf might work.

## Project Overview

The Community Demo is comprised of 4 individual projects:

```shell
~/CommunityDemo » tree -L 1
├── LICENSE
├── README.md
├── admin
├── api
├── core
├── pom.xml
└── site
```

- `admin` - a Spring Boot application for the Broadleaf admin for catalog management, see completed orders, etc
- `api` - a Spring Boot application that sets up the Broadleaf API endpoints
- `site` - a Spring Boot application that runs the Heat Clinic UI built with Thymeleaf as tradiitional MVC
- `core` a common jar that all other projects depend on, used for common functionality like domain

## Prerequisits:

 - Centos/RHEL 7
 - git
 - java 8
 - maven

### Steps:

**1. Install required packages:**
```
yum -y update && yum install -y epel-release git java-1.8.0-openjdk-devel.x86_64 wget unzip
```

**2. Install maven:**
 ```
cd /usr/local/src

wget http://apache.ip-connect.vn.ua/maven/maven-3/3.6.0/binaries/apache-maven-3.6.0-bin.tar.gz
tar -xf apache-maven-3.6.0-bin.tar.gz
mv apache-maven-3.6.0/ apache-maven/

cat <<EOF > /etc/profile.d/maven.sh
# Apache Maven Environment Variables
# MAVEN_HOME for Maven 1 - M2_HOME for Maven 2
export M2_HOME=/usr/local/src/apache-maven
export PATH=/usr/local/src/apache-maven/bin:${PATH}
EOF
source /etc/profile.d/maven.sh
```

## Running the projects

You must first do a `mvn package` or `mvn install` from the root to build all of the projects:

```shell
~/CommunityDemo » mvn clean install
```

After this completes you can run either `site`, `api` or `admin` by using the Spring Boot Maven plugin with `mvn spring-boot:run`. Example:

```shell
~/CommunityDemo » cd site
~/CommunityDemo/site » mvn spring-boot:run
Java HotSpot(TM) 64-Bit Server VM warning: ignoring option MaxPermSize=512m; support was removed in 8.0
[INFO] Scanning for projects...
[INFO]
[INFO] ------------------------------------------------------------------------
[INFO] Building Community Demo Site 1.0.0-SNAPSHOT
[INFO] ------------------------------------------------------------------------
[INFO]
[INFO] >>> spring-boot-maven-plugin:1.5.4.RELEASE:run (default-cli) > test-compile @ boot-community-demo-site >>>
[INFO]
[INFO] --- maven-resources-plugin:2.6:resources (default-resources) @ boot-community-demo-site ---
[INFO] Using 'UTF-8' encoding to copy filtered resources.
[INFO] Copying 0 resource
[INFO] Copying 128 resources
[INFO]
[INFO] --- jrebel-maven-plugin:1.1.7:generate (generate-rebel-xml) @ boot-community-demo-site ---
[INFO]
[INFO] --- maven-compiler-plugin:3.1:compile (default-compile) @ boot-community-demo-site ---
[INFO] Nothing to compile - all classes are up to date
[INFO]
[INFO] --- maven-dependency-plugin:2.10:copy (copy-agent) @ boot-community-demo-site ---
[INFO] Configured Artifact: org.springframework:spring-instrument:4.3.9.RELEASE:jar
[INFO] org.springframework:spring-instrument:4.3.9.RELEASE:jar already exists in /Users/phillip/broadleaf/5.2/CommunityDemo/site/target/agents
[INFO]
[INFO] --- maven-resources-plugin:2.6:testResources (default-testResources) @ boot-community-demo-site ---
[INFO] Using 'UTF-8' encoding to copy filtered resources.
[INFO] skip non existing resourceDirectory /Users/phillip/broadleaf/5.2/CommunityDemo/site/src/test/resources
[INFO]
[INFO] --- maven-compiler-plugin:3.1:testCompile (default-testCompile) @ boot-community-demo-site ---
[INFO] No sources to compile
[INFO]
[INFO] <<< spring-boot-maven-plugin:1.5.4.RELEASE:run (default-cli) < test-compile @ boot-community-demo-site <<<
[INFO]
[INFO]
[INFO] --- spring-boot-maven-plugin:1.5.4.RELEASE:run (default-cli) @ boot-community-demo-site ---
[INFO] Attaching agents: [/Users/phillip/broadleaf/5.2/CommunityDemo/site/target/agents/spring-instrument.jar]
objc[3168]: Class JavaLaunchHelper is implemented in both /Library/Java/JavaVirtualMachines/jdk1.8.0_73.jdk/Contents/Home/jre/bin/java (0x10c6444c0) and /Library/Java/JavaVirtualMachines/jdk1.8.0_73.jdk/Contents/Home/jre/lib/libinstrument.dylib (0x10c7574e0). One of the two will be used. Which one is undefined.
Listening for transport dt_socket at address: 8000

 ,,                                       ,,    ,,                       ,...
*MM                                     `7MM  `7MM                     .d' ""
 MM                                       MM    MM                     dM`
 MM,dMMb.`7Mb,od8 ,pW"Wq.   ,6"Yb.   ,M""bMM    MM  .gP"Ya   ,6"Yb.   mMMmm
 MM    `Mb MM' "'6W'   `Wb 8)   MM ,AP    MM    MM ,M'   Yb 8)   MM    MM
 MM     M8 MM    8M     M8  ,pm9MM 8MI    MM    MM 8M""""""  ,pm9MM    MM
 MM.   ,M9 MM    YA.   ,A9 8M   MM `Mb    MM    MM YM.    , 8M   MM    MM
 P^YbmdP'.JMML.   `Ybmd9'  `Moo9^Yo.`Wbmd"MML..JMML.`Mbmmd' `Moo9^Yo..JMML.
 --------------------------------------------------- C O M M E R C E ------

2017-07-10 07:46:28.786  INFO 3168 --- [           main] com.community.SiteApplication            : Starting SiteApplication on macbook.local with PID 3168 (/Users/osxuser/CommunityDemo/site/target/classes started by osxuser in /Users/osxuser/broadleaf/5.2/CommunityDemo/site)
2017-07-10 07:46:28.790  INFO 3168 --- [           main] com.community.SiteApplication            : No active profile set, falling back to default profiles: default

...
...
2017-07-10 07:49:13.052  INFO 3212 --- [eduler_Worker-1] o.h.cache.internal.StandardQueryCache    : HHH000248: Starting query cache at region: query.Search
2017-07-10 07:49:13.181  INFO 3212 --- [           main] c.c.c.s.s.SolrIndexCleanupServiceImpl    : Not rebuilding indexes because value was update
2017-07-10 07:49:13.479  INFO 3212 --- [           main] s.b.c.e.t.TomcatEmbeddedServletContainer : Tomcat started on port(s): 8443 (https) 8080 (http)
2017-07-10 07:49:13.493  INFO 3212 --- [           main] com.community.SiteApplication            : Started SiteApplication in 32.617 seconds (JVM running for 33.017)

```

If you have a JRebel license you can use the `jrebel` profile to start with the Jrebel agent, using a `jrebel.agent.args` property. Example on OSX:

```shell
mvn spring-boot:run -Pjrebel -Djrebel.agent.args='-agentpath:/full/path/to/jrebel/lib/libjrebel64.dylib'
```

We recommend moving the `jrebel.agent.args` property into your global `~/.m2/settings.xml` file so that you can just start the application with:

```shell
mvn spring-boot:run -Pjrebel
```

For more information on which agent to use for your operating system, [consult the Jrebel documentation](https://manuals.zeroturnaround.com/jrebel/standalone/springboot.html#springboot).

### Active Ports

Each project by default starts up with different remote debug ports and HTTP/HTTPS connector ports:

- `site`
  - base url: https://localhost:8081
  - http - `8080`
  - https - `8081`
  - remote debug port - `8000`
- `admin`
  - base url: https://localhost:8083/admin
  - http - `8082`
  - https - `8083`
  -  - `8001`
- `api`
  - base url: https://localhost:8085/api
  - http - `8084`
  - https - `8085`
  - remote debug port - `8002`

## Add unit test

To be able to run unit test via `mvn test` command, please create file `./core/src/test/java/testpackage/SampleTest.java` and add next content to it:
```
package testpackage;

import org.junit.Test;

import static org.junit.Assert.assertTrue;

public class SampleTest {

    @Test
    public void testSomething() {
        assertTrue(1 == 1);
    }
}
```

Add `junit 4.12` dependency to the module dependencies

## Deploy to Artifactory

To deploy build artifacts through Artifactory you need to add a deployment element with the URL of a target local repository to which you want to deploy your artifacts. Please, use next next configuration example:
```
<distributionManagement>
    <snapshotRepository>
        <id>snapshots</id>
        <name>e6f37d2755ed-snapshots</name>
        <url>http://83.170.112.143:80/artifactory/libs-snapshot-local</url>
    </snapshotRepository>
</distributionManagement>
```
Distribution management acts precisely as it sounds: it manages the distribution of the artifact and supporting files generated throughout the build process.

### Repository

Where as the repositories element specifies in the POM the location and manner in which Maven may download remote artifacts for use by the current project, `distributionManagement` specifies where (and how) this project will get to a remote repository when it is deployed. The repository elements will be used for snapshot distribution if the snapshotRepository is not defined.

### Security settings

Please, create new file in `~/.m2/settings-security.xml` location and add next content to it:
```
<settingsSecurity>
  <master>{y6JedC6tibIH60BF1Kd+2ElNkD8YseDsSIcD8HsCCdc=}</master>
</settingsSecurity>
```

This is required to decrypt passwords by `maven`

## License

The Broadleaf Commerce Demo Site is itself licensed under the Broadleaf Fair Use License Agreement - Version 1.0 (http://license.broadleafcommerce.org/fair_use_license-1.0.txt). The Broadleaf Commerce core and module libraries have different license models you should be aware of.

Broadleaf Commerce core libraries, as well as the menu library, are released under a dual license format. They may be used under the terms of the Fair Use License 1.0 (http://license.broadleafcommerce.org/fair_use_license-1.0.txt) unless the restrictions on use therein are violated and require payment to Broadleaf, in which case the Broadleaf End User License Agreement (EULA), Version 1.1 (http://license.broadleafcommerce.org/commercial_license-1.1.txt) shall apply. Alternatively, the Commercial License may be replaced with a mutually agreed upon license between you and Broadleaf Commerce.

Various commercial modules that are also available (for instance, price list management) are released under the applicable commercial license. These are not included with the core Broadleaf framework.
