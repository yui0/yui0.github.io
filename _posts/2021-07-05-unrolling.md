---
layout: post
title: C言語のループを展開して高速化する
tags: [c,loop,unrolling,fast]
---

C言語のループを展開して高速化するマクロを作成した。

## マクロを使う

```
// ©2021 Yuichiro Nakada
// gcc unrolling.c -o unrolling
#include <stdio.h>

#define DO16(e) e e e e e e e e e e e e e e e e
#define FOR16(n, e) { int c=n/16; n-=c*16; do { DO16(e) } while (--c>0); do { e } while (--n>0); }
#define DO4(e) e e e e
#define FOR4(n, e) { int c=n/4; n-=c*4; do { DO4(e) } while (--c>0); do { e } while (--n>0); }

int main()
{
	int n = 0;
	int len = 17;
	FOR4(len,
		printf("%d\n", n);
		n++;
	);

	n = 0;
	len = 17;
	FOR16(len,
		printf("%d\n", n);
		n++;
	);
}
```
