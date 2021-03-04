---
title: "Using Furigana in Hugo"
description: "Furigana adalah huruf hiragana di atas huruf kanji yang berguna sebagai cara membaca kanji"
date: 2020-01-28T00:36:19+09:00
draft: false
---

## Furigana dalam Hugo

Penulisan blog di Hugo menggunakan markdown (.md). Dan alhamdulillah Hugo memiliki fitur untuk menampilkan furigana. Furigana adalah huruf hiragana yang ditempatkan di atas huruf kanji untuk memudahkan membaca kanji misalnya adalah sebagai berikut:

<ruby>許<rp>(</rp><rt>ゆる</rt><rp>)</rp><ruby>してくれて、ありがとう。

Dibaca: yurushite kurete, arigatou.
Artinya: terima kasih telah memaafkanku.

### Penggunaan

Berikut ini adalah markup-nya:

```ruby
<ruby>許<rp>(</rp><rt>ゆる</rt><rp>)</rp><ruby>してくれて、ありがとう。
```

### Referensi

[https://discourse.gohugo.io/t/using-furigana-ruby-with-markdown/15156/3](https://discourse.gohugo.io/t/using-furigana-ruby-with-markdown/15156/3)
