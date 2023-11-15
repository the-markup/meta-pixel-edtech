# Data for “Facebook Tracks Kids Before They’re Old Enough to Make an Account”

This contains the data for our story "[Facebook Watches Teens Online As They Prep for College](https://themarkup.org/pixel-hunt/2023/11/22/facebook-watches-teens-online-as-they-prep-for-college)".

Dozens of education-related websites transmitted information on visitors through the Meta Pixel.

# Methodology

The Markup tested hundreds of education-related websites based on [work from computer science researchers](https://dl.acm.org/doi/abs/10.1145/3544548.3580777) from the University of Chicago and New York University this year. The researchers used public databases of K-12 schools to develop a list of education-related websites that were frequently linked to from schools.

We ran an automated [Blacklight](https://themarkup.org/blacklight) scan on 114 of these sites. You can read more about how Blacklight conducts its scans [here](https://themarkup.org/blacklight/2020/09/22/how-we-built-a-real-time-privacy-inspector).

The results showed that of these sites, 31 employed the Meta tracking pixel. We included one additional website which we suspected to contain a tracking pixel, [collegeboard.org](https://collegeboard.org/), to bring the total to 32 websites.

We then manually inspected the network traffic while visiting these sites. We looked for any network calls to Facebook servers for the following events:

- A **page view** event when the page initially loaded, sending the name of the page, the URL, and a user ID.
- A **button click** event when a user clicked on a button to log in or access an internal link, sending the button text.

When we found evidence of any of these taking place, we documented it with a screenshot showing the network activity in the browser’s Developer Tools’ Network activity panel showing the call, and the information sent. We also included a [HAR file](https://en.wikipedia.org/wiki/HAR_(file_format)) for the testing session for each site. A HAR file is an archive format supported by most major browsers that contains a recording of all network requests made and received during a browsing session. (_Note: Any instance of a login email or password appearing in plaintext in a HAR file was replaced with the string `MARKUP_REDACTED`_).

Questions? Write to us: [colin@themarkup.org](mailto:colin@themarkup.org) or [ross@themarkup.org](mailto:ross@themarkup.org)

## Data

* **[meta-pixel-edtech-blacklight.csv](https://github.com/the-markup/meta-pixel-edtech/blob/main/meta-pixel-edtech-blacklight.csv)** 3KB. 33 rows. First row is the header.

* We created folders for every website we tested. Inside each folder, there are: 
    * **screenshots** of relevant data being sent to Facebook via the Meta tracking pixel 
    * **HAR files** saved during the process of documenting the data collection


## Data Dictionary

The data format of [meta-pixel-edtech-blacklight.csv](https://github.com/the-markup/meta-pixel-edtech/blob/main/meta-pixel-edtech-blacklight.csv) is as follows:

| Column | Description |
| --- | --- |
| organization | The organization of the websites we tested. |
| domain | The domain of the websites we tested. |
| bl_domain | The domain of the websites we tested, as it appears in Blacklight. |
| third_party_trackers, cookies | The number of ad trackers and third-party cookies found on each website. See the [Blacklight repo](https://github.com/the-markup/blacklight-collector) for more details. |
| canvas_fingerprints, session_recorders, key_logging, meta_pixel_events | Tests for the existence of canvas fingerprinting, session recording, key logging, and Meta pixel events. See the [Blacklight repo](https://github.com/the-markup/blacklight-collector) for more details. |
| ga | Test for the existence of Google Analytics’ “Remarketing Audiences” tool. See the [Blacklight methodology](https://themarkup.org/blacklight/2020/09/22/how-we-built-a-real-time-privacy-inspector) for more details.

## Licensing
Copyright 2023, The Markup News Inc.

Redistribution and use in source and binary forms, with or without modification, are permitted provided that the following conditions are met:

Redistributions of source code must retain the above copyright notice, this list of conditions and the following disclaimer.

Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution.

Neither the name of the copyright holder nor the names of its contributors may be used to endorse or promote products derived from this software without specific prior written permission.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.