---
layout: post
date: '2017-03-30 12:00 +0900'
published: true
title: 自分のブログがはてブされたらはてなの「お知らせ」に通知させる【Jekyll版】
tags: hatena jekyll
---
はてなブログに慣れきっているのでこれがないとなんか落ち着かない。

▼ のコードを`_layouts/default.html`などからヘッダーやフッターに貼り付けるだけでほぼ完了。

```html
<!--hatena bookmark notify-->
<rdf:RDF
xmlns:rdf="http://www.w3.org/1999/02/22-rdf-syntax-ns#"
xmlns:dc="http://purl.org/dc/elements/1.1/"
xmlns:foaf="http://xmlns.com/foaf/0.1/">
<rdf:Description rdf:about="{% raw %}{{ site.url }}{{ page.url }}{% endraw %}">
<foaf:maker rdf:parseType="Resource">
<foaf:holdsAccount>
<foaf:OnlineAccount foaf:accountName="はてなID">
<foaf:accountServiceHomepage rdf:resource="http://www.hatena.ne.jp/" />
</foaf:OnlineAccount>
</foaf:holdsAccount>
</foaf:maker>
</rdf:Description>
</rdf:RDF>
```

はてなIDの部分に自分のIDを入力すればOK。うまくいかない場合は`{% raw %}{{ site.url }}{{ page.url }}{% endraw %}`の部分を`{% raw %}{{ site.url }}{{ site.baseurl }}{{ page.url }}{% endraw %}`するなど自分の設定にあわせて変更してください。よく分からない場合は`{% raw %}{{ site.url }}{% endraw %}`だけにすれば通知されます。

参考 : <a href="http://b.hatena.ne.jp/help/entry/nocomment#pageauth" target="_blank">コメント一覧非表示機能について - はてなブックマークヘルプ</a>
