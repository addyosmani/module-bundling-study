## Module bundling study

This repo includes raw results from a study conducted on the time to interactivity of a large set (130-160) 
of production React apps. These apps are generally bundled using Webpack 1 or Webpack 2. 

## How is Time to Interactive measured?

[Lighthouse](https://github.com/googlechrome/lighthouse) currently considers TTI as the moment after DOMContentLoaded 
where the main thread is available enough to handle user input. It looks for the first 500ms window where estimated 
Input Latency is <50ms at the 90% percentile.

## Test environment

A runner was built on top of Lighthouse for taking the results of a React.js JavaScript bundling survey, running 
multiple audit runs against these URLs and generating a set of averages and medians. This runner is not yet OSS, but
is trivial to replicate (iterate over CSV, run Lighthouse, store results). 

Conditions for testing:

* Nexus 5X (Lighthouse over remote debugging)
* Both emulated 3G and harsh (packet-loss) 3G
* For throttled 3G: 
  * Latency: 150ms RTT, downloadThroughput: 1.60
  * 1.6ms download throughput (similar to WebPageTest's 3G preset)
* Native CPU and throttled CPU

## Why don't the Lighthouse runs include the URLs field?

The point of this study is to highlight trends rather than point any site out for having a slow TTI. For this reason,
files starting with `lighthouse-*` or `web-page-test` have had their URL field filtered out. This allows us to focus 
on TTI scores, medians, averages whilst not going witch-hunting :)

That said, it's important to point out the data in this study was not made up. URLs for apps tested can be found in 
unfiltered/cleaned form in `raw-survey-results.csv` should you wish to run your own study and reach your own conclusions.

## License

Released under an Apache-2.0 license.