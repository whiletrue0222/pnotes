---
published: true
title: SourceGear DiffMerge 설치 및 한글 폰트 문제
categories:
- 툴
tags:
- DiffMerge
- DiffMerge한글
- MergeTool
redirect_from:
- archives/97
wpbackup:
  author:
    display_name: whiletrue
    email: whiletrue0222@gmail.com
    login: whiletrue
    url: ''
  author_login: whiletrue
  author_email: whiletrue0222@gmail.com
  wordpress_id: 97
  wordpress_url: http://whiletrue0222.com/pnotes/?p=97
  date: 2011-10-13 12:57:00 +0900
  date_gmt: 2011-10-13 03:57:00 +0900
---

Diff Tool로 WinMerge를 사용하고 있다.
사용하면서 비교 품질이 마음에 안 드는 부분이 조금 있었는데 [본격 diff 툴 비교 리뷰](http://ljh131.tistory.com/143) 이 글 보고 DiffMerge를 설치해 봤다.
아래는 설치하면서 발생한 문제들과 해결



# AnkhSVN 연동 문제

회사에서 VS2005 + AnkhSVN을 사용하고 있는데
DiffMerge연동이 안되었다.
찾아보니 최신 DiffMerge는 실행파일 경로가 변경되었다.

실행파일 경로를 다음과 같이 바꿔주면 해결.

도구 -> 옵션 -> 소스제어 -> Subversion User Tools -> External Diff Tool 에서
C:\Program Files\SourceGear\Common\DiffMerge\sgdm.exe



# 한글 깨지는 문제.

cpp파일을 비교해서 보는데 주석이 깨져서 나오다.
기본 셋팅은 System Character Encoding으로 되어 있는 깨져 나와서 짜증나 있던 중 파일 형식별로 셋팅이 또 따로 있었다.
확인해보니 Encoding이 Western European (ISO-8859-1)로 되어있었다.

Option -> File Windows -> Rulesets -> Custom Rulesets -> C/C++/C# Source 선택 ->
Edit -> Named Character Encoding 이 Western European (ISO-8859-1) 또는 엉뚱한 것으로 되어
있는지 확인.

위에 Fallback Character Encoding Options에서 Use System Local/Default Encoding을
선택하면 해결



아직은 적응이 덜 돼서 인지 툴 UI나 사용성은 WinMerge가 다 좋은 듯하다.
그리고 DiffMerge는 ~~키워드나 주석 컬러링이~~ syntax highlighting이 안돼서 가독성이 떨어지는데 써보고 비교품질마저
마음에 들지 않으면 다시 WinMerge로 갈 생각이다.



제작사 페이지
<http://sourcegear.com/diffmerge/index.html>

---
<http://tortoisesvn.net/docs/release/TortoiseSVN_en/tsvn-dug-settings.html#tsvn-dug-settings-progs>
TortoiseSVN 연동 참고 페이지
