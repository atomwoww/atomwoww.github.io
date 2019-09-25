---
layout: post
title:  Chrome Browser Bookmark location
description: installation go
categories: troubleshooting
tag: [chrome, bookmark]
author: atom
---
* content
{:toc}

## Chrome browser

windows, ubuntu, mac os 공통으로 가장 많이 사랑하는 Web Browser는 아마 Chrome이 아닐까 싶습니다.  
Internet Explorer가 Active X 등으로 엉망이되고 사람들이 떠나가고 Chrome Browser로 옮겼고 Internet Explorer에서 자동으로 Bookmark migration이 손쉽게 되었습니다.  
다만 저는 이 북마크들을 다른 사람과 공유하고 싶었습니다. 그러기 위해서는 Chrome Browser가 강력하게 제공하는 멀티 디바이스 동기화로는 해결이 되지 않고 직접 북마크 파일을 옮겨야 했습니다.  
Internet Explorer에서는 Bookmark가 별도의 폴더로 빠져있어서 그 폴더만 복사하면 되었는데 Chrome은 어찌된건지 꽁꽁 숨겨두어서 이를 해결해야 했고 그 방법에 대해 다루겠습니다.  

## Bookmark 위치 찾기

### mac os

Mac 에서는 더더욱 숨겨져있다 일단 아래를 참고하면 된다.  
>[https://canopyit.com/google-chrome-bookmarks-file-location-mac/](https://canopyit.com/google-chrome-bookmarks-file-location-mac/)  

1. Terminal에서 아래와 같이 숨겨진 파일을 찾을 수 있도록 변경한다.

    ``` bash
    “chflags nohidden ~/Library”
    ```

2. 이제 Bookmark가 숨겨진 폴더로 이동합니다.

    ``` bash
    cd ~/Library/Application Support/Google/Chrome/Default
    ```

### windows 10

1. windows 탐색기에서 숨김파일을 볼 수 있게 수정합니다.
![windows hidden file]({{"assets/images/2019-09-25-chromeBookmark/hiddenfile.PNG" | relative_url }})

2. 아래 파일경로로 이동합니다.

``` windows
c:\users\{userid}\AppData\Local\Google\Chrome\User Data\Default
```

## Bookmark 복사 및 수정

* 이제 해당 위치에서 북마크 백업 파일을 복사해줍니다. 북마크 파일은 `Bookmarks.bak` 입니다.

* 백업한 파일을 공유하면 되고 이때 북마크 파일은 json format 이기에 적당히 수정하여 각 사용자에게 복사하면 됩니다.

예시

``` json
{
   "checksum": "7d0f878121d551df134ee65c46ef5b9a",
   "roots": {
      "bookmark_bar": {
         "children": [ {
            "date_added": "13211876370502151",
            "id": "5",
            "name": "Docker log driver – fluentd 사용 구성 | a day in the life",
            "type": "url",
            "url": "https://bltin.wordpress.com/2018/06/18/docker-log-driver-fluentd-test/"
         } ],
         "date_added": "13211859240093017",
         "date_modified": "13211876370502151",
         "id": "1",
         "name": "북마크바",
         "type": "folder"
      },
      "other": {
         "children": [  ],
         "date_added": "13211859240093034",
         "date_modified": "0",
         "id": "2",
         "name": "기타 북마크",
         "type": "folder"
      },
      "synced": {
         "children": [  ],
         "date_added": "13211859240093037",
         "date_modified": "0",
         "id": "3",
         "name": "모바일 북마크",
         "type": "folder"
      }
   },
   "version": 1
```
