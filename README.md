<!-- markdownlint-disable MD026 -->

# Awesome Web Performance Metrics

## 🤖 synthetic/lab testing tools

[WebpageTest.org](https://www.webpagetest.org/)
(also [WPO-Foundation/webpagetest](https://github.com/WPO-Foundation/webpagetest) on GitHub)

[Lighthouse](https://developers.google.com/web/tools/lighthouse/)
(also [GoogleChrome/lighthouse](https://github.com/GoogleChrome/lighthouse) on GitHub)

## 🍹 real user monitoring (RUM)

Web APIs/polyfills in the browser

## ☎️ 'classic' browser metrics

[Docs - `DOMContentLoaded`](https://developer.mozilla.org/en-US/docs/Web/Events/DOMContentLoaded)

[Docs - `load`](https://developer.mozilla.org/en-US/docs/Web/Events/load) or more specifically `window.load`

[Spec - Navigation Timing](https://www.w3.org/TR/navigation-timing-2/)

[Spec - Resource Timing](https://www.w3.org/TR/resource-timing-2/)

[Blogpost - Navigation and Resource Timing](https://developers.google.com/web/fundamentals/performance/navigation-and-resource-timing/)

no direct connection ux in itself 🙁

## 👫 user-centric metrics

the idea from [Leveraging the Performance Metrics that Most Affect User Experience](https://developers.google.com/web/updates/2017/06/user-centric-performance-metrics) by @philipwalton / Google

🔜 is it happening?

🤔 is it meaningful?

👆 is it usable?

🥃 is it smooth?

use these to organize/prioritize your metrics

## 🔜 happening? - first pixel on the screen?

[Definition - Start Render - webpagetest](https://sites.google.com/a/webpagetest.org/docs/using-webpagetest/metrics)

[Spec - Paint Timing](https://w3c.github.io/paint-timing/)

## 🤔 meaningful? - above the fold rendered?

[Definition - Visually Complete - webpagetest](https://sites.google.com/a/webpagetest.org/docs/using-webpagetest/metrics/speed-index) - this is on the Speed Index page of the docs

[Definition - First Meaningful Paint](https://developers.google.com/web/tools/lighthouse/audits/first-meaningful-paint)

[Spec - First Meaningful Paint](https://docs.google.com/document/d/1BR94tJdZLsin5poeet0XoTW60M0SjvOJQttKT-JK8HI/view)

## 🤔 meaningful? - speed index

[Definition - Perceptual Speed Index - Lighthouse](https://developers.google.com/web/tools/lighthouse/audits/speed-index)

[Definition - Speed Index - webpagetest](https://sites.google.com/a/webpagetest.org/docs/using-webpagetest/metrics/speed-index)

[Talk - Speed Perception and Lighthouse](https://ldnwebperf.org/events/speed-perception-and-lighthouse/) by @estelle - LdnWebPerf talk about Speed index

## 🤔 meaningful? - hero element timing

[W3C github issue - Element Timing API](https://github.com/w3c/charter-webperf/issues/30)

[Spec - Hero Element Timing](https://docs.google.com/document/d/1yRYfYR1DnHtgwC4HRR04ipVVhT1h5gkI6yPmKCgJkyQ/edit#)

[Blogpost - Hero Element Timing - SpeedCurve](https://speedcurve.com/blog/web-performance-monitoring-hero-times/)

[Polyfill - Hero Element Timing](https://github.com/tdresser/hero-element-polyfill) - see also the [announcement here](https://groups.google.com/a/chromium.org/forum/m/#!topic/progressive-web-metrics/ND6JVZRWqqg)

[Blogpost - Last Painted Hero coming to WebpageTest](https://speedcurve.com/blog/last-painted-hero/)

[Spec - Hero Text Element Timing](https://docs.google.com/document/d/1sBM5lzDPws2mg1wRKiwM0TGFv9WqI6gEdF7vYhBYqUg/edit#heading=h.eny79fwwx642)

[Spec - Hero Text Element Timestamps](https://docs.google.com/document/d/1co1yefZWQ4QvG_2WT0nCrqxcAgjU08um9Boe_JzHkdE/edit#heading=h.zwg1kfkhqmx)

## 👆 usable? - JS loaded?

[Spec - User Timing](https://www.w3.org/TR/user-timing/)

```js
componentDidMount() {
    performance.mark("yourcomponent.usable");
}
```

## 👆 usable? - first interactive (time to interactive)

[Definition - Time to Interactie - webpagetest](https://github.com/WPO-Foundation/webpagetest/blob/master/docs/Metrics/TimeToInteractive.md)

[Definition - First Interactive - Lighthouse](https://developers.google.com/web/tools/lighthouse/audits/first-interactive)

[Spec - First Interactive - Lighthouse](https://docs.google.com/document/d/1GGiI9-7KeY3TPqS3YT271upUVimo-XiL5mwWorDUD4c/edit)

[Spec - Long Tasks](https://w3c.github.io/longtasks/)

[Polyfill - First Interactive](https://github.com/GoogleChromeLabs/tti-polyfill)

## 👆 usable? - input delay

[Definition - Estimated Input Latency - Lighthouse](https://developers.google.com/web/tools/lighthouse/audits/estimated-input-latency)

[Polyfill - First Input Delay](https://github.com/GoogleChromeLabs/first-input-delay)

## 🥃 smooth? - frame rate

[Docs - Chrome Devtools - FPS](https://developers.google.com/web/tools/chrome-devtools/evaluate-performance/#analyze_frames_per_second)

[Docs - Firefox Developer Tools - Frame rate](https://developer.mozilla.org/en-US/docs/Tools/Performance/Frame_rate)

## 😵 load abandonment

[Example - tracking `visibilitychange`](https://developers.google.com/web/updates/2017/06/user-centric-performance-metrics#load_abandonment)

[Spec - Page Visibility](https://www.w3.org/TR/page-visibility-2/)
