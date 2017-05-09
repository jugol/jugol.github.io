---
layout: post
title:  "잡쇼퍼 개발 정리"
date:   2016-05-10
excerpt: "어떻게 지금까지 왔나"
jobshopper: true
tag:
- jobshopper
- developing
- logs
comments: true
---


# 왜 이런 포스트를 남기기 시작하는가?

팀 업무 공유차원에서 잔디를 쓰는데 너무 글이 많아질 것 같아서 섣불리 잘 못올리겠다.  
그리고 남들 관심도없는 개발용어 쫘르륵 쓰는거 결국 서로 대화창 지면상 손해일 것 같아서  
혹시나 다른 개발자가 생길 경우를 대비해 틈틈히 남겨놓는 로그 정도의 의미가 있겠다.  

## 그래서 이 포스트의 내용은?

간략하게 개발 스택과, 개발 과정에 대한 정리를 하고자 한다.  
어째서 이런 기술들을 채택했고, (구차한 변명들과..) 그래서 나아가야 할 방향이 무엇인지

그리고 개발을 모르는 다른 팀원들이 웹사이트에 대해 대충 이해하기를 바라기도 하고(...)  

여튼 대충 이렇게 남기고 그러다보면 최소한 이후의 개발자가 따라오는 데에 도움이 되지 않을까!

## 개발 스택 / Back , Server

<figure class="third">
	<img src="https://node-os.com/assets/images/nodejs.png">
	<img src="https://www.cert.gov.py/application/files/4814/8362/5066/mongod.png">
	<img src="https://glynrob.com/wp-content/uploads/redis_logo.png">
    <img src="https://www.pcmag.com/sm/pcmagus/photo/default/sean-golden-google-app-engine-logo_ft3h.jpg">
	<figcaption>오 이렇게 이미지들을 모아서 해 놓으니 그럴듯해보이는군</figcaption>
</figure>

솔직히 짜잘짜잘한 다른 기술들을 더 적기 보다, 큼지막하게 쓰인 기술들을 적기로 마음 먹었다.  
(귀찮아서는 아니고...^^~~~~!)  

우선 **node js / express** 로 백앤드를 구성했다.  
이유는 단순한데
* 이미 돌리고있는 다른 node/express 웹페이지가 있었고, 처음 개발할 당시에 굉장히 급히 프로토 타입을 개발해야 해서 거기서 소스를 많이 복붙해서 가져왔다.
* 내가 겪어본 아는 몇안되는 백앤드 개발 언어. (php , spring , nodejs)
* 그중에 spring은 너무 혼자하기는 개발속도가 안나올 것 같았고 php는 ..ㅎㅎ... 알거라고 생각한다.

백앤드가 정해지고 나니 DB는 자연스럽게 **MONGO DB**를 선택했다. 사실 몇가지 이슈가 있기는 했다.  
그 중에 가장 큰것은 불안정성이었는데, 그건 그냥 업데이트 되면 괜찮아 질 거라고 믿고 쓰기로 했다.  
다음과 같은 장점 때문에 자연스럽게 채택하게 되었는데,  
* Mongoose 와 연계해서 쓰게되면 db 테이블 수정 삭제가 너무 편하다.
* 개발 속도, 편의성이 아주 향상된다.
* 사용자의 로그를 쌓아야 해서 데이터가 많은데, 그 많은 데이터를 처리하기에 좋다고 생각했다.

**redis** 는 사실 세션 때문에 쓰기 시작했는데  
서비스의 특성상 user의 속성을 거의 매 뷰마다 계산하고, 지지고 볶는데  
기존의 mongoose 예제(평범한) 코드로는 세션에 \_id 만을 저장하고 매번 속성은 db에서 불러오게 된다.
이 과정이 보나마나 굉장한 cost가 들 것이기 때문에  
차라리 그러느니 램메모리 DB에 user 세션을 모두 올려놓고, 세션마다 user 모든 정보를 가지고 있게 만들기로 결정했다.  

