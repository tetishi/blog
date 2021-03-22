---
Title: ナビゲーションをページ上部で固定する方法 Bulma
Date: 2021-03-08T11:29:14+09:00
---
CSSでは`position: fixed;`で出来ますが、Bulmaではどのようにするのか調べてみました。

navbarコンポーネントのところに`is-fixed-top`を置くとナビゲーションをページ上部に固定できるようです。
```
header.navbar.is-fixed-top
```

`has-navbar-fixed-top`をhtmlタグかbodyタグのところに置くとナビゲーションのpaddingを良い感じに調節してくれます。
```
body.has-navbar-fixed-top
```

参考
https://bulma.io/documentation/components/navbar/#fixed-navbar
