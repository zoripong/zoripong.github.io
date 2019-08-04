---
layout: post
title: Jekyll과 Github Pages를 이용한 간단한 블로그 제작기
tags:
  - tech
---

안녕하세요. Yool입니다. 

블로그의 첫 게시물로 블로그를 준비하는데 사용한 Jekyll과 Github Pages에 대해 다루어 보려고 합니다.

## 시작하며

블로그를 시작하기에 앞서 어떠한 채널을 통해 포스팅을 공유할지 고민이 많았습니다.

Brunch, Tistory, Github Pages 등 블로그를 시작할 수 있는 서비스가 많았지만, 마크다운을 통한 게시물 작성과 zoripong.[github.io](http://github.io) 라는 도메인의 매력에 Github Pages + Jekyll을 이용하여 블로그를 시작하게 되었습니다.

### 마크다운?

특수 기호와 문자를 이용한 간단한 구조의 문법을 통해 컨텐츠를 작성할 수 있는 텍스트 기반의 마크업 언어

### Github Pages?

Github 저장소의 내용을 웹페이지로 만들어 주는 서비스로 `[username.github.io](http://username.github.io)` 도메인을 통하여 컨텐츠에 접근이 가능합니다.

## 1. Jekyll 테마 선택

테마란 누군가 Jekyll 프로젝트를 이용하여 스타일을 적용 해놓은 것입니다. [해당 페이지](http://jekyllthemes.org/)에서 다양한 Jekyll 테마를 확인 할 수 있습니다.

시작할 때에는 무작정 jekyll 프로젝트를 설치 후 테마를 설정하려고 하였지만 마음에 드는 테마를 Fork 해온 후 적용시키는 것이 더 빠를 것 같다는 판단에 방향을 바꾸게 되었습니다.

저는 기존 [Kiko](https://github.com/microdotblog/theme-kiko) 테마를 발전 시킨 [Kiko-now](https://github.com/aweekj/kiko-now)를 이용하려고 합니다.

![github에서 프로젝트 fork하기]({{ site.baseurl }}/images/2019-8-5/1-fork-project.png)

테마를 선택 하였다면 Github Repository의 우측에 위치하는 Fork 버튼을 이용하여 원하는 계정으로 프로젝트를 Fork합니다. 저는 `zoripong` 계정에 Fork하였습니다.

![github에서 프로젝트 이름 변경하기]({{ site.baseurl }}/images/2019-8-5/2-rename-with-github.png)



이제 Fork 한 Repository로 이동하여 Repo 이름을 `username.github.io`로 변경해줍니다. 저의 경우 zoripong.github.io로 변경해주었습니다.

## 2. 프로젝트 구조 파악하기

프로젝트를 Customize 하기 전 알고 있으면 도움이 되는 프로젝트 구조에 대해 알아가는 시간입니다. 빠른 시작을 원하시는 분은 이 단계를 건너 뛰어도 무관합니다. 해당 파일 및 디렉토리는 [Kiko-now](https://github.com/aweekj/kiko-now)를 기준으로 하고 있습니다.

### [.gitignore](https://git-scm.com/docs/gitignore)

git의 버전관리에 제외할 파일 목록을 지정하는 파일입니다. 업로드를 원치 않는 파일을 해당 파일에 추가하면 해당 파일은 버전관리 대상에서 제외됩니다.

### 404.md

[http status code](https://ko.wikipedia.org/wiki/HTTP_404)가 404일 경우 해당 페이지를 보여주는 페이지입니다. 즉 사용자가 존재하지 않는 페이지를 찾을 때 보여지는 페이지입니다.

### _config.yml

Jekyll 프로젝트에 대한 설정 파일입니다. 해당 파일을 통해 페이지의 제목이나 설명과 같은 정보를 수정할 수 있으며 또한 plugin을 추가할 수도 있습니다. 

### _posts

포스팅 할 컨텐츠들이 위치할 디렉토리 입니다. 글을 작성하기 위해서는 해당 디렉토리 아래에 파일을 만들게 됩니다. `_posts`에 저장되는 파일들은 `YYYY-MM-DD-name-of-post.ext` 형태로 저장되는 것이 컨벤션 입니다.

### images

이미지 파일을 저장하는 디렉토리 입니다.

## 3.  로컬에 세팅하기

여러가지 작업을 한번에 진행하기 위해 로컬에 설치 후 작업하였습니다.

빠르게 진행하고 싶으신 분은 브라우저에서 직접 파일들을 수정하여 진행해도 무관합니다. 실제로 설치하지 않고 브라우저만을 이용해서도 충분히 블로그 운영이 가능합니다.

### 1) 로컬에 Repository 내려받기

    $ cd project-path
    $ git clone git@github.com:zoripong/zoripong.github.io.git

fork한 프로젝트를 로컬로 내려 받습니다.

### 2) Jekyll 설치하기

    $ gem install jekyll

Mac OS에는 Ruby가 이미 설치 되어있기 때문에 `gem` 명령어를 바로 이용할 수 있습니다. 

    $ gem install jekyll
    ERROR:  While executing gem ... (Gem::FilePermissionError)
    	You don't have write permissions for the /Library/Ruby/Gems/2.3.0 directory.
    $ sudo gem install jekyll 

만약 위와 같이 Permission과 관련된 문제가 생길 경우 `sudo` 명령어를 통해 root 권한을 준 후 설치가 가능합니다.

    $ cd zoripong.github.io
    $ jekyll serve

위 커맨드들을 모두 수행 했다면 이제 생성된 프로젝트를 로컬에서 4000번 포트를 통해 확인할 수 있습니다. 

브라우저에서 `localhost:4000`을 접속하여 우리의 블로그가 될 사이트를 확인할 수 있습니다.

## 4. Customizing

### 1) _config.yml 수정하기

![Customizing한 블로그 상단]({{ site.baseurl }}/images/2019-8-5/3-customizing-navigator.png)

    # Name of your site (displayed in the header)
    name: Yool's
    
    # Short bio or description (displayed in the header)
    description: 게으름을 벗어나기 위한 블로그
    
    # URL of your avatar or profile pic (you could use your GitHub profile pic)
    avatar: https://avatars2.githubusercontent.com/u/26541456

사이트의 상단에 위치하는 이름과 설명, 사진에 대한 설정입니다.

`name`과 `description`에 블로그 이름과 설명을 기입하고, 사이트의 상단에 위치를 설정하는 `avatar` 는 일단 github profile로 설정하였습니다.

    navigation:
      - name: Blog
        url: /
      - name: About
        url: /about
      - name: Archive
        url: /archive
      - name: Tags
        url: /tags

사이트 우측 상단에 위치하는 네비게이션에 대한 설정입니다. 저는 기존에 존재했던 `Theme` 탭에 대한 설정은 삭제하고 위 4가지의 탭만 남겨 두었습니다.

![Customizing한 블로그 하단]({{ site.baseurl }}/images/2019-8-5/4-customizing-footer.png)


    footer-links:
      behance: # https://www.behance.net/<username>
      dribbble:
      email: devuri404@gmail.com
      facebook:
      flickr:
      github: zoripong/zoripong.github.io
      googleplus: # anything in your profile username that comes after plus.google.com/
      instagram: https://www.instagram.com/y.oo.l/
      linkedin:
      pinterest:
      rss: # just type anything here for a working RSS icon
      stackoverflow: # your stackoverflow profile, e.g. "users/50476/bart-kiers"
      tumblr: # https://<username>.tumblr.com
      twitter:
      youtube: # channel/<your_long_string> or user/<user-name>

이 부분은 Facebook, github 등 다른 사이트에 링크를 설정할 수 있는 부분입니다. 저는 위와 같이 수정하였습니다.

    # Text under the icons in footer
    footer-text: © 2019 yool's

마지막으로 링크 아래에 적을 텍스트를 지정할 수 있습니다. *이 부분에 대해서 수정을 해도 괜찮을지 걱정이 되긴 하였지만 일단 바꾸어 보았습니다.*

### 2) 필요없는 파일 삭제하기

- _posts
    - 해당 디렉토리에 존재하는 모든 하위 파일들을 삭제하였습니다.
- images
    - 404.jpg를 제외한 모든 이미지 파일을 삭제하였습니다.
- README.md

### 3) [about.md](http://about.md) 수정하기

![About.md 파일이 보여주는 화면]({{ site.baseurl }}/images/2019-8-5/5-about-md.png)


네비게이션의 두 번째 탭인 About을 누르면 보이는 페이지에 대한 파일입니다. 

    ---
    layout: page
    title: About
    permalink: /about/
    ---
    # 기술블로그를 시작하며.
    
    안녕하세요. 풀 스택 프로그래머 Yool입니다.
    
    개인적으로 공부한 기술적 지식이나 경험들을 기록하고 공유하기 위해 블로그를 시작하게 되었습니다.
    
    모든 블로그 포스팅에 대한 피드백과 아젠다는 언제나 환영합니다. 🙏
    
    ## Contact me
    
    [devuri404@gmail.com](mailto:devuri404@gmail.com)

저는 위와 같이 파일을 수정하였습니다.

### 4) 위 변경 사항 반영하기

위 작업을 모두 끝냈다면, 이제 github의 master branch에 적용하면 됩니다.

브라우저를 통해서 진행하신 분들은 단순히 변경사항을 저장(commit)만 하면 되고, 로컬에서 진행하신 분들은 커밋을 한 후 원격 저장소에 Push만 하면 자동으로 배포까지 완료됩니다.

## 5. 호스팅 된 페이지 확인하기

![호스팅 된 페이지 (zoripong.github.io)]({{ site.baseurl }}/images/2019-8-5/6-hosting.png)


이제 `[your-github-user-name.github.io](http://your-github-user-name.github.io)`에 접속하면 여러분의 블로그를 볼 수 있게 됩니다. `_posts`에 있는 파일들을 전부 삭제하여 텅 빈 느낌이 있지만 글을 쓸 수록 채워지게 되겠죠.

## 마치며

Tistory, Brunch 등 다른 블로그 서비스에 비하면 직접 세팅 해주어야 한다는 단점이 있지만, 반대로 생각하면 그만큼 자유롭게 Cutomizing 할 수 있다는 장점이 되는 것 같습니다. 뿐만 아니라 마크다운을 통한 게시글 작성은 글을 작성하는데 쓰이는 시간과 부담을 줄여주는 것 같습니다.

첫 기술 블로그라 필요한 내용이 누락되거나, 잘못된 내용이 기입될 수 있습니다. 여러분의 피드백을 환영합니다! 🙌