**Google App Engine** 은 .... 일단 google storage에 이미지 담아놓고 전송하는게 무료이고.  
카드뉴스 형식의 데이터를 많이 주고받는 우리 서비스에 나름 잘 어울린다고 생각했다.  
하지만 내가 결정한게 아니라서 사실 이건 왜 썼다고 말하기가 애매하다. 엉엉엉엉...  
양욱이가 추천해줘서 그냥 썼다 <-ㅋㅋㅋ...자존심이고 뭐고...


## 개발 스택 / Front

<figure class="third">
    <img src="http://d3jx7kyaz22lna.cloudfront.net/wp-content/uploads/2014/12/logo-ejs.jpg">
    <img src="https://site2img-api.herokuapp.com/parse/files/MqX4RIjBpnVgUg9lRrxmWRsDVmqR5SCOaYmnSpnx/2ba43291aa42c2e1e11e268e780a5e96_img.png">
    <img src="https://wikiprogramming.org/wp-content/uploads/2016/10/jquery-icon.png">
	<figcaption>언젠가는 갈아 엎어야지~</figcaption>
</figure>

아. 이야기 했는지 모르겠는데 개발 거의 전부 혼자 했다.  
그래서 시간과 노동력이 아주 부족했기 때문에 **bootstrap** 은 거의 필수였다.  
당연하게도, 따라서 **jquery** 를 자연스럽게 쓸 수 밖에 없었다.  
약-간 의아한 부분은 **ejs** 라고 할 수 있는데 몇가지 장단점이 분명히 있다.  
**단점** 으로는
* 서버사이드 렌더링이라 CPU를 잡아먹는건 사실이다.
* Angular4와 비교해서 하이브리드 웹앱으로 확장하기가 비교적 까다롭다.  

**장점** 은
* 개중에는 그래도 제일 빠르고
* HTML자체에서 수정해서 쓰기가 제일 편하다.

하지만 시간이 된다면 Angular로 다시 처음부터 갈아엎고 싶다.  
개인적인 욕심이기도 하고, 웹앱 편하게 만들고 싶다.

## License

유료 서비스라 아마 소스 전부가 공개되지 않을 것 같다.

{% highlight yaml %}
프로그래밍~ 재미있다.
오늘 아침에는 이걸 쓰다가 시간이 다 가버렸군~
Angular 공부 또한 조금 했으니까! 괜찮겠지~~
다시 공부하러 가야겠다.
{% endhighlight %}

**깨알팁**  
지킬에서는 post 작성할 때 마크다운 형식이라 자동으로는 개행이 안된다.
이 떄, 맨 뒤에 스페이스를 두개 따닥 붙여놓으면 개행이 된다.


