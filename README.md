# CSB-SDK README

## [README of 中文](https://github.com/aliyun/csb-sdk/blob/master/README_cn.md)

## Introduction

The CSB-SDK is a client-side invocation SDK for HTTP or Web Service API opened by the CSB (Cloud Service Bus) product. It is responsible for invoking the open API and signing the request information.

## Content in the CSB-SDK
* common       Base classes used by both HTTP-SDK and WS-SDK
* http-client  The client SDK for invoking HTTP API  [details](http-client/README.md)
* ws-client    The client SDK for binding security params into WebService client dispatch or port [details](ws-client/README.md)
* samples      Unit Tests for using above SDKs [details](samples/README.md)
* others       HTTP-SDK for other Languages' implementation, e.g. PHP, Go and Node.js

## Build from source code


```
# 1. download sourcefrom Github (once time only)
git clone https://github.com/aliyun/csb-sdk.git
cd csb-sdk
     

# 2. show and switch to desired branch, e.g.
git branch
git checkout 1.1.5.

# 3. Build common module
cd common
mvn clean install 

# 4. Build http SDK
cd ../http-client

# 4.1 install as maven dependency to local repository
mvn clean install  -Dmaven.test.skip

# 4.2 build as a standalone jar
bash gen-standaloneJar.sh

# 5. Build WS SDK
cd ../ws-client

# 5.1 install as maven dependency to local repository
mvn clean install  -Dmaven.test.skip

# 5.2 build as a standalone jar
bash gen-standaloneJar.sh

```

# Use the SDK as dependency in your pom.xml
1. Directly use the maven dependency from maven central repository. Use release dependency in your pom.xml

```
  <!--To use HTTP-SDK-->
  <dependency>
     <groupId>com.alibaba.csb.sdk</groupId>
     <artifactId>http-client</artifactId>
     <version>${http.sdk.version}</version>
  </dependency>

  <!--To use WS-SDK-->
  <dependency>
     <groupId>com.alibaba.csb.sdk</groupId>
     <artifactId>ws-client</artifactId>
     <version>${ws.sdk.version}</version>
  </dependency>
```

Note: Please check latest release version from [here](release.md)

2. Use snapshot dependency in your pom.xml

```
  <!--To use HTTP-SDK-->
  <dependency>
     <groupId>com.alibaba.csb.sdk</groupId>
     <artifactId>http-client</artifactId>
     <version>${http.sdk.snapshot.version}</version>
  </dependency>

  <!--To use WS-SDK-->
  <dependency>
     <groupId>com.alibaba.csb.sdk</groupId>
     <artifactId>ws-client</artifactId>
     <version>${ws.sdk.snapshot.version}</version>
  </dependency>
     
     
  <repositories>
    ...
      
    <!--define snapshot repository for SDK releases-->   
    <repository>
      <id>csb-sdk-snapshots</id>
      <url>https://oss.sonatype.org/content/repositories/snapshots/</url>
      <releases>
        <enabled>false</enabled>
      </releases>
      <snapshots>
        <enabled>true</enabled>
      </snapshots>
    </repository>
  </repositories>
```

Note: Please check latest snapshot version from [here](release.md)

* Release Notes
  [change history](release.md)

## Other-Languages support (beta version!!!)
1. PHP based HTTP-SDK
A http-sdk implementation by PHP script [details](others/php/README.md)

2. Go  based HTTP-SDK
A http-sdk implementation by Go script [details](others/golang/README.md)

3. node.js based HTTP-SDK
A http-sdk implementation by Node.js [details](others/node.js/README.md)

4. .net based HTTP-SDK
A http-sdk implementation by .net [details](CSharp/README.md)

## Future Work

- Support more Aliyun base service
- Support more friendly code migration.

## License

Licensed under the [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0.html)
