---
layout: post
title:  Halyard 설치하기
description: installation Halyard
categories: troubleshooting
tag: [Spinnaker, Halyard]
author: atom
---
* content
{:toc}

## Spinnaker 관리도구 Halard 설치하기

Spinnaker를 프로덕션 환경에서 설치하려면 Spinnaker를 관리하는 Halyard라는 도구를 설치해야 한다. 설치는 Linux와 Mac을 지원한다.

### Pre Requirement

* Java >= 8

### 설치 스크립트 다운받기

#### Mac용 스크립트

``` bash
Junseokui-MacBook-Pro:spinnaker junseokoh$ curl -O https://raw.githubusercontent.com/spinnaker/halyard/master/install/macos/InstallHalyard.sh
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  4559  100  4559    0     0   5338      0 --:--:-- --:--:-- --:--:--  5332
```

#### Linux용 스크립트

``` bash
curl -O https://raw.githubusercontent.com/spinnaker/halyard/master/install/debian/InstallHalyard.sh
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 10637  100 10637    0     0  25028      0 --:--:-- --:--:-- --:--:-- 25028
```

### 스크립트로 설치

``` bash
chmod +x InstallHalyard.sh
sudo bash InstallHalyard.sh
```
![]({{ "/assets/images/2019-09-28-Halyard_install/halyard_install_ubuntu.gif" | relative_url }})

- 계정 정보를 넣어주면 된다.

## [Trouble shooting for Java install on Mac]({{ "2019/09/28/Java_install_on_mac//#trouble-shooting-for-java-install" | relative_url }})

다운받은 스크립트를 실행할 때 Java 8 이상이 필요하고 설치되어 있지 않다면 `Java >=8 not yet installed - please install java >=8.` 오류가 발생한다. 이를 위해서는 Java를 설치해야한다.
다만 brew install java 로 설치하게 되면 openJDK13 버젼이 설치되어진다. 스크립트에 보면 java 13버젼은 지원하지 않는다.

```sh

function install_java() {
  set +e
  local java_version=$(java -version 2>&1 head -1)
  set -e

  if [[ "$java_version" == *"1.8"* ]] || \
     [[ "$java_version" == *"9.0"* ]] || \
     [[ "$java_version" == *"10.0"* ]] || \
     [[ "$java_version" == *"11"* ]] || \
     [[ "$java_version" == *"12"* ]] || \
     [[ "$java_version" == "java version \"10\""* ]]; then
    echo "Java is already installed & at the right version"
    return 0;
  fi
```

