---
layout: post
title: C言語のループを展開して高速化する
tags: [c,loop,unrolling,fast]
---

C言語のループを展開して高速化するマクロを作成した。

## マクロを使う

- ソース

```
// ©2021 Yuichiro Nakada
// gcc unrolling.c -o unrolling
#include <stdio.h>

#define DO16(e) e e e e e e e e e e e e e e e e
#define FOR16(n, e) { int c=n/16; n-=c*16; for (; c>0; c--) { DO16(e) }; do { e } while (--n>0); }
#define DO4(e) e e e e
#define FOR4(n, e) { int c=n/4; n-=c*4; for (; c>0; c--) { DO4(e) }; do { e } while (--n>0); }

int main()
{
	int n = 0;
	int len = 17;
	FOR4(len,
		printf("%d\n", n);
		n++;
	);

	n = 0;
	len = 3;
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

- 実行結果

```
$ ./unrolling 
0
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
0
1
2
0
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
```
