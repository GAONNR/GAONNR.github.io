<!--
---
layout: post
title: 포맷 스트링 버그 정리
category: hacking
---

포맷 스트링 버그(Format String Bug, FSB)는 동아리에서 밥값을 하기 위해선 필수인 기법임에도 불구하고, 매번 할 때마다 까먹고 헷갈려서, 확실한 기억을 위해 여기에 정리해서 올리기로 하였다.

우선 포맷 스트링이란 무엇인가에 대해 알아볼 필요가 있다. C언어를 다뤄 본 사람이라면, 다음과 같은 코드들을 많이 써 봤을 것이다.

    printf("%d", num);
    printf("%s", str);

여기서, `%d`나 `%s`같은 인자들을 포맷 스트링이라고 부른다.

/home/fsb

vim fsb.c

gdb fsb -> print &changethis
-->
