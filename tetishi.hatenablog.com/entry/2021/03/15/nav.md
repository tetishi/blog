---
Title: ナビゲーションをページ上部で固定する Bulma
Date: 2021-03-08T11:29:14+09:00
---
Bulmaではどのようにしてナビゲーションバーを固定できるのか調べました。

Fixed navbar#
You can now fix the navbar to either the top or bottom of the page. This is a 2-step process:

Add either is-fixed-top or is-fixed-bottom to the navbar component
```
<nav class="navbar is-fixed-top">
```
Add the corresponding has-navbar-fixed-top or has-navbar-fixed-bottom modifier to either <html> or <body> element to provide the appropriate padding to the page
```
<html class="has-navbar-fixed-top">
```
Try it out!

参照
https://bulma.io/documentation/components/navbar/#fixed-navbar
