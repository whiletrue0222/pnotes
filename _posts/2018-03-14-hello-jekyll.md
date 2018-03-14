---
title: 안녕 지킬
---

# 지킬로 이사 결정
지킬로 이사했다.
몇년간 글을 안썼지만 관리 이슈로 이사했다.

cafe24 웹호스팅으로 [워드프레스]와 [도쿠위키] 를 사용하고 있었다.
몇년전에 도쿠위키가 php 지원 버전을 올렸는데 이용중인 웹호스팅 서비스가 지원하는 php 버전이 낮았다.
php 버전을 올리려면 웹호스팅 서비스를 변경해야했다.

아직까지는 이용중인 웹호스팅 서비스로 워드프레스를 최신으로 사용할 수 있다.
그렇치만 앞으로도 그럴까?

유지비는 얼마 안하지만, 사용 비중이 높지 않은데 주기적으로 웹호스팅 서비스를 변경하고 싶지 않았다.
워드프레스도 영원할 거 같지 않고.

도쿠위키는 비공개 개인적인 기록이 위주라 굳이 위키일 필요가 없다.
쓰기 편한 [원노트]로 전부 옮겼다

블로그는 어쩔까? 호스팅 업체를 바꿔야 하나?
[지킬]/[GitHub Pages]는 어떨까?

일단 [staticgen]을 살펴봤다.

최근 개인적으로 파이썬을 쓰며 공부해서 파이썬으로 작성된 [pelican]을 고려했으나 최신 릴리즈가 1년이 넘었더라.

**불안하다.**

