---
layout: post
title: Mac 에서 Java 설치하기
subtitle: Java Home
categories: troubleshooting
tags: [java, mac]
author: atom
---

* content
{:toc}

## 1. Homebrew를 이용하여 Java 설치하기

### 1.1 최신 Java를 설치하기

* 현재 기준으로는 jdk13 버젼이 설치된다.

```shell
Junseokui-MacBook-Pro:spinnaker junseokoh$ brew cask reinstall java
==> Satisfying dependencies
==> Downloading https://download.java.net/java/GA/jdk13/5b8a42f3905b406298b72d750b6919f6/33/GPL/openjdk-13_osx-
Already downloaded: /Users/junseokoh/Library/Caches/Homebrew/downloads/c2f9a23dff44fa35b8605ddc5815f27b1598591a7bc5b27e1308ae93846f290e--openjdk-13_osx-x64_bin.tar.gz
==> Verifying SHA-256 checksum for Cask 'java'.
==> Uninstalling Cask java
==> Removing directories if empty:
/Library/Java/JavaVirtualMachines
Password:
==> Purging files for version 13,33:5b8a42f3905b406298b72d750b6919f6 of Cask java
==> Installing Cask java
==> Moving Generic Artifact 'jdk-13.jdk' to '/Library/Java/JavaVirtualMachines/openjdk-13.jdk'.
🍺  java was successfully installed!
```

### 1.2 특정 버젼의 Java를 설치하기

* 일단 adoptoenjdk 에서 패키지를 받을 수 있도록 수정해주고 어떤 버젼을 받을 수 있는지 검색한다.
* 여기 아래에서는 이미 설치되어 있어서 reinstall 명령어를 쳤지만 처음할때는 install로 변경 후 작업하면 된다.

```shell
Junseokui-MacBook-Pro:spinnaker junseokoh$ brew tap AdoptOpenJDK/openjdk
Ignoring commonmarker-0.17.13 because its extensions are not built.  Try: gem pristine commonmarker --version 0.17.13
Ignoring commonmarker-0.17.13 because its extensions are not built.  Try: gem pristine commonmarker --version 0.17.13
Updating Homebrew...
==> Auto-updated Homebrew!
Updated 1 tap (homebrew/cask).
No changes to formulae.

Junseokui-MacBook-Pro:spinnaker junseokoh$ brew search jdk
==> Casks
adoptopenjdk                         adoptopenjdk12                       adoptopenjdk8-openj9
adoptopenjdk10                       adoptopenjdk12-jre                   adoptopenjdk8-openj9-jre
adoptopenjdk11                       adoptopenjdk12-openj9                adoptopenjdk8-openj9-jre-large
adoptopenjdk11-jre                   adoptopenjdk12-openj9-jre            adoptopenjdk8-openj9-large
adoptopenjdk11-openj9                adoptopenjdk12-openj9-jre-large      adoptopenjdk9
adoptopenjdk11-openj9-jre            adoptopenjdk12-openj9-large          oracle-jdk
adoptopenjdk11-openj9-jre-large      adoptopenjdk8 ✔                      oracle-jdk-javadoc
adoptopenjdk11-openj9-large          adoptopenjdk8-jre                    sapmachine-jdk
```

* 여기서 검색된 버젼의 jdk를 설치해준다.

```shell
Junseokui-MacBook-Pro:spinnaker junseokoh$ brew cask reinstall adoptopenjdk8
==> Satisfying dependencies
==> Downloading https://github.com/AdoptOpenJDK/openjdk8-binaries/releases/download/jdk8u222-b10/OpenJDK8U-jdk_
Already downloaded: /Users/junseokoh/Library/Caches/Homebrew/downloads/6d931a656709dc41c28192764ea33a6018257ffb420f3606d42e7d845824e31a--OpenJDK8U-jdk_x64_mac_hotspot_8u222b10.pkg
==> Verifying SHA-256 checksum for Cask 'adoptopenjdk8'.
==> Uninstalling Cask adoptopenjdk8
==> Uninstalling packages:
net.adoptopenjdk.8.jdk
Password:
==> Purging files for version 8,222:b10 of Cask adoptopenjdk8
==> Installing Cask adoptopenjdk8
==> Running installer for adoptopenjdk8; your password may be necessary.
==> Package installers may write to any location; options such as --appdir are ignored.
installer: Package name is AdoptOpenJDK
installer: Installing at base path /
installer: The install was successful.
🍺  adoptopenjdk8 was successfully installed!
```

## 2. 다른 버젼 삭제하기

* 만약 다른 Java version이 필요없어지면 아래 위치에 가서 삭제하면 된다.
```/Library/Java/JavaVirtualMachines/{JavaVersion}.jdk```

## 3. version 확인하기

```shell
Junseokui-MacBook-Pro:spinnaker junseokoh$ java -version
openjdk version "1.8.0_222"
OpenJDK Runtime Environment (AdoptOpenJDK)(build 1.8.0_222-b10)
OpenJDK 64-Bit Server VM (AdoptOpenJDK)(build 25.222-b10, mixed mode)
```
