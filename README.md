[![Build Status](https://github.com/CycloneDX/cyclonedx-maven-plugin/workflows/Maven%20CI/badge.svg)](https://github.com/CycloneDX/cyclonedx-maven-plugin/actions?workflow=Maven+CI)
[![Maven Central](https://maven-badges.herokuapp.com/maven-central/org.cyclonedx/cyclonedx-maven-plugin/badge.svg)](https://maven-badges.herokuapp.com/maven-central/org.cyclonedx/cyclonedx-maven-plugin)
[![License](https://img.shields.io/badge/license-Apache%202.0-brightgreen.svg)][License]
[![Website](https://img.shields.io/badge/https://-cyclonedx.org-blue.svg)](https://cyclonedx.org/)
[![Slack Invite](https://img.shields.io/badge/Slack-Join-blue?logo=slack&labelColor=393939)](https://cyclonedx.org/slack/invite)
[![Group Discussion](https://img.shields.io/badge/discussion-groups.io-blue.svg)](https://groups.io/g/CycloneDX)
[![Twitter](https://img.shields.io/twitter/url/http/shields.io.svg?style=social&label=Follow)](https://twitter.com/CycloneDX_Spec)


CycloneDX Maven Plugin
=========

The CycloneDX Maven plugin creates an aggregate of all dependencies and transitive dependencies of a project 
and creates a valid CycloneDX bill-of-material document from the results. CycloneDX is a lightweight BOM 
specification that is easily created, human readable, and simple to parse. 

Maven Usage
-------------------

```xml
<!-- uses default configuration -->
<plugins>
    <plugin>
        <groupId>org.cyclonedx</groupId>
        <artifactId>cyclonedx-maven-plugin</artifactId>
        <version>2.1.0</version>
    </plugin>
</plugins>
```


Default Values
-------------------
```xml
<plugins>
    <plugin>
        <groupId>org.cyclonedx</groupId>
        <artifactId>cyclonedx-maven-plugin</artifactId>
        <version>2.1.0</version>
        <executions>
            <execution>
                <phase>verify</phase>
                <goals>
                    <goal>makeAggregateBom</goal>
                </goals>
            </execution>
        </executions>
        <configuration>
            <projectType>library</projectType>
            <schemaVersion>1.2</schemaVersion>
            <includeBomSerialNumber>true</includeBomSerialNumber>
            <includeCompileScope>true</includeCompileScope>
            <includeProvidedScope>true</includeProvidedScope>
            <includeRuntimeScope>true</includeRuntimeScope>
            <includeSystemScope>true</includeSystemScope>
            <includeTestScope>false</includeTestScope>
            <includeLicenseText>false</includeLicenseText>
            <outputFormat>all</outputFormat>
        </configuration>
    </plugin>
</plugins>
```

Notes
-------------------
As of v2.0.0, the default CycloneDX BOM format is v1.2 and will produce both XML and JSON. 

Goals
-------------------
The CycloneDX Maven plugin contains the following two goals:
* makeBom
* makeAggregateBom

By default, the BOM(s) will be attached as an additional artifacts during a Maven install or deploy.

* `${project.artifactId}-${project.version}-cyclonedx.xml`
* `${project.artifactId}-${project.version}-cyclonedx.json`

This may be switched off by setting `cyclonedx.skipAttach` to true.

makeBom and makeAggregateBom can optionally be skipped completely by setting `cyclonedx.skip` to true.

## CycloneDX Schema Support

The following table provides information on the version of this node module, the CycloneDX schema version supported, 
as well as the output format options. Use the latest possible version of this node module that is the compatible with 
the CycloneDX version supported by the target system.

| Version | Schema Version | Format(s) |
| ------- | ----------------- | --------- |
| 2.0.x | CycloneDX v1.2 | XML/JSON |
| 1.4.x | CycloneDX v1.1 | XML |
| 1.0x | CycloneDX v1.0 | XML |

Copyright & License
-------------------

CycloneDX Maven Plugin is Copyright (c) Steve Springett. All Rights Reserved.

Permission to modify and redistribute is granted under the terms of the Apache 2.0 license. See the [LICENSE] file for the full license.

[License]: https://github.com/CycloneDX/cyclonedx-maven-plugin/blob/master/LICENSE
