---
layout: post
title:  "Windows10에서 GitHub 블로그 만들기"
date:   2022-01-02
categories: Github
tags: Github
image: /assets/article_images/2022-01-02-create-github-blog/title.png
---

기록의 중요성을 뼈저리게 느껴 블로그를 시작하게 됐어요.

티스토리, velog, 브런치 등등 많은 플랫폼이 있었지만 `1일 1커밋 운동에 가장 효율적인 것이 무엇일까?`라는 물음에 나온 답은 `깃허브 블로그`였습니다!

예전에 깃허브 블로그 만드는 것을 도전해보려 했다가 너무 어려워보였던 탓에 할 엄두도 내지 못했지만 이제는 아무것도 아니라는 것을 깨달았기에 만들어보려 합니다..허허

혹시나 다음에 제가 다시 또 만드는 불상사가 생길 수 있을 것 같아 최대한 자세히 써보려하니 아직 깃허브 블로그가 없다면 저랑 같이 만들어보시죠 :)

공식문서를 굉장히 좋아하기 때문에 <a href="https://pages.github.com/" target="_blank">GitHub Pages 공식문서</a>를 적극 참조했습니다.

# GitHub Pages Repository 생성 및 설정

***

⭕ 1. Repository 생성
![New 버튼 누르기](./2022-01-02-create-github-blog/1.PNG)

>Repository name을 username.github.io와 같은 형식으로 생성 (공식문서에서 꼭 본인의 username과 동일하게 만들어야 한다고 하니 username을 확인하시고 만드세요!)

![username.github.io Repository 생성](./2022-01-02-create-github-blog/2.PNG)

저의 username은 `newdoin`이기 때문에 `newdoin.github.io`로 repository를 생성했습니다.

⭕ 2. Repository clone
로컬에서 글을 작성하고 커밋/푸시해주기 위해 생성한 repository를 clone 합니다.

![Repository clone 하기](./2022-01-02-create-github-blog/3.PNG)

우측 초록색 Code 버튼을 누르고 HTTPS 주소를 복사해서 git bash에 아래의 명령어를 입력합니다.

```bash
git clone <복사한 HTTPS 주소>
```

명령어 실행이 완료됐다면, 해당 `폴더로 이동` 후 `index.html` 파일을 생성해봅시다!

```
cd <username>.github.io          # 폴더 이동
echo "Hello World" > index.html  # index.html 파일 생성
```

⭕ 3. Commit/Push
변경사항을 저장하기 위해 변경사항들을 `add`하고 `commit` 해준 다음 `push` 해주면 끝! 쉽죠?!???!?!

```
git add .                        # 변경사항 모두 추가
git commit -m "initial commit"   # 변경사항 커밋
git push -u origin main          # 레포지토리에 적용
```

⭕ 4. Test
이제 repository에 가서 제대로 push가 됐는지 확인해보고 username.github.io로 접속해보세요. 아래와 같이 나오면 성공!

![index.html 확인 결과](./2022-01-02-create-github-blog/4.PNG)

# Jekyll Theme 적용하기

***

블로그라고 해서 따라했더니 결과물이 너무 실망스러우셨나요? 사실 저도 실망했습니다..ㅎ

그래도 Jekyll Theme을 적용해주면 손쉽게 가독성 있는 블로그를 만들 수 있으니 아직 포기하지 마시고 따라오세용

⭕ 1. Ruby 설치
Jekyll Theme을 적용했는데 어떻게 바뀌고 있는건지, 내가 올린 포스팅이 잘 올라갔는지 로컬에서 확인하기 위해 jekyll 설치가 필요합니다.

jekyll 설치를 위해선 ruby 명령어를 사용하기 때문에 ruby를 먼저 설치하도록 하죠!

다양한 방법이 있었지만 윈도우10에서는 인스트롤러를 이용해서 설치하는게 가장 편했습니다 :)

[ruby installer](https://rubyinstaller.org/downloads/){:target="_blank"}에서 가장 최신 버전을 받으시면 되는데, 

jekyll이 32bit라서 ruby도 32bit(x86)를 받는게 좋다고 합니다.

ruby 설치는 큰 어려움 없이 나오는 절차대로 설치하면 되기에 더 이상의 설명은 생략할게요.

⭕ 2. Jekyll 설치
ruby 설치가 끝났다면 아래의 명령어로 jekyll을 설치해봅시다!

```
gem install jekyll bundler
```

⭕ 3. Jekyll Theme 적용
Jekyll Theme은 무료부터 유료까지 굉장히 많습니다. 

테마 하나 고르는 데 시간이 엄청 걸리더라구요... 어찌저찌 하나 찾으셨으면, 바로 다운받으시거나 최신 버전을 위해 만든이의 repository로 이동하셔서

다운로드 받으시면 됩니다. (fork 해서 clone해도 무방합니다.)

![테마 다운로드](./2022-01-02-create-github-blog/5.PNG)

다운로드 받으셨다면 안에 있는 파일 모두 본인이 클론한 깃허브 블로그 폴더에 넣으시면 됩니다!

그리고 아래의 명령어를 입력해주세요.

```
bundle install
```

⭕ 3. Jekyll 로컬에서 실행하기
테마를 잘 가져왔는지 아래의 명령어로 로컬에서 확인해봅시다!

```
bundle exec jekyll serve
```

![로컬에서 확인](./2022-01-02-create-github-blog/6.PNG)

가져온 테마가 잘 보인다면 성공!

>❌ cannot load such file -- webrick <br>
>이런 에러가 발생하신 분들도 계실텐데요..예 접니다. 다행스럽게도 쉽게 해결이 가능했습니다!

```
bundle add webrick
```

이렇게 webrick을 add 해주면 끝 :)

# GitHub Blog 관리하기

***

이제 로컬에서 확인할 수 있으니 포스팅을 하거나 꾸몄을 때 serve 명령어로 미리 확인해보고 원하는대로 잘 됐다면 commit/push 해주면 됩니다.

명령어는 아까와 동일해요.

```
git add .                        # 변경사항 모두 추가
git commit -m "initial commit"   # 변경사항 커밋
git push -u origin main          # 레포지토리에 적용
```

그럼 모두 고생하셨습니다 :)