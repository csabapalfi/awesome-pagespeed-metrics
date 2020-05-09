# Awesome Page Speed Metrics [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> Metrics to help understand page speed and user experience.

## Contents

<!-- toc -->

- [Concepts](#concepts)
  - [Lab Data (Synthetic Measurements)](#lab-data-synthetic-measurements)
  - [Field Data (Real User Monitoring - RUM)](#field-data-real-user-monitoring---rum)
  - [Critical rendering path](#critical-rendering-path)
  - [Long tasks](#long-tasks)
  - [User-centric metrics](#user-centric-metrics)
  - [Apdex score](#apdex-score)
- [Rendering metrics](#rendering-metrics)
  - [First Contentful Paint (FCP)](#first-contentful-paint-fcp)
  - [First Meaningful Paint (FMP)](#first-meaningful-paint-fmp)
  - [Speed Index](#speed-index)
  - [Start render](#start-render)
  - [First Paint (FP)](#first-paint-fp)
  - [Visually Complete](#visually-complete)
  - [Hero Element Timing](#hero-element-timing)
  - [Cumulative Layout Shift (CLS)](#cumulative-layout-shift-cls)
  - [Largest Contentful Paint (LCP)](#largest-contentful-paint-lcp)
- [Interactivity metrics](#interactivity-metrics)
  - [First CPU Idle](#first-cpu-idle)
  - [Time to Interactive (TTI)](#time-to-interactive-tti)
  - [First Input Delay (FID)](#first-input-delay-fid)
  - [First Interactive](#first-interactive)
  - [Consistently Interactive](#consistently-interactive)
  - [Estimated Input Latency](#estimated-input-latency)
  - [Max Potential First Input Delay](#max-potential-first-input-delay)
  - [Total Blocking Time (TBT)](#total-blocking-time-tbt)
- [Network metrics](#network-metrics)
  - [DNS latency](#dns-latency)
  - [TCP and SSL/TLS latency](#tcp-and-ssltls-latency)
  - [Time to First Byte (TTFB)](#time-to-first-byte-ttfb)
  - [Transferred bytes](#transferred-bytes)
- [Other metrics](#other-metrics)
  - [Google PageSpeed Insights score](#google-pagespeed-insights-score)
  - [User Timing](#user-timing)
  - [Server Timing](#server-timing)
  - [Frame rate](#frame-rate)
  - [DOMContentLoaded](#domcontentloaded)
  - [window.load](#windowload)

<!-- tocstop -->

## Concepts

### Lab Data (Synthetic Measurements)

Make a request to your page with a tool and evaluate performance. Be sure to make it realistic (e.g. by throttling network and CPU) and reduce noise (e.g. by running multiple times).

- [Lighthouse](https://developers.google.com/web/tools/lighthouse/) - A tool built on Google Chrome to audit web pages. You can run it from Chrome DevTools, a Chrome Extension or from the command line (even with headless Chrome).
- [Google PageSpeed Insights](https://developers.google.com/speed/pagespeed/insights/) - Free and hosted Lighthouse reporting (and more) by Google.
- [WebpageTest](https://www.webpagetest.org/) - Free and hosted web performance testing (also an open source project).
- [Sitespeed.io](https://www.sitespeed.io/) - A set of open source performance monitoring tools.
- [Calibre](https://calibreapp.com) - Web performance monitoring SaaS.
- [treo.sh](https://treo.sh/) - Web performance monitoring SaaS.
- [SpeedCurve](https://speedcurve.com/) - Web performance monitoring SaaS.

---

### Field Data (Real User Monitoring - RUM)

Collect performance data from real users visiting your page. Be mindful of the actual overhead, as it runs in your user's browser and watch out for browser support of more recent metrics (e.g. compared to your user-base).

- [Performance tracking with Google Analytics (GA)](https://philipwalton.com/articles/the-google-analytics-setup-i-use-on-every-site-i-build/#performance-tracking)
- [Chrome User Experience Report (CrUX)](https://developers.google.com/web/tools/chrome-user-experience-report/)
- [Load abandonment](https://developers.google.com/web/updates/2017/06/user-centric-performance-metrics#load_abandonment) - Track  `visibilitychange` to account for survivorship bias.
- [SpeedCurve LUX](https://speedcurve.com/features/lux/) - Real User Monitoring SaaS.
- [Akamai mPulse](https://www.akamai.com/uk/en/products/performance/mpulse-real-user-monitoring.jsp) - Real User Monitoring SaaS.
- [Sematext Experience](https://sematext.com/experience/) - Real User Monitoring SaaS.

### Critical rendering path

The critical rendering path is **everything that happens between receiving network bytes and rendering something on the screen**. To optimize any rendering metrics like [First Contentful Paint (FCP)](#first-contentful-paint-fcp) or [Speed Index](#speed-index) you have to understand how the critical rendering path works.

- [Critical rendering path](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/)

### Long tasks

The browser Main Thread that handles user input is also the one executing JavaScript (among many other things). Blocking the Main Thread for too long can make your page unresponsive.

A user perceives any visual change within 100ms as instant. Any task blocking the Main Thread by **taking longer than 50ms is considered a long task** (as it might make the browser unresponsive to user input).

To optimize interactivity metrics like [Time to Interactive (TTI)](#time-to-interactive-tti) and [First Input Delay (FID)](#first-input-delay-fid) you have to understand long tasks and how to avoid them as much as possible.

- [Spec - Long Tasks](https://w3c.github.io/longtasks/)
- [Blogpost - Tracking CPU with Long Tasks API](https://calendar.perfplanet.com/2017/tracking-cpu-with-long-tasks-api/)

### User-centric metrics

Users are typically looking for visual feedback and reassurance. To measure this perceived performance (at various stages of loading) we can choose metrics that directly answer the questions below.

- [User-centric Performance Metrics](https://developers.google.com/web/updates/2017/06/user-centric-performance-metrics)
- Is it happening? - Did the navigation start successfully? Has the server responded? (e.g [FCP](https://github.com/csabapalfi/awesome-web-performance-metrics/#first-contentful-paint-fcp))
- Is it useful/meaningful? - Has enough content rendered that users can engage with it? (e.g. [FMP](https://github.com/csabapalfi/awesome-web-performance-metrics/#first-meaningful-paint-fmp))
- Is it usable - Can users interact with the page, or is it still busy loading? (e.g [TTI](https://github.com/csabapalfi/awesome-web-performance-metrics/#time-to-interactive-tti))
- Is it delightful/smooth? - Are the interactions smooth and natural, free of lag and jank?

### Apdex score

Application Performance Index, or [Apdex](https://en.wikipedia.org/wiki/Apdex), is a measurement of your users’ level of satisfaction based on the response time of request(s) when interacting with your website or application. 

- [Apdex technical specification](http://www.apdex.org/index.php/category/specification/)
- [How to Use Apdex Score to Measure User Satisfaction](https://sematext.com/blog/how-to-use-your-apdex-score-to-measure-user-satisfaction/)

---

## Rendering metrics

### First Contentful Paint (FCP)

First Contentful Paint marks the time at which the **first text or image is painted** (including background images), non-white canvas or SVG. This includes text with pending webfonts. This is the first time users could start consuming page content.

- Lab: Lighthouse
- Field: Chrome 60+, Opera 47+, CrUX
- [Docs - FCP - Lighthouse](https://developers.google.com/web/tools/lighthouse/audits/first-contentful-paint)
- [Spec - FCP - W3C](https://w3c.github.io/paint-timing/)


### First Meaningful Paint (FMP)

First Meaningful Paint measures **when the primary content of a page is visible**. It's essentially the paint after which the biggest above-the-fold layout change has happened, and web fonts have loaded.

- Lab: Lighthouse
- Field: N/A
- [Docs - FMP - Lighthouse](https://developers.google.com/web/tools/lighthouse/audits/first-meaningful-paint)
- [Spec - First Meaningful Paint](https://docs.google.com/document/d/1BR94tJdZLsin5poeet0XoTW60M0SjvOJQttKT-JK8HI/view)

### Speed Index

Speed Index shows **how quickly the contents of a page are visibly populated** (lower numbers are better). This is done by frequently measuring visual completeness during loading. The quicker the page is more visually complete the lower the value.

- Lab: Lighthouse, WPT (but slightly different spec)
- Field: N/A
- [Docs - Speed Index - Lighthouse](https://developers.google.com/web/tools/lighthouse/audits/speed-index)
- [Docs - Speed Index - WPT](https://sites.google.com/a/webpagetest.org/docs/using-webpagetest/metrics/speed-index)
- [Talk - Speed Perception and Lighthouse](https://ldnwebperf.org/events/speed-perception-and-lighthouse/)


### Start render

The Start Render is the time from the start of the initial navigation until the **first non-white content is painted** to the browser display.

- Lab: WPT
- Field: N/A but similar to [First Paint (FP)](#first-paint-fp)
- [Docs - Start Render - WPT](https://sites.google.com/a/webpagetest.org/docs/using-webpagetest/metrics)


### First Paint (FP)

First Paint reports the time when **the browser first rendered after navigation**. This excludes the default background paint, but includes non-default background paint. This is the first key moment developers care about in page load – when the browser has started to render the page.

- Lab: LightHouse JSON report includes it but not the HTML report, also similar to [Start render](#start-render) in WPT
- Field: Chrome 60+, Opera 47+, CrUX
- [Spec - FP - W3C](https://w3c.github.io/paint-timing/)

### Visually Complete

The Visually Complete is the time from the start of the initial navigation until the **visible (above the fold) part of your page is no longer changing**. (Measured using a color histogram based on video/screenshots recording).

- Lab: WPT
- Field: N/A
- [Docs - Visually Complete - WPT](https://sites.google.com/a/webpagetest.org/docs/using-webpagetest/metrics/speed-index)

### Hero Element Timing

Hero Element Timing captures **when specific elements are painted** by the browser (e.g. your `h1` or your hero image, etc).

- Lab: WPT
- Field: N/A but see unmantained polyfill below
- [W3C GitHub issue - Element Timing API](https://github.com/w3c/charter-webperf/issues/30)
- [Spec - Hero Element Timing](https://docs.google.com/document/d/1yRYfYR1DnHtgwC4HRR04ipVVhT1h5gkI6yPmKCgJkyQ/edit#)
- [Blogpost - Hero Element Timing - SpeedCurve](https://speedcurve.com/blog/web-performance-monitoring-hero-times/)
- [Polyfill - Hero Element Timing](https://github.com/tdresser/hero-element-polyfill) - see also the [announcement here](https://groups.google.com/a/chromium.org/forum/m/#!topic/progressive-web-metrics/ND6JVZRWqqg)
- [Blogpost - User Timing for Element Timing - SpeedCurve](https://speedcurve.com/blog/user-timing-and-custom-metrics/)
- [Blogpost - Last Painted Hero coming to WebpageTest](https://speedcurve.com/blog/last-painted-hero/)
- [Docs - Element Timing Explainer](https://docs.google.com/document/d/1blFeMVdqxB0V3BAJh60ptOBFY7cJSXnf7VyW3wspbZ8/edit#heading=h.eny79fwwx642)
- [Docs - Hero Text Element Timestamps](https://docs.google.com/document/d/1co1yefZWQ4QvG_2WT0nCrqxcAgjU08um9Boe_JzHkdE/edit#heading=h.zwg1kfkhqmx)


### Cumulative Layout Shift (CLS)

A metric derived from the Layout Instability API. The cumulative layout shift (CLS) score is determined by calculating the sum of all unexpected (not within 0.5s of a user interaction) layout shift scores from page load until the page's lifecycle state changes to hidden.

- Lab: N/A
- Field: CrUX + Chrome 73+ (origin trial)
- [Spec - Layout Instability](https://github.com/WICG/layout-instability)
- [Chrome - Origin Trial for Layout Stability API](https://developers.chrome.com/origintrials/#/view_trial/1215971899390033921)
- [Blogpost - The Layout Instability API](https://web.dev/layout-instability-api/)

### Largest Contentful Paint (LCP)

- Lab: N/A
- Field: N/A (Chrome: in development)
- [Spec - Largest Contentful Paint](https://github.com/WICG/LargestContentfulPaint)
- [Docs - Largest Contentful Paint](https://docs.google.com/document/d/1ySnglZJiCbOrOMX8PNgE0mRKmt9vglNDyggE8oYN8gQ/edit#heading=h.hjlf1s5m20ko)
- [Blogpost - Largest Contentful Paint](https://web.dev/largest-contentful-paint/)

---

## Interactivity metrics

### First CPU Idle

First CPU Idle marks the **first time at which the page's main thread is quiet enough to handle user input**.

- Lab: Lighthouse, WPT (but it's called **First interactive** in WPT)
- Field: N/A
- [Docs - First Interactive - WPT](https://github.com/WPO-Foundation/webpagetest/blob/master/docs/Metrics/TimeToInteractive.md)
- [Docs - First CPU Idle - Lighthouse](https://developers.google.com/web/tools/lighthouse/audits/first-cpu-idle)

### Time to Interactive (TTI)

Time to interactive is **the time it takes for the page to become fully interactive** (as in Main Thread quiet for 5s). Not to confuse with First Interactive or First CPU Idle. (Warning: one of the most confusing and misunderstood metrics).

- Lab: Lighthouse, WPT (see [Consistently Interactive](#consistently-interactive))
- Field: Not recommended as users interacting with your page can skew field measurements of TTI
- [Polyfill - TTI](https://github.com/GoogleChromeLabs/tti-polyfill)
- [Spec - TTI - Lighthouse](https://docs.google.com/document/d/1GGiI9-7KeY3TPqS3YT271upUVimo-XiL5mwWorDUD4c/edit)
- [Blogpost - TTI](https://blog.dareboost.com/en/2019/05/measuring-interactivity-time-to-interactive/)

### First Input Delay (FID)

First Input Delay (FID) measures **the time from when a user first interacts with your site to the time when the browser is actually able to respond** to that interaction. An interaction can be when users click a link, tap on a button, or use a custom, JavaScript-powered control.

- Lab: N/A (as it requires the user to interact with the page)
- Field: IE9+ (and Safari, Chrome, Firefox) (with polyfill - 0.4KB)
- [Docs - FID](https://developers.google.com/web/updates/2018/05/first-input-delay)
- [Polyfill - FID](https://github.com/GoogleChromeLabs/first-input-delay)


### First Interactive

See [First CPU Idle](#first-cpu-idle). WPT still calls it First Interactive but Google/Lighthouse renamed to First CPU Idle to avoid confusing this with [Time to Interactive (TTI)](#time-to-interactive-tti)

### Consistently Interactive

See [Time to Interactive (TTI)](#time-to-interactive-tti). WPT still refers to TTI as Consistently Interactive but it's only available for Chrome and not surfaced on the UI (only in raw results XML/JSON).

### Estimated Input Latency

Estimated Input Latency is **an estimate of how long your app takes to respond to user input**, in milliseconds, during the busiest 5s window of page load. If your latency is higher than 50 ms, users may perceive your app as laggy. 

- Lab: Lighthouse
- Field: N/A
- [Docs - Estimated Input Latency - Lighthouse](https://developers.google.com/web/tools/lighthouse/audits/estimated-input-latency)

### Max Potential First Input Delay

The maximum potential [First Input Delay](#first-input-delay-fid) that your users could experience. Basically equals to the duration of the longest [long task](#long-tasks) on the browser Main Thread.

- Lab: Lighthouse
- Field: N/A

### Total Blocking Time (TBT)

- Lab: Lighthouse
- Field: N/A
- [Total Blocking Time](https://docs.google.com/document/d/1xCERB_X7PiP5RAZDwyIkODnIXoBk-Oo7Mi9266aEdGg/edit)

---

## Network metrics

Network timing field data can uncover a non-optimized TLS setup, slow DNS lookups or server side processing and issues with CDN configuration. See also a separate section about measuring [transferred bytes](#transferred-bytes).

- [Blogpost - Navigation and Resource Timing](https://developers.google.com/web/fundamentals/performance/navigation-and-resource-timing/)
- [Spec - Navigation Timing](https://www.w3.org/TR/navigation-timing-2/)
- [Spec - Resource Timing](https://www.w3.org/TR/resource-timing-2/)

### DNS latency

- Lab: DNS performance testing tools
- Field: IE9+, Safari 9+

```js
// Measuring DNS lookup time
var pageNav = performance.getEntriesByType("navigation")[0];
var dnsTime = pageNav.domainLookupEnd - pageNav.domainLookupStart;
```

### TCP and SSL/TLS latency

- Lab: See [Qualys SSL Labs](https://www.ssllabs.com/ssltest/index.html) for an audit
- Field: IE9+, Safari 9+

```js
// Quantifying total connection time
var pageNav = performance.getEntriesByType("navigation")[0];
var connectionTime = pageNav.connectEnd - pageNav.connectStart;
var tlsTime = 0; // <-- Assume 0 by default

// Did any TLS stuff happen?
if (pageNav.secureConnectionStart > 0) {
  // Awesome! Calculate it!
  tlsTime = pageNav.connectEnd - pageNav.secureConnectionStart;
}
```

### Time to First Byte (TTFB)

- Lab: most server load testing tools report this
- Field: IE9+, Safari 9+

```js
var ttfb = pageNav.responseStart - pageNav.requestStart;
```

### Transferred bytes

You can measure the byte weight of your assets with a number of tools. You would normally track these Lab only as the numbers are usually the same in the Field (but be mindful of device type or geographical location specific pages).

Measuring own (and third-party) JavaScript bytes is crucial as JavaScript is the main cause of high [TTI](#time-to-interactive-tti) or [FID](#first-input-delay-fid) values.

- Lab: Lighthouse (budgets), Sitespeed.io, custom tools
- Field: N/A - but numbers usually the same as in Lab
- [Sitespeed.io PageXray](https://www.sitespeed.io/documentation/pagexray/)
- [Lighthouse Performance Budgets](https://developers.google.com/web/tools/lighthouse/audits/budgets)
- [Can You Afford It?: Real-world Web Performance Budgets](https://infrequently.org/2017/10/can-you-afford-it-real-world-web-performance-budgets/)
- [Which third party scripts are most excessive](https://github.com/patrickhulce/third-party-web)

---

## Other metrics

### Google PageSpeed Insights score

- [About PageSpeed Insights](https://developers.google.com/speed/docs/insights/v5/about)
- [What's in the Google PageSpeed score](https://medium.com/expedia-group-tech/whats-in-the-google-pagespeed-score-a5fc93f91e91)
- [How Google Pagespeed works](https://calibreapp.com/blog/how-pagespeed-works/)


### User Timing

The User Timing API allows the developer to create application specific timestamps that are part of the browser's performance timeline. e.g. you can create a user timing mark to measure when your JS has loaded for a specific component on the page.

- Lab: Lighthouse, WPT
- Field: IE 10+, Safari 11+ (and Chrome, Firefox of course)
- [Spec - User Timing](https://www.w3.org/TR/user-timing/)

### Server Timing

Surface any backend server timing metrics (e.g. database latency, etc.) in the developer tools in the user's browser or in the PerformanceServerTiming interface.

- [Docs - Server Timing](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Server-Timing)


### Frame rate

 The frame rate is the **frequency at which the browser can display frames**. A frame represents the amount of work a browser does in one event loop iteration such as processing DOM events, resizing, scrolling, rendering, CSS animations, etc. A frame rate of 60 fps (frames per second) is a common target for a good responsive user experience. This means the browser should process a frame in about 16.7 ms.

- Lab: Chrome and FF Devtools
- Field: No browser implements the Frame Timing API yet but you can roll your own fps meter using `requestAnimationFrame`
- [Docs - Frame Timing API](https://developer.mozilla.org/en-US/docs/Web/API/Frame_Timing_API)
- [Docs - Chrome Devtools - FPS](https://developers.google.com/web/tools/chrome-devtools/evaluate-performance/#analyze_frames_per_second)
- [Docs - Firefox Developer Tools - Frame rate](https://developer.mozilla.org/en-US/docs/Tools/Performance/Frame_rate)

### DOMContentLoaded

- [Docs - `DOMContentLoaded`](https://developer.mozilla.org/en-US/docs/Web/Events/DOMContentLoaded)

### window.load

- [Docs - `window.load`](https://developer.mozilla.org/en-US/docs/Web/Events/load)

## License

[![CC0](http://mirrors.creativecommons.org/presskit/buttons/88x31/svg/cc-zero.svg)](https://creativecommons.org/publicdomain/zero/1.0/)

To the extent possible under law, Csaba Palfi has waived all copyright and related or neighboring rights to this work.

