---
title: 안녕 파이썬
tags:
- python
---

![python-logo]

# import `__hello__`

책으로 맛만 보는거라던가, 업무상 필요해서 급하게 익히는 거 말고 능숙히 다룰 언어가 있어야 될거 같다.
그래서 선택한 언어는 파이썬.

들여쓰기를 강제한다.
와. 중괄호 안 써도 된다. 중괄호 위치 논쟁도 없겠고.
공백이냐 탭이냐, 중괄호를 어디에 붙일거냐 이런 소모적인 논쟁은 적겠다 싶었다.

# import this
파이썬에 대해서는 이래저래 얘기를 많이 들었다.
간결한 언어이고 크리스마스에 만들기 시작했고 구글에서도 사용하고 여러 게임회사에서도 사용하고.

파이썬을 선택하게 된 가장 큰 영향은 아래 철학인거 같다.

>
> There should be one`--`and preferably only one`--`obvious way to do it.
> 어떤 일에든 명확한 - 바람직하며 유일한 - 방법이 존재한다.
> 
> [The Zen of Python][pep20] ([번역 출처][zenofpy_ko])


# 어떻게 익힐까?
사실 익히려고 시도는 많이 했다.
근데 진도가 안나간다.

처음에는 목표 없이 책만 읽었다. 문법이나 사용법을 알아야 코딩을 할테니.
[파이썬 완벽 가이드] 언어 부분 읽는데만 한참 걸렸다.
알고 있는 개념을 문법이 다른 이유로 다시 읽으려니 곤욕이었다.

이대론 안되겠다.
즐겁게 익힐 방법이 뭐가 있을까?

업무상 내 행동패턴을 보면 하루에도 수십번 여는 폴더가 있다.
작업표시줄에 가득차면 번잡하니 다 닫고
다시 그 폴더를 열고 그런다.

폴더부터 원클릭으로 열어보자.
그래서 업무상 개인적으로 사용할 툴을 만들면서 파이썬을 익혔다.
혼자쓸꺼니 막짜도 되고. 시간 날 때 우아한 방법을 찾아보지. 뭐 어때.


# 책
[파이썬 완벽 가이드]로 기본 사용 법을 익혔다.
[파이썬 코딩의 기술]도 종종 읽고.
[파이썬을 여행하는 히치하이커를 위한 안내서]가 나왔길래 사서 봤다.

히치하이커를 처음 읽었으면 좋았을텐데.. 본격적으로 익히기 시작했을 때는 출간이 안됐었고 사이트가 있는지도 몰랐다.


# Windows 에서 python 사용하기
Windows에서는 겪는 문제들이 많다. 뭔가를 익힐 때 자주 발목을 잡는다.

## pip install
cmd.exe 를 열고 pylint를 설치하면 에러가 난다. (파워쉘로 해도 마찬가지다)
```batch
pip install pylint
```
> UnicodeDecodeError: 'utf-8' codec can't decode byte 0xb6 in position 67: invalid start byte

이건 또 뭐람.

[Git for Windows]를 설치하고 그에 딸려오는 git bash상에서 설치하면 된다.
pip 로 패키지 설치할 때 실패하면 항상 git bash로 설치한다.

## venv
가상환경이란게 있네.
개인적으로 사용할 것이니 안 써도 됐다.
익히는 것에 집중하고 싶어 신경도 안썼지만 알긴 해야지.

[venv]가 있고 좀더 편하게 쓸 수 있게 [virtualenvwrapper]도 있다.
아니 왠걸 윈도우즈에서는 [virtualenvwrapper]가 동작 안한다.
[virtualenvwrapper-win]을 써야 한다.

[파이썬의 개발 "환경" (env) 도구들] 이 포스트가 많이 도움됐다.


# IDE
[VSCode]와 [PyCharm]을 같이 사용했다.
PyCharm만 썻더라면 위 문제들은 겪지도 않았을 것 같다.

PyCharm이 편하고 좋은데 자동으로 해주는 게 많아서 왜 되는지 몰랐다.
예로 PyCharm은 기본 설정으로 다음이 체크되어 있다.
- Add content roots to PYTHONPATH
- Add source roots to PYTHONPATH

지금도 왜 이게 옵션으로써 필요한지 모르겠다. 독학의 한계인가.

비교 대상이 있으면 이해 하기도 편하고 왜 좋은지 알 수 있을 것 같았다.
궁금하자나. 번거롭더라도 같이 썻다.


# 몇 가지 라이브러리에 대한 소감

## [Data Classes](https://www.python.org/dev/peps/pep-0557/)
파이썬은 struct가 없다. class를 쓰던 [namedtuple]을 써야하는데 불편하다.
dataclasses는 직관적이고 타이핑도 적다.

## [jsoncomment](https://pypi.python.org/pypi/jsoncomment/0.2.3)
json 스펙에는 주석이 없다. 표준 모듈로는 주석을 포함하면 파싱을 못한다.
근데 주석 포함해서 많이들 쓰잖아. VSCode 설정 파일만 해도 그렇고.