아는분 께도 물어보고 [GitHub에서도 미니까](https://help.github.com/articles/using-a-static-site-generator-other-than-jekyll/) 지킬로 가자

그래서 블로그는 지킬로 선택.


# 이사하자

[pnotes]와 [lifelog] 합쳐서 글이 82개다.
손으로 옮기기 너무 싫다. 귀찮아.

[jekyll importer]가 있다. 이거 없었음 그냥 워드프레스 썼을꺼다.

[WordPress](https://import.jekyllrb.com/docs/wordpress/), [WordPress.com](https://import.jekyllrb.com/docs/wordpressdotcom/) 2가지 버전이 있다.

난 셀프 호스팅이니 전자를 선택.
나중에 알고보니 셀프호스팅이더라도 내보내기한 xml 파일로 WordPress.com impoter를 사용할 수 있다.

import 결과물의 파일명들이 [퍼센트인코딩]되었다.
사람이 알아 먹을 수 있나.

파이썬으로 변환했다
```python
import os
from urllib.parse import unquote

os.rename(filename, unquote(filename))
```

파일들을 열어보니 frontmatter에 불필요한게 많다.
그리고 내용은 html이다.

[python-frontmatter]를 이용해서 load, save
내용은 [html2text]를 이용해 변환.

```python
import frontmatter
import html2text

with open('_post/post.html') as f:
    post = frontmatter.load(f)

    # 불필요한 거 삭제
    del post.metadata['key']

    # 마크다운으로 변환
    post.content = html2text.html2text(post.content)

with codecs.open(mdpath, 'w', encoding='utf-8') as mdfile:
    text = frontmatter.dumps(post,
                             allow_unicode=True)  # 한글이 %로 인코딩된다 url 인코딩?
```

metadata가 dict 타입인데 저장할 때 정렬되서 저장된다.
변환이 잘됐나 diff 로 확인해야하는데 원본 순서대로 저장이 안되니 확인이 힘들다.

구글링 해서 원본 순서대로 저장하는 방법을 찾았다.
<https://stackoverflow.com/questions/16782112/can-pyyaml-dump-dict-items-in-non-alphabetical-order>

위 링크대로 representer를 추가하고
변환 단계에 metadata를 OrderedDict로 변경했다.
```python
def dict_to_odereddict(d: Dict):
    l = []
    for key, val in d.items():
        if isinstance(val, dict):
            val = dict_to_odereddict(val)
        l.append((key, val))
    return OrderedDict(l)

post.metadata = dict_to_odereddict(post.metadata)

text = frontmatter.dumps(post,
                         Dumper=yaml.Dumper  # dumper 지정
                         allow_unicode=True)
```

포스트 url은 어떻게하지? 유지했으면 좋겠는데..
frontmatter에 [permalink]를 이용할까?

워드프레스의 포스트 url은 /archive/1 처럼 번호형식으로 썼다
일관성을 위해 새글의 permalink를 일일이 지정하고 넘버링하는 것도 힘들고 귀찮을거 같다.

[jekyll-redirect-from]을 이용했다.

새로운 url 형식은 :year/:title 로 했다. default는 너무 긴거 같아


# 한땀 한땀
html2text 변환 결과물이 완벽하지는 않다.
테이블이나 link에 불필요한 개행 문자들이 포함되어 있다.

일부 이미지/유튜브 링크들을 아예 날려 먹은 것도 있다.

이런건 어쩔 수 없이 하나하나 워드프레스 글들과 비교하며 수정했다.


# 호스팅, 저장소
호스팅은 당연히 [GitHub Pages]

워드프레스 쓸때는 [multisite] 기능을 이용했었는데 지킬은 그런거 없다.

실질적으로 블로그는 [pnotes], [lifelog] 2개지만 [root]를 위한 페이지 저장소도 만들어야 한다.
이렇게 말이다.
- <https://whiletrue0222.com>
- <https://whiletrue0222.com/pnotes/>
- <https://whiletrue0222.com/lifelog/>


몇몇 실수 했던 것을 적자면
## 저장소 이름
root 저장소는 이름에 저장소 이름에 .github.io 를 붙여야 한다.
이렇게 **whiletrue0222.github.io**

대충 읽은 것을 반성.

## 저장소에 올릴거?
GitHub에 jekyll 원본? 그대로 올리면 된다.

jekyll 문서 읽을 때 build 가 있길래 빌드 후 결과물인 _site 를 올리는 건줄 알았는데
뭔가 찜찜한게 아닌거 같아서 [지킬을 쓰는 사이트](https://jekyllrb.com/docs/sites/)를 봤더니 빌드한걸로 올리지 않네?

빌드는 GitHub에서 알아서 해준다.

# 테마

GitHub Page에서 이용할 수 있는 테마는 한정되어 있다
<https://pages.github.com/themes/>

적용하니 글목록이 안나오네?

index.md 파일을 손바줘야 겠네.
[minima 테마의 home을 참고 했다](https://github.com/jekyll/minima/blob/master/_layouts/home.html)

# 도메인

cafe24에서 기존 블로그에 도메인 연결을 끊고 A Record를 변경
<https://help.github.com/articles/setting-up-an-apex-domain/>

그리고 
whiletrue0222.github.io 저장소 설정에서 custom domain 을 지정했다.
그러니 CNAME 파일이 자동으로 생기네

# 끝
틈틈히 작업해서 1주일 정도 걸렸다.

파이썬 코딩도 하고 이것 저것 새로 알아가는 재미도 있었다.

[root]: https://whiletrue0222.com
[pnotes]: https://whiletrue0222.com/pnotes
[lifelog]: http://whiletrue0222.com/lifelog
[지킬]: https://jekyllrb.com/
[워드프레스]: https://wordpress.org/
[도쿠위키]: https://www.dokuwiki.org
[원노트]: https://www.onenote.com
[staticgen]: https://www.staticgen.com/
[pelican]: http://docs.getpelican.com/en/stable/index.html
[GitHub]: https://github.com/
[jekyll importer]: https://import.jekyllrb.com/docs/home/
[퍼센트인코딩]: https://ko.wikipedia.org/wiki/%ED%8D%BC%EC%84%BC%ED%8A%B8_%EC%9D%B8%EC%BD%94%EB%94%A9
[python-frontmatter]: http://python-frontmatter.readthedocs.io/en/latest/
[html2text]: https://github.com/aaronsw/html2text
[permalink]: https://jekyllrb.com/docs/permalinks/
[jekyll-redirect-from]: https://github.com/jekyll/jekyll-redirect-from
[GitHub Pages]: https://pages.github.com/
[multisite]: https://codex.wordpress.org/Create_A_Network
