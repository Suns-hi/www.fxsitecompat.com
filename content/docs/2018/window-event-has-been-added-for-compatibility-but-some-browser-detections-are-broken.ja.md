---
title: "`window.event` が互換性のため追加されましたが、一部のブラウザー判別に影響があります"
date: "2018-08-14T19:14:00-04:00"
categories: ["dom"]
tags: []
versions: ["63"]
statuses: "affecting"
references:
    - url: "https://bugzilla.mozilla.org/show_bug.cgi?id=218415"
      title: "Bug 218415 - Request for window.event object added to DOM to ease cross browser scripting"
    - url: "https://bugzilla.mozilla.org/show_bug.cgi?id=1479964"
      title: "Bug 1479964 - Tracking event.keyCode issue due to the implementation of window.event"
---
Firefox 63 で [`window.event`](https://developer.mozilla.org/docs/Web/API/Window/event) プロパティが実装されました。これは Internet Explorer に由来するものですが、`Event.prototype.srcElement`、`Event.prototype.returnValue` とともに DOM 仕様での標準化が行われたためです。

この変更はウェブ互換性の改善を意図していますが、この旧非標準プロパティを使用した一部のブラウザー判別コードはむしろ正常に動作しなくなることが予想されます。既に報告されている典型的な例は、Firefox では `0` を返す `event.keyCode` を巻き込んだもので、Mozilla のエンジニアが対応中です。他にも問題が発生する可能性があるため、あなたのコードをスキャンして、もし `window.event` が見つかった場合は、その機能が Firefox で動作することを確かめてください。

なお、`srcElement` の対応は既に [Firefox 62 で追加](https://www.fxsitecompat.com/ja/docs/2018/support-for-event-prototype-srcelement-has-been-added/) されており、これも少なくとも 1 件の互換性問題をもたらしています。