double slash(//) 주석을 쓰려면 아래처럼 만져줘야 한다.
```python
import jsoncomment
jsoncomment.package.comments.COMMENT_PREFIX = ("#", ";", "//")
```

## [tkinter](https://docs.python.org/3.6/library/tkinter.html)
파이썬에 내장된 모듈이라 처음에 썼다.

## [PyQt](https://www.riverbankcomputing.com/software/pyqt/intro)
tkinter로는 뭔가 부족하고 안 이쁘다.
그래서 PyQt로 교체. 근데 cx_Freeze로 패키징하면 용량이 크더라.

[qdarkstyle]로 시커멓게 만들어 썼다.

## [cx_Freeze](https://anthony-tuininga.github.io/cx_Freeze/)
배포용으로 만들기 위해 사용.
인하우스툴을 쓰기 위해 모두가 파이썬을 설치할 필요가 없으니.

## [pyparsing](http://pyparsing.wikispaces.com/)
파서 라이브러리.
소스 파일에서 enum만 파싱해서 다둘일이 있었는데 하드 코딩했었다.
다음엔 이거 써서 만들어야지.
예제도 풍부하다.


# 마무리

[지킬로 이사할 때 사용했고][hello-jekyll] 간단한 툴 만들때도 사용해봤다.
다음에는 뭘 만들어볼까?

겨우 걸음마를 뗀 수준이지만 익히는 과정에서 다른 것들도 많이 배우게 된 것 같다.
쓸수록 매력있는 언어다.

[List Comprehensions] 사랑한다.


[//]: <> (책 링크)
[파이썬 완벽 가이드]: http://www.insightbook.co.kr/book/programming-insight/%ED%8C%8C%EC%9D%B4%EC%8D%AC-%EC%99%84%EB%B2%BD-%EA%B0%80%EC%9D%B4%EB%93%9C
[파이썬 코딩의 기술]: https://ridibooks.com/v2/Detail?id=754018005&_s=search&_q=%ED%8C%8C%EC%9D%B4%EC%8D%AC
[파이썬을 여행하는 히치하이커를 위한 안내서]: http://www.yes24.com/24/goods/55258117


[//]: <> 기타 링크
[pep20]: https://www.python.org/dev/peps/pep-0020/
[zenofpy_ko]: https://bitbucket.org/sk8erchoi/peps-korean/src/5e2f0c181f5ff13d7947515ed7e82c805e9f6629/pep-0020.txt?at=default&fileviewer=file-view-default
[파이썬의 개발 "환경" (env) 도구들]: https://spoqa.github.io/2017/10/06/python-env-managers.html


[venv]: https://docs.python.org/3/library/venv.html
[virtualenvwrapper]: https://pypi.python.org/pypi/virtualenvwrapper/4.8.2
[virtualenvwrapper-win]: https://pypi.python.org/pypi/virtualenvwrapper-win
[namedtuple]: https://docs.python.org/3/library/collections.html#collections.namedtuple
[qdarkstyle]: https://github.com/ColinDuquesnoy/QDarkStyleSheet
[List Comprehensions]: https://www.python.org/dev/peps/pep-0202/

[VSCode]: https://code.visualstudio.com/
[PyCharm]: https://www.jetbrains.com/pycharm/
[Git for Windows]: https://gitforwindows.org/
[hello-jekyll]: {{ site.baseurl }}{% post_url 2018-03-14-hello-jekyll %}

[//]: <> (이미지)
[python-logo]: https://lh3.googleusercontent.com/7SU0tS6FDAcX9QBwr00Rl6mlJlbaCdLKEumecuVP5xR3fUW2XOCPEF-gqBjEm1-Qp-6nv3AiVptSQZ2zmnPCwY7hloj52WVW9KT8YBYH76q7GdY44uUUy4nHrnqU1ud18U1fLGqZXA1sfNcNFuPBSunlyo5vPZulckzvwneLmL5zk2UaeklSQVN3k-ADLVlYwVf_m2SMZFMbf_i87LTSKR191dIu5Yq6QGc24zKTl66TPajzglBh6aAgInp5D4p7AUwfWYPfc7jvhTFBCSgMbrwxb0QVGDAAdiPMqrc_duD39yAzYQM4gJVoVQV_cmloXAW-VFeb76CJv61TYJO-uPP5Qo4-o03WPlU5XLJLE3abOlK6XFiZQrgaa7HaTU52Qm2600X3yBj9voZwRaKGClamh820U3K2fd6f7gAUAPgBburmbcsaNxhGjVKzCfPFGztfG0LphNDZ6199grIzSCfCdrq7WqT3aZvVwnkT6wSBcW986DYK6IlohacZT0O2QnwLvg3y-U5-hVT0flvlQitk6yaCeIK2XTtX3xwrYoaTWoZkkrUrlN40VbExDGdLxPv92iFURvKD3iEIZUv6YSzYHKQ5EFBAgehtc4fonPhpkKvwMhNGfPSatYir1embFP9PncjrxUqPHRWfZ3gJDG7z6nWzqcZ39A=w290-h82-no