<!-- ![Moon Homepage](https://cloud.githubusercontent.com/assets/754514/14509720/61c61058-01d6-11e6-93ab-0918515ecd56.png)    

<center><b>Moon</b> is a minimal, one column jekyll theme.</center>

 I'm not a developer or designer. And I don't add footer to show who did this theme. If you like this theme or using it, please give a **star** for motivation, It makes me happy.

<iframe src="https://ghbtns.com/github-btn.html?user=TaylanTatli&repo=Moon&type=star&count=true&size=large" frameborder="0" scrolling="0" width="160px" height="30px"></iframe>    

## Installation
* Fork the [Moon repo](https://github.com/TaylanTatli/Moon/fork)
* Edit `_config.yml` file.
* Remove sample posts from `_posts` folder and add yours.
* Edit `index.md` file in `about` folder.
* Change repo name to `YourUserName.github.io`    

That's all.

## Preview

{% capture images %}
	https://cloud.githubusercontent.com/assets/754514/14509716/61ac6c8e-01d6-11e6-879f-8308883de790.png
	https://cloud.githubusercontent.com/assets/754514/14509717/61ad05ae-01d6-11e6-85ae-5a817dd8763b.png
	https://cloud.githubusercontent.com/assets/754514/14509714/61a89708-01d6-11e6-8fcd-74b002a060df.png
{% endcapture %}
{% include gallery images=images caption="Screenshots of Moon Theme" cols=3 %}

---

{% capture images %}
	https://cloud.githubusercontent.com/assets/754514/14509718/61b09a20-01d6-11e6-8da1-4202ae4d83cd.png
	https://cloud.githubusercontent.com/assets/754514/14509715/61aa9d00-01d6-11e6-81a6-c6837edf2e84.png
{% endcapture %}
{% include gallery images=images caption="Moon Theme on Small Screen Size" cols=2 %}      

See a [live version of Moon](http://taylantatli.github.io/Moon) hosted on GitHub.      

## Site Setup
A quick checklist of the files you’ll want to edit to get up and running.    

### Site Wide Configuration
`_config.yml` is your friend. Open it up and personalize it. Most variables are self explanatory but here's an explanation of each if needed:

#### title

The title of your site... shocker!

Example `title: My Awesome Site`

#### bio

The description to show on your homepage.

#### description

The description to use for meta tags and navigation menu.

#### url

Used to generate absolute urls in `sitemap.xml`, `feed.xml`, and for generating canonical URLs in `<head>`. When developing locally either comment this out or use something like `http://localhost:4000` so all assets load properly. *Don't include a trailing `/`*.

Examples:

{% highlight yaml %}
url: http://taylantatli.me/Moon
url: http://localhost:4000
url: //cooldude.github.io
url:
{% endhighlight %}

#### reading_time

Set true to show reading time for posts. And set `words_per_minute`, default is 200.

#### logo
Your site's logo. It will show on homepage and navigation menu. Also used for twitter meta tags.

#### background
Image for background. If you don't set it, color will be used as a background.

#### Google Analytics and Webmaster Tools

Google Analytics UA and Webmaster Tool verification tags can be entered in `_config.yml`. For more information on obtaining these meta tags check [Google Webmaster Tools](http://support.google.com/webmasters/bin/answer.py?hl=en&answer=35179) and [Bing Webmaster Tools](https://ssl.bing.com/webmaster/configure/verify/ownership) support.

#### MathJax
It's enabled. But if you don't want to use it. Set it false in  `_config.yml`.

#### Disqus Comments
Set your disqus shortname in `_config.yml` to use comments.

---

### Navigation Links

To set what links appear in the top navigation edit `_data/navigation.yml`. Use the following format to set the URL and title for as many links as you'd like. *External links will open in a new window.*

{% highlight yaml %}
- title: Home
  url: /

- title: Blog
  url: /blog/

- title: Projects
  url: /projects/

- title: About
  url: /about/

- title: Moon
  url: http://taylantatli.me/Moon
{% endhighlight %}

---

## Layouts and Content

Moon Theme use [Jekyll Compress](https://github.com/penibelst/jekyll-compress-html) to compress html output. But it can cause errors if you use "linenos" (line numbers). I suggest don't use line numbers for codes, because it won't look good with this theme, also i didn't give a proper style for them. If you insist to use line numbers, just remove `layout: compress` string from layouts. It will disable compressing.

### Feature Image

You can set feature image per post. Just add `feature: some link` to your post's front matter.

```
feature: /assets/img/some-image.png
or
feaure: http://example.com/some-image.png
```    
 This also will be used for twitter card:

![Moon Twitter Card](https://cloud.githubusercontent.com/assets/754514/14509719/61c5751c-01d6-11e6-8c29-ce8ccad149bf.png)

### Comments
To show disqus comments for your post add `comments: true` to your post's front matter.

---

## Questions?

Found a bug or aren't quite sure how something works? By all means [file a GitHub Issue](https://github.com/TaylanTatli/Moon/issues/new). And if you make something cool with this theme feel free to let me know.

---

## License

This theme is free and open source software, distributed under the MIT License. So feel free to use this Jekyll theme on your site without linking back to me or including a disclaimer. -->
