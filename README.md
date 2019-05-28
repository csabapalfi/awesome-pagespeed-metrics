<!-- markdownlint-disable MD026 -->

# Awesome Web Performance Metrics

- [Collecting metrics](#collecting-metrics)
  * [Lab data (Synthetic measurements)](#lab-data-synthetic-measurements)
    + [Google Lighthouse (LH)](#google-lighthouse-lh)
    + [WebpageTest (WPT)](#webpagetest-wpt)
    + [Sitespeed.io](#sitespeedio)
  * [Field data (Real User Monitoring - RUM)](#field-data-real-user-monitoring---rum)
    + [Your web analytics](#your-web-analytics)
    + [Chrome User Experience Report (CrUX)](#chrome-user-experience-report-crux)
- [Recommended metrics](#recommended-metrics)
  * [Rendering](#rendering)
    + [First Contentful Paint (FCP)](#first-contentful-paint-fcp)
    + [First Meaningful Paint (FMP)](#first-meaningful-paint-fmp)
    + [Speed Index](#speed-index)
  * [Interactivity](#interactivity)
    + [First CPU Idle](#first-cpu-idle)
    + [Time to Interactive (TTI)](#time-to-interactive-tti)
    + [First Input Delay (FID)](#first-input-delay-fid)
  * [Byte Weight](#byte-weight)
    + [JavaScript bytes (incl third-parties)](#javascript-bytes-incl-third-parties)
    + [Initial document bytes](#initial-document-bytes)
  * [Network Timing](#network-timing)
    + [DNS](#dns)
    + [TCP and TLS](#tcp-and-tls)
    + [TTFB](#ttfb)
- [Concepts](#concepts)
  * [Critical rendering path](#critical-rendering-path)
  * [Long tasks](#long-tasks)
  * [User-centric metrics](#user-centric-metrics)
    + [Is it happening?](#is-it-happening)
    + [Is it useful/meaningful?](#is-it-usefulmeaningful)
    + [Is it usable?](#is-it-usable)
    + [Is it delightful/smooth?](#is-it-delightfulsmooth)
- [Other metrics](#other-metrics)
  * [Start render](#start-render)
  * [First Paint (FP)](#first-paint-fp)
  * [Visually Complete](#visually-complete)
  * [Hero Element Timing](#hero-element-timing)
  * [First Interactive](#first-interactive)
  * [Consistently Interactive](#consistently-interactive)
  * [Estimated Input Latency](#estimated-input-latency)
  * [User Timing mark when JS loaded](#user-timing-mark-when-js-loaded)
  * [DOMContentLoaded](#domcontentloaded)
  * [window.load](#windowload)
  * [Frame rate](#frame-rate)
  * [Server Timing](#server-timing)
  * [Effective Connection Type](#effective-connection-type)
  * [Layout Instability](#layout-instability)
  * [Largest Conentful Paint](#largest-conentful-paint)

## Collecting metrics

### Lab data (Synthetic measurements)

Make a request to your page with a tool and evaluate performance.

* **Make it realistic** (e.g. by throttling network and CPU)
* **Reduce noise** (e.g. by running multiple times)

#### Google Lighthouse (LH)

Lighthouse is a tool **built on Google Chrome** to audit web pages. You can run it from Chrome DevTools, a Chrome Extension or from the command line (even with headless Chrome).

* [Docs - Lighthouse](https://developers.google.com/web/tools/lighthouse/#devtools)
* Tools built on LH:
    * [Google PageSpeed Insights](https://developers.google.com/speed/pagespeed/insights/)
    * [Calibre](https://calibreapp.com)
    * [treo.sh](https://treo.sh/)
    * and [lots more](https://github.com/GoogleChrome/lighthouse/#lighthouse-integrations)

#### WebpageTest (WPT)

WebpageTest is an open source project to test web page performance. It **supports multiple browsers**, testing on real devices and has a free hosted version at [webpagetest.org](https://www.webpagetest.org/)

* [Docs - WebpageTest (WPT)](https://sites.google.com/a/webpagetest.org/docs/using-webpagetest/quick-start-quide)
* Some tools were originally built on WPT (and now support LH as well):
    * [SpeedCurve](https://speedcurve.com/)


#### Sitespeed.io

Sitespeed.io is a set of Open Source tools to monitor and measure the performance of your web site.

* [Sitespeed.io](https://www.sitespeed.io/)

---

### Field data (Real User Monitoring - RUM)

Collect performance data from real users visiting your page.

* Be mindful of the actual **overhead**, as it runs in your user's browser.
* Consider **browser support** of more recent metrics (e.g. compared to your user-base)
* Track load abandonment by [tracking `visibilitychange`](https://developers.google.com/web/updates/2017/06/user-centric-performance-metrics#load_abandonment) to account for survivorship bias

#### Your web analytics

* Web analytics tracking can also be used to track performance
* [Blogpost - Performance tracking with Google Analytics (GA)](https://philipwalton.com/articles/the-google-analytics-setup-i-use-on-every-site-i-build/#performance-tracking)

#### Chrome User Experience Report (CrUX)

The Chrome User Experience Report provides user experience metrics for how real-world Chrome users experience popular destinations on the web. Available as a Google BigQuery dataset.

* [Docs - CrUX](https://developers.google.com/web/tools/chrome-user-experience-report/)

---

## Recommended metrics

### Rendering

#### First Contentful Paint (FCP)

First Contentful Paint marks the time at which the **first text or image is painted** (including background images), non-white canvas or SVG. This includes text with pending webfonts. This is the first time users could start consuming page content.

* Lab: Lighthouse
* Field: Chrome 60+, Opera 47+, CrUX
* [Docs - FCP - LH](https://developers.google.com/web/tools/lighthouse/audits/first-contentful-paint)
* [Spec - FCP - W3C](https://w3c.github.io/paint-timing/)


#### First Meaningful Paint (FMP)

First Meaningful Paint measures **when the primary content of a page is visible**. It's essentially the paint after which the biggest above-the-fold layout change has happened, and web fonts have loaded.

* Lab: Lighthouse
* Field: N/A
* [Docs - FMP - LH](https://developers.google.com/web/tools/lighthouse/audits/first-meaningful-paint)
* [Spec - First Meaningful Paint](https://docs.google.com/document/d/1BR94tJdZLsin5poeet0XoTW60M0SjvOJQttKT-JK8HI/view)

#### Speed Index

Speed Index shows **how quickly the contents of a page are visibly populated** (lower numbers are better). This is done by frequently measuring visual completeness during loading. The quicker the page is more visually complete the lower the value.

* Lab: Lighthouse, WPT (but slightly different spec)
* Field: N/A
* [Docs - Speed Index - LH](https://developers.google.com/web/tools/lighthouse/audits/speed-index)
* [Docs - Speed Index - WPT](https://sites.google.com/a/webpagetest.org/docs/using-webpagetest/metrics/speed-index)
* [Talk - Speed Perception and Lighthouse](https://ldnwebperf.org/events/speed-perception-and-lighthouse/)

### Interactivity

#### First CPU Idle

First CPU Idle marks the **first time at which the page's main thread is quiet enough to handle user input**.

* Lab: Lighthouse, WPT (but it's called **First interactive** in WPT)
* Field: N/A
* [Docs - First Interactive - WPT](https://github.com/WPO-Foundation/webpagetest/blob/master/docs/Metrics/TimeToInteractive.md)
* [Docs - First CPU Idle - Lighthouse](https://developers.google.com/web/tools/lighthouse/audits/first-cpu-idle)

#### Time to Interactive (TTI)

Time to interactive is **the time it takes for the page to become fully interactive.** Not to confuse with First Interactive or First CPU Idle. (TODO better definition, this is the most often misunderstood metric - e.g. how 'interactive' is defined)

* Lab: Lighthouse, WPT (it's called Consistently interactive in WPT, also only in Chrome even in WPT and not shown on the UI at all)
* Field: Chrome 58+ with polyfill (BUT note that users interacting with your page can skew field measurements of TTI)
* [Polyfill - TTI](https://github.com/GoogleChromeLabs/tti-polyfill)
* [Spec - TTI - LH](https://docs.google.com/document/d/1GGiI9-7KeY3TPqS3YT271upUVimo-XiL5mwWorDUD4c/edit)

#### First Input Delay (FID)

First Input Delay (FID) measures **the time from when a user first interacts with your site to the time when the browser is actually able to respond** to that interaction. An interaction can be when users click a link, tap on a button, or use a custom, JavaScript-powered control.

* Lab: N/A (as it requires the user to interact with the page)
* Field: IE9+ (and Safari, Chrome, Firefox) (with polyfill - 0.4KB)
* [Docs - FID](https://developers.google.com/web/updates/2018/05/first-input-delay)
* [Polyfill - FID](https://github.com/GoogleChromeLabs/first-input-delay)

---

### Byte Weight

You can measure the byte weight of your assets with a number of tools. You would normally track these Lab only as the numbers are usually the same in the Field (but be mindful of device type or geographical location specific pages).

* Lab: LH (custom audit), Sitespeed.io, custom tools
* Field: N/A - but numbers usually the same as in Lab
* [Sitespeed.io PageXray](https://www.sitespeed.io/documentation/pagexray/)
* [page-weight cli](https://www.sitespeed.io/documentation/pagexray/) - splits first-party and third-party
* [byte-weight-breakdown - LH custom audit](https://github.com/csabapalfi/byte-weight-breakdown)
* manually look at Chrome DevTools Network Tab

#### JavaScript bytes (incl third-parties)

Measure and keep track of the compressed (and uncompressed) byte weight of your own JS bundles and all thirdparty JS loaded on your page. Third parties can be analytics, marketing tags, customer support chat widget, etc.

Loading lots of JavaScript is usually the root cause of high [TTI](#time-to-interactive-tti-) or [FID](#first-input-delay-fid-) values.

* [Can You Afford It?: Real-world Web Performance Budgets](https://infrequently.org/2017/10/can-you-afford-it-real-world-web-performance-budgets/)
* [Which third party scripts are most excessive](https://github.com/patrickhulce/third-party-web)

#### Initial document bytes

Your initial HTML document is alway number one on your critical rendering path. Be sure not to excessively embed resources like SVGs or large amount JS or CSS. (Some critical CSS or JS is ok, the key here is how much).

* [Is your HTML bloated? A flamegraph can tell you why](https://medium.com/@csabapalfi/is-your-html-bloated-a-flamegraph-can-tell-you-why-e60e4313583c)

---

### Network Timing

When you try to optimize rendering metrics it's crucial to make sure that initial connection setup and your server response time is as fast as possible. 

Network timing field data can uncover a non-optimized TLS setup, slow DNS lookups or server side processing and issues with CDN configuration.

* Lab: e.g. Chrome Devtools but this is usually a Field metric
* Field: IE9+, (TODO confirm Safari support as it's reported differently by MDN and caniuse.com)
* [Blogpost - Navigation and Resource Timing](https://developers.google.com/web/fundamentals/performance/navigation-and-resource-timing/)
* [Spec - Navigation Timing](https://www.w3.org/TR/navigation-timing-2/)
* [Spec - Resource Timing](https://www.w3.org/TR/resource-timing-2/)

#### DNS

```js
// Measuring DNS lookup time
var pageNav = performance.getEntriesByType("navigation")[0];
var dnsTime = pageNav.domainLookupEnd - pageNav.domainLookupStart;
```

#### TCP and TLS

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

#### TTFB

```js
// Time to First Byte (TTFB)
var ttfb = pageNav.responseStart - pageNav.requestEnd;
```

---

## Concepts


### Critical rendering path

The critical rendering path is **everything that happens between receiving network bytes and rendering something on the screen**. To optimize any rendering metrics like [First Contentful Paint (FCP)](#first-contentful-paint-fcp) or [Speed Index](#speed-index) you have to understand how the critical rendering path works.

* [Critical rendering path](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/)

### Long tasks

The browser Main Thread that handles user input is also the one executing JavaScript (among many other things). Blocking the Main Thread for too long can make your page unresponsive.

A user perceives any visual change within 100ms as instant. Any task blocking the Main Thread by **taking longer than 50ms is considered a long task** (as it might make the browser unresponsive to user input).

To optimize interactivity metrics like [Time to Interactive (TTI)](#time-to-interactive-tti) and [First Input Delay (FID)](#first-input-delay-fid) you have to understand long tasks and how to avoid them as much as possible.

* [Spec - Long Tasks](https://w3c.github.io/longtasks/)
* [Blogpost - Tracking CPU with Long Tasks API](https://calendar.perfplanet.com/2017/tracking-cpu-with-long-tasks-api/)

### User-centric metrics

[Blogpost - User-centric Performance Metrics](https://developers.google.com/web/updates/2017/06/user-centric-performance-metrics)

Use the questions below to organize/prioritize your metrics from the user's perspective.

#### Is it happening?

> Did the navigation start successfully? Has the server responded?

* [First Contentful Paint (FCP)](#first-contentful-paint-fcp)

#### Is it useful/meaningful?
> Has enough content rendered that users can engage with it?

* [First Meaningful Paint (FMP)](#first-meaningful-paint-fmp)
* [Speed Index](#speed-index)
* [Hero Element Timing](#hero-element-timing)


#### Is it usable?
> Can users interact with the page, or is it still busy loading?

* [User Timing mark when JS loaded](#user-timing-mark-when-js-loaded)
* [First CPU Idle](#first-cpu-idle)
* [Time to Interactive (TTI)](#time-to-interactive-tti)
* [First Input Delay (FID)](#first-input-delay-fid)
* [Estimated Input Latency](#estimated-input-latency)

#### Is it delightful/smooth?	
> Are the interactions smooth and natural, free of lag and jank?

* [Frame rate](#frame-rate)

---

## Other metrics

### Start render

The Start Render is the time from the start of the initial navigation until the **first non-white content is painted** to the browser display.

* Lab: WPT
* Field: N/A but similar to [First Paint (FP)](#first-paint-fp)
* [Docs - Start Render - WPT](https://sites.google.com/a/webpagetest.org/docs/using-webpagetest/metrics)


### First Paint (FP)

First Paint reports the time when **the browser first rendered after navigation**. This excludes the default background paint, but includes non-default background paint. This is the first key moment developers care about in page load – when the browser has started to render the page.

* Lab: LightHouse JSON report includes it but not the HTML report, also similar to [Start render](#start-render) in WPT
* Field: Chrome 60+, Opera 47+, CrUX
* [Spec - FP - W3C](https://w3c.github.io/paint-timing/)

### Visually Complete

The Visually Complete is the time from the start of the initial navigation until the **visible (above the fold) part of your page is no longer changing**. (Measured using a color histogram based on video/screenshots recording).

* Lab: WPT
* Field: N/A
* [Docs - Visually Complete - WPT](https://sites.google.com/a/webpagetest.org/docs/using-webpagetest/metrics/speed-index)

### Hero Element Timing

Hero Element Timing captures **when specific elements are painted** by the browser (e.g. your `h1` or your hero image, etc).

* Lab: WPT
* Field: N/A but see unmantained polyfill below
* [W3C github issue - Element Timing API](https://github.com/w3c/charter-webperf/issues/30)
* [Spec - Hero Element Timing](https://docs.google.com/document/d/1yRYfYR1DnHtgwC4HRR04ipVVhT1h5gkI6yPmKCgJkyQ/edit#)
* [Blogpost - Hero Element Timing - SpeedCurve](https://speedcurve.com/blog/web-performance-monitoring-hero-times/)
* [Polyfill - Hero Element Timing](https://github.com/tdresser/hero-element-polyfill) - see also the [announcement here](https://groups.google.com/a/chromium.org/forum/m/#!topic/progressive-web-metrics/ND6JVZRWqqg)
* [Blogpost - User Timing for Element Timing - SpeedCurve](https://speedcurve.com/blog/user-timing-and-custom-metrics/)
* [Blogpost - Last Painted Hero coming to WebpageTest](https://speedcurve.com/blog/last-painted-hero/)
* [Docs - Element Timing Explainer](https://docs.google.com/document/d/1blFeMVdqxB0V3BAJh60ptOBFY7cJSXnf7VyW3wspbZ8/edit#heading=h.eny79fwwx642)
* [Docs - Hero Text Element Timestamps](https://docs.google.com/document/d/1co1yefZWQ4QvG_2WT0nCrqxcAgjU08um9Boe_JzHkdE/edit#heading=h.zwg1kfkhqmx)

### First Interactive

See [First CPU Idle](#first-cpu-idle). WPT still calls it First Interactive but Google/Lighthouse renamed to First CPU Idle to avoid confusing this with [Time to Interactive (TTI)](#time-to-interactive-tti)

### Consistently Interactive

See [Time to Interactive (TTI)](#time-to-interactive-tti). WPT still refers to TTI as Consistently Interactive but it's only available for Chrome and not surfaced on the UI (only in raw results XML/JSON).

### Estimated Input Latency

Estimated Input Latency is **an estimate of how long your app takes to respond to user input**, in milliseconds, during the busiest 5s window of page load. If your latency is higher than 50 ms, users may perceive your app as laggy. 

* Lab: LH
* Field: N/A
* [Docs - Estimated Input Latency - LH](https://developers.google.com/web/tools/lighthouse/audits/estimated-input-latency)

### User Timing mark when JS loaded

The User Timing API allows the developer to create application specific timestamps that are part of the browser's performance timeline. You can **create a user timing mark to measure when your JS has loaded** (e.g. for a specific component).

* Lab: LH, WPT
* Field: IE 10+, Safari 11+ (and Chrome, Firefox of course)
* [Spec - User Timing](https://www.w3.org/TR/user-timing/)

```js
componentDidMount() {
    performance.mark("yourcomponent.usable");
}
```

### DOMContentLoaded

* [Docs - `DOMContentLoaded`](https://developer.mozilla.org/en-US/docs/Web/Events/DOMContentLoaded)

### window.load

* [Docs - `load`](https://developer.mozilla.org/en-US/docs/Web/Events/load) or more specifically `window.load`

### Frame rate

 The frame rate is the **frequency at which the browser can display frames**. A frame represents the amount of work a browser does in one event loop iteration such as processing DOM events, resizing, scrolling, rendering, CSS animations, etc. A frame rate of 60 fps (frames per second) is a common target for a good responsive user experience. This means the browser should process a frame in about 16.7 ms.

* Lab: Chrome and FF Devtools
* Field: No browser implements the Frame Timing API yet but you can roll your own fps meter using `requestAnimationFrame`
* [Docs - Frame Timing API](https://developer.mozilla.org/en-US/docs/Web/API/Frame_Timing_API)
* [Docs - Chrome Devtools - FPS](https://developers.google.com/web/tools/chrome-devtools/evaluate-performance/#analyze_frames_per_second)
* [Docs - Firefox Developer Tools - Frame rate](https://developer.mozilla.org/en-US/docs/Tools/Performance/Frame_rate)

### Server Timing

Surface any backend server timing metrics (e.g. database latency, etc.) in the developer tools in the user's browser or in the PerformanceServerTiming interface.

* [Docs - Server Timing](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Server-Timing)


### Effective Connection Type

* [Network Information API](https://developer.mozilla.org/en-US/docs/Web/API/Network_Information_API)

### Layout Instability

* Lab: N/A
* Field: Chrome 73+ (origin trial)
* [Docs - Layout Instability](https://github.com/ehanley324/layout-instability/blob/master/explainer.md)
* [Chrome - Origin Trial for Layout Stability API](https://developers.chrome.com/origintrials/#/view_trial/1215971899390033921)

### Largest Conentful Paint

* Lab: N/A
* Field N/A (Chrome: in development)
* [Docs - Largest Contentful Paint](https://docs.google.com/document/d/1ySnglZJiCbOrOMX8PNgE0mRKmt9vglNDyggE8oYN8gQ/edit#heading=h.hjlf1s5m20ko)