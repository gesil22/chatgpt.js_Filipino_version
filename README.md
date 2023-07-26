<div align="center">

<div align="right">

###### English | <a href="zh-cn#readme">简体中文</a> | <a href="ja#readme">日本</a> | <a href="hi#readme">हिंदी</a> | <a href="de#readme">Deutsch</a> | <a href="es#readme">Español</a> | <a href="fr#readme">Français</a> | <a href="pt#readme">Português</a>

</div>

<br>

<h3>

<picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/kudoai/chatgpt.js/main/media/images/chatgpt.js-logo-dark-mode-5995x619.png">
    <img width=700 src="https://raw.githubusercontent.com/kudoai/chatgpt.js/main/media/images/chatgpt.js-logo-light-mode-5995x619.png">
</picture>
<br><br>

🤖 Isang malakas na client-side JavaScript library para sa ChatGPT
<br><br>

</div>
</h3>

<div align="center">

[![](https://img.shields.io/badge/License-MIT-green.svg?logo=internetarchive&logoColor=white&labelColor=464646&style=for-the-badge)](LICENSE.md)
[![](https://img.shields.io/github/commit-activity/m/kudoai/chatgpt.js?label=Commits&logo=github&logoColor=white&labelColor=464646&style=for-the-badge)](https://github.com/kudoai/chatgpt.js/commits/main)
![](https://img.shields.io/github/size/kudoai/chatgpt.js/dist/chatgpt-1.12.0.min.js?label=Minified%20Size&logo=databricks&logoColor=white&labelColor=464646&color=ff69b4&style=for-the-badge)
[![](https://img.shields.io/codefactor/grade/github/kudoai/chatgpt.js?label=Code+Quality&logo=codefactor&logoColor=white&labelColor=464646&style=for-the-badge)](https://www.codefactor.io/repository/github/kudoai/chatgpt.js)
[![](https://img.shields.io/badge/Mentioned_in-Awesome-cca8c4?logo=awesomelists&logoColor=white&labelColor=464646&style=for-the-badge)](https://github.com/sindresorhus/awesome-chatgpt#javascript)
[![](https://img.shields.io/badge/Featured_on-Product_Hunt-ff6154?logo=producthunt&logoColor=white&labelColor=464646&style=for-the-badge)](https://www.producthunt.com/posts/chatgpt-js)
![](https://img.shields.io/jsdelivr/gh/hw/kudoai/chatgpt.js?label=jsDelivr+Hits&logo=jsdelivr&logoColor=white&labelColor=464646&color=gold&style=for-the-badge)

</div>

## Tungkol sa

**chatgpt.js** ay isang malakas na JavaScript library na nagbibigay-daan para sa napakadaling pakikipag-ugnayan sa ChatGPT DOM.

- Mayaman sa katangian
- Nakatuon sa bagay
- Madaling gamitin
- Magaan (mahusay na gumaganap)

<p><img type="separator" height=8px width="100%" src="https://raw.githubusercontent.com/kudoai/chatgpt.js/main/media/images/separators/aqua.png"></p>

## Pag-import ng library

### ES6:

```js
(async () => {
  await import('https://code.chatgptjs.org/chatgpt-latest.min.js');
  // Your code here...
})();
```

### ES5:

```js
var xhr = new XMLHttpRequest();
xhr.open('GET', 'https://code.chatgptjs.org/chatgpt-latest.min.js');
xhr.onload = function () {
  if (xhr.status === 200) {
    var chatgptJS = document.createElement('script');
    chatgptJS.textContent = xhr.responseText;
    document.head.appendChild(chatgptJS);
    yourCode(); // runs your code
  }
};
xhr.send();

function yourCode() {
  // Your code here...
}
```

### <img style="margin: 0 2px -0.065rem 0" height=17 src="https://i.imgur.com/SATGr8j.png"></picture><img style="margin: 0 2px -0.035rem 1px" height=17.5 src="https://i.imgur.com/wcCg3al.png"> Greasemonkey:

> **Note** _Upang gumamit ng panimulang template: [kudoai/chatgpt.js-greasemonkey-starter](https://github.com/kudoai/chatgpt.js-greasemonkey-starter)_

 Ang mga repositoryo ng userscript tulad ng Greasy Fork ay nagpapanatili ng whitelist ng mga paunang inaprubahang CDN (gaya ng mga commit-specific na sanggunian mula sa `cdn.jsdelivr.net`) kaya ang URL ng pag-import ay mas mahaba upang mapanatili ang pagiging ma-publish sa mga site na ito.

```js
...
// @require https://cdn.jsdelivr.net/gh/kudoai/chatgpt.js@24a755998291094d0cd3b2bd395dff7c6756bbf9/dist/chatgpt-1.12.0.min.js
// ==/UserScript==

// Your code here...
```

Kung hindi mo planong mag-publish sa mga repo na ito, ang mas simple `https://code.chatgptjs.org/chatgpt-latest.min.js` ay maaring gamitin sa halip upang i-import ang pinakabagong pinaliit na release.

### <img style="margin: 0 2px -1px 0" height=16 src="https://www.google.com/chrome/static/images/favicons/apple-icon-60x60.png"> Chrome:

> **Note** _Upang gumamit ng panimulang template: [kudoai/chatgpt.js-chrome-starter](https://github.com/kudoai/chatgpt.js-chrome-starter)_

Dahil ang Google ay [kalaunan ay mag-phase out](https://developer.chrome.com/docs/extensions/migrating/mv2-sunset/) Manifest V2, hindi na papayagan ang remote code, kaya ang pagpapahalaga sa lokal na chatgpt.js ay mainam:

1. I-save https://raw.githubusercontent.com/kudoai/chatgpt.js/main/chatgpt.js sa isang subdirectory (`lib` sa halimbawang ito)

2. Magdagdag ng ES6 export statement sa dulo ng `lib/chatgpt.js`
```js
...
export { chatgpt }
```

3. Sa project's (V3) `manifest.json`, idagdag ang `lib/chatgpt.js` bilang isang mapagkukunang naa-access sa web
```json
    "web_accessible_resources": [{
        "matches": ["<all_urls>"],
        "resources": ["lib/chatgpt.js"]
    }],
```

4. Sa mga script na nanganagilangan ng `chatgpt.js` (foreground/background magkatulad), i-import ito tulad nito:
```js
(async () => {
  const { chatgpt } = await import(chrome.runtime.getURL('lib/chatgpt.js'));
  // Your code here...
})();
```

<p><img type="separator" height=8px width="100%" src="https://raw.githubusercontent.com/kudoai/chatgpt.js/main/media/images/separators/aqua.png"></p>

## Paggamit

**Ang chatgpt.js** ay isinulat nang may lubos na kakayahang umangkop sa isip.

Halimbawa:

```js
chatgpt.getLastResponse();
chatgpt.getLastReply();
chatgpt.response.getLast();
chatgpt.get('reply', 'last');
```

Ang bawat tawag ay pantay na kumukuha ng huling tugon. Kung sa tingin mo ay gagana ito, malamang gumagana... kaya i-type mo lang!

Kung hindi, magsumite lang ng [issue](https://github.com/kudoai/chatgpt.js/issues) or [PR](https://github.com/kudoai/chatgpt.js/pulls) at ito ay isasama, ezpz!

<p><img type="separator" height=8px width="100%" src="https://raw.githubusercontent.com/kudoai/chatgpt.js/main/media/images/separators/aqua.png"></p>

## Ginawa gamit ang chatgpt.js

### <picture><source media="(prefers-color-scheme: dark)" srcset="https://i.imgur.com/RduASbD.png"><img width=16 src="https://raw.githubusercontent.com/adamlui/chatgpt-addons/main/media/icons/openai-favicon64.png"></picture> [Autoclear ChatGPT History](https://chatgptevo.com/autoclear) <a href="https://github.com/awesome-scripts/awesome-userscripts#chatgpt"><img src="https://awesome.re/mentioned-badge.svg" style="margin:0 0 -2px 5px"></a>

Awtomatikong i-clear ang iyong kasaysayan ng query sa ChatGPT para sa maximum na privacy.
<br>[Install](https://github.com/adamlui/autoclear-chatgpt-history#installation) /
[Readme](https://github.com/adamlui/autoclear-chatgpt-history#readme) /
[Discuss](https://github.com/adamlui/autoclear-chatgpt-history/discussions)

### <img width=16 src="https://i.imgur.com/1yjmK3W.png"> [Automatic ChatGPT DAN](https://github.com/madkarmaa/automatic-chatgpt-dan)

Awtomatikong magpadala ng mga DAN prompt sa ChatGPT.
<br>[Install](https://github.com/madkarmaa/automatic-chatgpt-dan#%EF%B8%8F-installation) /
[Readme](https://github.com/madkarmaa/automatic-chatgpt-dan#readme) /
[Discuss](https://github.com/madkarmaa/automatic-chatgpt-dan/issues)

### <img src="https://media.bravegpt.com/images/bravegpt-icon48.png" width=18> [BraveGPT](https://bravegpt.com) <a href="https://www.producthunt.com/posts/bravegpt?utm_source=badge-featured&utm_medium=badge&utm_souce=badge-bravegpt" target="_blank"><img src="https://api.producthunt.com/widgets/embed-image/v1/featured.svg?post_id=385630&theme=light" style="width: 112px; height: 24px; margin:0 0 -4px 5px;" width="112" height="24" /></a>

Ipakita ang mga sagot sa ChatGPT sa sidebar ng Brave Search (pinapatakbo ng GPT-4!)
<br>[Install](https://github.bravegpt.com/#installation) /
[Readme](https://github.bravegpt.com/#readme) /
[Discuss](https://github.bravegpt.com/discussions)

### <picture><source media="(prefers-color-scheme: dark)" srcset="https://i.imgur.com/RduASbD.png"><img width=16 src="https://raw.githubusercontent.com/adamlui/chatgpt-userscripts/main/media/icons/openai-favicon64.png"></picture> [ChatGPT Auto-Continue ⏩](https://chatgptevo.com/autocontinue/github) <a href="https://github.com/awesome-scripts/awesome-userscripts#chatgpt"><img src="https://awesome.re/mentioned-badge.svg" style="margin:0 0 -3px 3px"></a>

Awtomatikong ipagpatuloy ang pagbuo ng maramihang mga tugon sa ChatGPT.<br>
[Install](https://github.com/adamlui/chatgpt-auto-continue#installation) /
[Readme](https://github.com/adamlui/chatgpt-auto-continue#readme) /
[Discuss](https://chatgptevo.com/autocontinue/discussions)

### <picture><source media="(prefers-color-scheme: dark)" srcset="https://i.imgur.com/RduASbD.png"><img width=16 src="https://raw.githubusercontent.com/adamlui/chatgpt-addons/main/media/icons/openai-favicon64.png"></picture> [ChatGPT Auto Refresh ↻](https://chatgptevo.com/autorefresh) <a href="https://github.com/awesome-scripts/awesome-userscripts#chatgpt"><img src="https://awesome.re/mentioned-badge.svg" style="margin:0 0 -2px 5px"></a>

Pinapanatiling sariwa ang mga session ng ChatGPT para maalis ang mga error sa network + Mga pagsusuri sa Cloudflare.
<br>[Install](https://github.com/adamlui/chatgpt-auto-refresh#installation) /
[Readme](https://github.com/adamlui/chatgpt-auto-refresh#readme) /
[Discuss](https://github.com/adamlui/chatgpt-auto-refresh/discussions)

### <img src="https://media.duckduckgpt.com/images/ddgpt-icon48.png" width=17> [DuckDuckGPT](https://duckduckgpt.com) <a href="https://www.producthunt.com/posts/duckduckgpt?utm_source=badge-featured&utm_medium=badge&utm_souce=badge-duckduckgpt" target="_blank"><img src="https://api.producthunt.com/widgets/embed-image/v1/featured.svg?post_id=379261&theme=light" style="width: 112px; height: 24px; margin:0 0 -4px 5px;" width="112" height="24" /></a>

Ipakita ang mga sagot sa ChatGPT sa DuckDuckGo sidebar (pinapatakbo ng GPT-4!)
<br>[Install](https://github.duckduckgpt.com/#installation) /
[Readme](https://github.duckduckgpt.com/#readme) /
[Discuss](https://github.duckduckgpt.com/discussions)

<br>

<a href="https://chatgptinfinity.com" target="_blank"><img width=555 src="https://raw.githubusercontent.com/adamlui/chatgpt-infinity/main/chrome/media/images/tiles/marquee-promo-tile-1400x560.png"></a>

<br>

<a href="https://chatgptwidescreen.com" target="_blank"><img width=555 src="https://raw.githubusercontent.com/adamlui/chatgpt-widescreen/main/chrome/media/images/tiles/marquee-promo-tile-1400x560.png"></a>

<br>

Kong may ginawa ka sa chatgpt.js na gusto mong ibahagi, mag-email sa [showcase@chatgptjs.org](mailto:showcase@chatgptjs.org) o magbukas lang ng [pull request](https://github.com/kudoai/chatgpt.js/pulls)!

<p><img type="separator" height=8px width="100%" src="https://raw.githubusercontent.com/kudoai/chatgpt.js/main/media/images/separators/aqua.png"></p>

## Mga Kontribyutor

Umiiral ang library na ito salamat sa code, pagsasalin, isyu at ideya mula sa mga sumusunod na kontribyutors:

[![](https://images.weserv.nl/?url=https://avatars.githubusercontent.com/u/10906554?first-contrib=2023.03.15&h=50&w=50&mask=circle&maxage=7d '@adamlui')](https://github.com/adamlui)
[![](https://images.weserv.nl/?url=https://avatars.githubusercontent.com/u/71683364?first-contrib=2023.03.16-get-functions&h=50&w=50&mask=circle&maxage=7d '@mefengl')](https://github.com/mefengl)
[![](https://images.weserv.nl/?url=https://avatars.githubusercontent.com/u/131989355?first-contrib=2023.04.30-doc-translations&h=50&w=50&mask=circle&maxage=7d '@Zin6969')](https://github.com/Zin6969)
[![](https://images.weserv.nl/?url=https://avatars.githubusercontent.com/u/30551844?first-contrib=2023.05.02-getlastresponse-bug-report&h=50&w=50&mask=circle&maxage=7d '@madruga8')](https://github.com/madruga8)
[![](https://images.weserv.nl/?url=https://avatars.githubusercontent.com/u/54934866?first-contrib=2023.05.01-clearchats-discard-fix&h=50&w=50&mask=circle&maxage=7d '@XiaoYingYo')](https://github.com/XiaoYingYo)
[![](https://images.weserv.nl/?url=https://avatars.githubusercontent.com/u/129722778?first-contrib=2023.05.24-css-readability&h=50&w=50&mask=circle&maxage=7d '@AliAlSarre')](https://github.com/AliAlSarre)
[![](https://images.weserv.nl/?url=https://avatars.githubusercontent.com/u/100418457?first-contrib=2023.06.02-send-function-bug-report&h=50&w=50&mask=circle&maxage=7d '@madkarmaa')](https://github.com/madkarmaa)
[![](https://images.weserv.nl/?url=https://avatars.githubusercontent.com/u/1170326?first-contrib=2023.06.10-html-parser-idea&h=50&w=50&mask=circle&maxage=7d '@wamoyo')](https://github.com/wamoyo)
[![](https://images.weserv.nl/?url=https://avatars.githubusercontent.com/u/33952?first-contrib=2023.06.10-html-parser-idea&h=50&w=50&mask=circle&maxage=7d '@meiraleal')](https://github.com/meiraleal)
[![](https://images.weserv.nl/?url=https://avatars.githubusercontent.com/u/22633385?first-contrib=2023.07.11-fix-ja-doc-md&h=50&w=50&mask=circle&maxage=7d '@eltociear')](https://github.com/eltociear)
[![](https://images.weserv.nl/?url=https://avatars.githubusercontent.com/in/29110&h=50&w=50&mask=circle&maxage=7d 'Dependabot')](https://github.com/dependabot)
[![](https://images.weserv.nl/?url=https://i.imgur.com/tNyIPmG.jpg?h=50&w=50&mask=circle&maxage=7d 'ChatGPT')](https://chat.openai.com)

<br>

<p><img type="separator" height=8px width="100%" src="https://raw.githubusercontent.com/kudoai/chatgpt.js/main/media/images/separators/aqua.png"></p>

<div id="star-history" align="center">

<br>

<a href="https://star-history.com/#kudoai/chatgpt.js&Timeline">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://api.star-history.com/svg?repos=kudoai/chatgpt.js&type=Timeline&theme=dark" />
    <img width=665 src="https://api.star-history.com/svg?repos=kudoai/chatgpt.js&type=Timeline" />
  </picture>
</a>

<br>_Pag-isipang bigyan ang repo na ito ng ⭐ kung nkatulong ito sa iyo!_

</div>

#

<a href="https://github.com/kudoai/chatgpt.js/tree/main/dist">**Releases**</a> /
<a href="https://github.com/kudoai/chatgpt.js/discussions">Discuss</a> /
<a href="#">Back to top ↑</a>
