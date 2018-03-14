---
published: true
title: Effective STL - 10년된 책이지만 여전히 유용하다
categories:
- 책
redirect_from:
- archives/184
wpbackup:
  author:
    display_name: whiletrue
    email: whiletrue0222@gmail.com
    login: whiletrue
    url: ''
  author_login: whiletrue
  author_email: whiletrue0222@gmail.com
  wordpress_id: 184
  wordpress_url: http://whiletrue0222.com/pnotes/?p=184
  date: 2013-05-17 02:03:10 +0900
  date_gmt: 2013-05-16 17:03:10 +0900
---

![](https://lh4.googleusercontent.com/-Vvmkl0JFj0M/UZUFJLoyqUI/AAAAAAAAD9g/3mZqTgHBXBQ/s400/effective%2520stl.jpg)

국내에 번역서는 2006년에 출간되었지만 원서는 2001년에 나왔다.
벌써 10년이 넘은 책이다.
더 늦기전에 읽는 게 좋을 것 같아서 C++11도 나온 지금에서야 읽게 되었다.

책이 나온지 오래됐기에 당시의 STL 플랫폼과 C++사양으로 설명하기 때문에 옛날 이야기 같은 내용도 있지만, 여전히 유용하고 깊이 있는
내용들이 많다.

STL의 활용뿐 아니라 관련 개념이라던가 용어에 대한 설명도 잘 되어 있기 때문에 도움이 많이 되었다.

앞으로도 틈틈히 들춰보면서 상기 시켜야 될 것 같다.

밑줄 쫙.

> p130
>  "수축시켜 맞추기" 방법은 엄밀히 말해 "용량을 최대한 작게 만드는 것"이 아니라. "컨테이너의 현재 크기(size)에 대해 구현 코드에 따라 다르게 만들어지는 용량만큼 작게 만드는 것"이라고 알아두셔야 정확합니다.

> p136
>  정의를 어떻게 내렸느냐에서 출발하고 있는데, find 알고리즘의 경우 상등정(equality)으로 내린 반면, set::insert는 동등성(equivalence)으로 내리고 있습니다.

> p288
>  정렬되지 않은 범위가 정렬된다는 것은 정렬 이외의 또 하나의 변화를 뜻합니다. 두 개의 값이 같은지를 비교할 때 사용하던 상등성(equality) 기준이 동등성(equivalence)으로 바뀐다는 것이죠.

> p301
>  함수를 매개 변수로 넘기려고 하면, 컴파일러는 조용히 이 함수를 함수 포인터로 바꿔 버립니다. 즉, 실제로 넘겨지는 놈은 포인터라는 이야기죠.

> p306
>  코드를 쓰기보다는 읽기를 더 많이 하는 것이 소프트웨어 공학의 본질이요 이치입니다.

...

>  여러분이 오늘 작성한 코드는 언젠가 다른 사람들 -여러분 자신일 수도 있습니다- 이 읽을 거라는 사실을요. 그때를 대비해 두라는 말입니다.
