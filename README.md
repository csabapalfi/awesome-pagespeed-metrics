<!-- markdownlint-disable MD026 -->

# Awesome Web Performance Metrics

- [Lab data (Synthetic measurements)](#lab-data-synthetic-measurements)
  * [Google Lighthouse (LH)](#google-lighthouse-lh)
  * [WebpageTest (WPT)](#webpagetest-wpt)
  * [Sitespeed.io](#sitespeedio)
- [Field data (Real User Monitoring - RUM)](#field-data-real-user-monitoring---rum)
- [User-centric metrics](#user-centric-metrics)
- [Is it happening?](#is-it-happening)
  * [Start render](#start-render)
  * [First Contentful Paint (FCP)](#first-contentful-paint-fcp)
- [Is it useful/meaningful?](#is-it-usefulmeaningful)
  * [Visually Complete](#visually-complete)
  * [First Meaningful Paint (FMP)](#first-meaningful-paint-fmp)
  * [Speed Index](#speed-index)
  * [Hero Element Timing](#hero-element-timing)
- [Is it usable?](#is-it-usable)
  * [User Timing marks](#user-timing-marks)
  * [First CPU Idle](#first-cpu-idle)
  * [Time to Interactive (TTI, Consistently Interactive)](#time-to-interactive-tti-consistently-interactive)
  * [First Interactive](#first-interactive)
  * [Estimated Input Latency](#estimated-input-latency)
  * [First Input Delay (FID)](#first-input-delay-fid)
- [Is it delightful/smooth?](#is-it-delightfulsmooth)
  * [Frame rate](#frame-rate)
- [Page lifecycle](#page-lifecycle)
  * [DOMContentLoaded](#domcontentloaded)
  * [window.load](#windowload)
  * [Load abandonment](#load-abandonment)
- [Network timing](#network-timing)
  * [Navigation Timing](#navigation-timing)
  * [Resource Timing](#resource-timing)
  * [Server Timing](#server-timing)
- [Resource byte weights (TODO)](#resource-byte-weights-todo)
  * [Initial HTML weight](#initial-html-weight)
  * [JavaScript weight](#javascript-weight)
- [Concepts (TODO)](#concepts-todo)
  * [Critical rendering path](#critical-rendering-path)
  * [The Main Thread and Long tasks](#the-main-thread-and-long-tasks)

## Lab data (Synthetic measurements)

Make a request to your page with a tool and evaluate performance.

### Google Lighthouse (LH)

Lighthouse is a tool built on Chrome to audit web pages. You can run it from Chrome DevTools, a Chrome Extension or from the command line (even with headless Chrome).

* [Docs - Lighthouse](https://developers.google.com/web/tools/lighthouse/#devtools)
* Tools built on LH:
    * [Tool - Google PageSpeed Insights](https://developers.google.com/speed/pagespeed/insights/)
    * [Tool - web.dev/measure](https://web.dev/measure)

### WebpageTest (WPT)


* [Docs - WebpageTest (WPT)](https://sites.google.com/a/webpagetest.org/docs/using-webpagetest/quick-start-quide) and tools built on top of it
* Some tools were originally built on WPT (and now support LH as well):
    * [Tool - SpeedCurve](https://speedcurve.com/)
    * [Tool - Calibre](https://calibreapp.com)

### Sitespeed.io

Sitespeed.io is a set of Open Source tools that makes it easy to monitor and measure the performance of your web site.

* [Tool - Sitespeed.io](https://www.sitespeed.io/)

---

## Field data (Real User Monitoring - RUM)

Collect performance data from real users visiting your page.

* [Docs - Chrome User Experience Report (CrUX)](https://developers.google.com/web/tools/chrome-user-experience-report/)
* [Blogpost - Performance tracking Google Analytics (GA)](https://philipwalton.com/articles/the-google-analytics-setup-i-use-on-every-site-i-build/#performance-tracking)
* Your own analytics

---

## User-centric metrics

[Blogpost - User-centric Performance Metrics](https://developers.google.com/web/updates/2017/06/user-centric-performance-metrics)

Use the questions below to organize/prioritize your metrics from the user's perspective.

* [Is it happening?](#is-it-happening)
* [Is it useful/meaningful?](#is-it-usefulmeaningful)
* [Is it usable?](#is-it-usable)
* [Is it delightful/smooth?](#is-it-delightfulsmooth)

---

## Is it happening?

* Did the navigation start successfully? 
* Has the server responded?

### Start render

The Start Render time is measured as the time from the start of the initial navigation until the first non-white content is painted to the browser display.

* Browser support: N/A
* [Docs - Start Render - WPT](https://sites.google.com/a/webpagetest.org/docs/using-webpagetest/metrics)


### First Contentful Paint (FCP)

First Contentful Paint marks the time at which the first text or image is painted.

* Browser support: Chrome 60+, Opera 47+
* [Docs - FCP - LH](https://developers.google.com/web/tools/lighthouse/audits/first-contentful-paint)
* [Spec - FCP - W3C](https://w3c.github.io/paint-timing/)

---

## Is it useful/meaningful?	
* Has enough content rendered that users can engage with it?

### Visually Complete

* Browser support: N/A
* [Docs - Visually Complete - WPT](https://sites.google.com/a/webpagetest.org/docs/using-webpagetest/metrics/speed-index)


### First Meaningful Paint (FMP)

First Meaningful Paint measures when the primary content of a page is visible. It's essentially the paint after which the biggest above-the-fold layout change has happened, and web fonts have loaded.

* Browser support: N/A
* [Docs - FMP - LH](https://developers.google.com/web/tools/lighthouse/audits/first-meaningful-paint)
* [Spec - First Meaningful Paint](https://docs.google.com/document/d/1BR94tJdZLsin5poeet0XoTW60M0SjvOJQttKT-JK8HI/view)

### Speed Index

Speed Index shows how quickly the contents of a page are visibly populated.

* Browser support: N/A
* [Docs - Speed Index - LH](https://developers.google.com/web/tools/lighthouse/audits/speed-index)
* [Docs - Speed Index - WPT](https://sites.google.com/a/webpagetest.org/docs/using-webpagetest/metrics/speed-index)
* [Talk - Speed Perception and Lighthouse](https://ldnwebperf.org/events/speed-perception-and-lighthouse/)

### Hero Element Timing

> TODO: summary + cleanup links

* [W3C github issue - Element Timing API](https://github.com/w3c/charter-webperf/issues/30)
* [Spec - Hero Element Timing](https://docs.google.com/document/d/1yRYfYR1DnHtgwC4HRR04ipVVhT1h5gkI6yPmKCgJkyQ/edit#)
* [Blogpost - Hero Element Timing - SpeedCurve](https://speedcurve.com/blog/web-performance-monitoring-hero-times/)
* [Polyfill - Hero Element Timing](https://github.com/tdresser/hero-element-polyfill) - see also the [announcement here](https://groups.google.com/a/chromium.org/forum/m/#!topic/progressive-web-metrics/ND6JVZRWqqg)
* [Blogpost - Last Painted Hero coming to WebpageTest](https://speedcurve.com/blog/last-painted-hero/)
* [Spec - Hero Text Element Timing](https://docs.google.com/document/d/1sBM5lzDPws2mg1wRKiwM0TGFv9WqI6gEdF7vYhBYqUg/edit#heading=h.eny79fwwx642)
* [Spec - Hero Text Element Timestamps](https://docs.google.com/document/d/1co1yefZWQ4QvG_2WT0nCrqxcAgjU08um9Boe_JzHkdE/edit#heading=h.zwg1kfkhqmx)

---

## Is it usable?
* Can users interact with the page, or is it still busy loading?

### User Timing marks

[Spec - User Timing](https://www.w3.org/TR/user-timing/)

```js
componentDidMount() {
    performance.mark("yourcomponent.usable");
}
```

### First CPU Idle

> TODO cleanup/reorg all TTI links

First CPU Idle marks the first time at which the page's main thread is quiet enough to handle input.

### Time to Interactive (TTI, Consistently Interactive)

Time to interactive is the amount of time it takes for the page to become fully interactive.

a.k.a Consistently Interactive

### First Interactive

[Definition - Time to Interactie - webpagetest](https://github.com/WPO-Foundation/webpagetest/blob/master/docs/Metrics/TimeToInteractive.md)

[Definition - First Interactive - Lighthouse](https://developers.google.com/web/tools/lighthouse/audits/first-interactive)

[Spec - First Interactive - Lighthouse](https://docs.google.com/document/d/1GGiI9-7KeY3TPqS3YT271upUVimo-XiL5mwWorDUD4c/edit)

[Spec - Long Tasks](https://w3c.github.io/longtasks/)

[Polyfill - First Interactive](https://github.com/GoogleChromeLabs/tti-polyfill)

### Estimated Input Latency

Estimated Input Latency is an estimate of how long your app takes to respond to user input, in milliseconds, during the busiest 5s window of page load. If your latency is higher than 50 ms, users may perceive your app as laggy. 

* [Docs - Estimated Input Latency - LH](https://developers.google.com/web/tools/lighthouse/audits/estimated-input-latency)

### First Input Delay (FID)

* Browser support: IE9+ (with polyfill - 0.4KB)
* [Polyfill - First Input Delay](https://github.com/GoogleChromeLabs/first-input-delay)

---

## Is it delightful/smooth?	
* Are the interactions smooth and natural, free of lag and jank?

### Frame rate

[Docs - Chrome Devtools - FPS](https://developers.google.com/web/tools/chrome-devtools/evaluate-performance/#analyze_frames_per_second)

[Docs - Firefox Developer Tools - Frame rate](https://developer.mozilla.org/en-US/docs/Tools/Performance/Frame_rate)

---

## Page lifecycle

### DOMContentLoaded

[Docs - `DOMContentLoaded`](https://developer.mozilla.org/en-US/docs/Web/Events/DOMContentLoaded)

### window.load

[Docs - `load`](https://developer.mozilla.org/en-US/docs/Web/Events/load) or more specifically `window.load`

### Load abandonment

[Example - tracking `visibilitychange`](https://developers.google.com/web/updates/2017/06/user-centric-performance-metrics#load_abandonment)

[Spec - Page Visibility](https://www.w3.org/TR/page-visibility-2/)

---

## Network timing

[Blogpost - Navigation and Resource Timing](https://developers.google.com/web/fundamentals/performance/navigation-and-resource-timing/)

### Navigation Timing

[Spec - Navigation Timing](https://www.w3.org/TR/navigation-timing-2/)

### Resource Timing

[Spec - Resource Timing](https://www.w3.org/TR/resource-timing-2/)

### Server Timing

Surface any backend server timing metrics (e.g. database latency, etc.) in the developer tools in the user's browser or in the PerformanceServerTiming interface.

[Docs - Server Timing](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Server-Timing)

---

## Resource byte weights (TODO)

### Initial HTML weight

### JavaScript weight

---

## Concepts (TODO)

### Critical rendering path

### The Main Thread and Long tasks