---
theme: default
background: https://cover.sli.dev
title: Webpack to Rspack
info: |
  ## Webpack to Rspack
  WebpackからRspackへの移行
class: text-center
drawings:
  persist: false
transition: slide-left
mdc: true
---



## 自己紹介

---

## 今日話すこと
- Rspackとは何か？
- Webpackから移行した結果
- 移行時に詰まったところ
- その他所感

---

## Rspackとは？
Rust製のbundler。Rollup、Rolldown、Webpackと同列。
Webpackとの高い互換性を持ち、Webpackからの移行が容易。
※ Viteとは違う。Viteに対してはRsbuildがある

---

## どんなプロダクトを移行した？

---

## なぜRspackへ移行？

---

Webpack -> Viteはよくある例
なぜあえてRspack？

プロダクトがdjango、vue.jsのSPAだが、JSのエントリーポイントの配信はDjangoが行っていて、その際のscriptの記述に、django-webpack-loader x bundle trackerを使っていた。
その関係でViteへの移行にはバックエンド側の修正も必要になり、二の足を踏んでいた
（工数をかければできるが、通常のプロダクト開発と並行して片手間でやるには重かった）

その点、RspackはWebpackのプラグインがそのまま動くので、django-webpack-loader x bundle trackerの移行問題もない。それで、ただビルドが早くなる
=> 最高

---

## 移行結果は？

ビルド -> 0 % speedup!
dev -> 0% speedup!

最高！

---

## 移行にかかったコストは？

dev ビルドの移行1hほど（documentのmigrationを見ながらそのまま行えばOK）
prod ビルドの移行5hほど（Rspack builtinのloader、pluginのproductionビルドでの動きが
