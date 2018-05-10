---
title: "`removestream` イベントが `RTCPeerConnection` から削除されました"
date: "2018-05-09T09:54:00-04:00"
categories: ["audio-video", "dom"]
tags: []
versions: ["60"]
references:
    - url: "https://bugzilla.mozilla.org/show_bug.cgi?id=1442385"
      title: "Bug 1442385 - Remove dead onremovestream code"
---
`RTCPeerConnection` インターフェイス上の [`removestream`](https://developer.mozilla.org/ja/docs/Web/Events/removestream) イベントとそれに対応する [`onremovestream`](https://developer.mozilla.org/ja/docs/Web/API/RTCPeerConnection/onremovestream) イベントハンドラープロパティは、WebRTC 仕様で廃止されたため、Firefox 60 で削除されました。`MediaStream` 上の `removetrack` イベントとそれに対応する [`onremovetrack`](https://developer.mozilla.org/ja/docs/Web/API/MediaStream/onremovetrack) イベントハンドラーを代わりに使ってください。