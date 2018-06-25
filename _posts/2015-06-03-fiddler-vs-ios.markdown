---
layout: post
title:  "Fiddler vs. iOS"
date:   2015-06-03 00:00:00
categories: networking
---
Dear Alice,

This is meant as a tl;dr on Fiddler MITM proxying. Covering the latest issues and news. Troy Hunt has already covered Mobile App security and proxies thoroughly through his [blog](http://www.troyhunt.com/2014/10/find-crazy-stuff-in-mobile-app.html) and [Pluralsight courses](http://www.pluralsight.com/author/troy-hunt).

### Install and setup
Grab the latest version of Fiddler from [http://www.telerik.com/fiddler](http://www.telerik.com/fiddler). After Fiddler is properly installed, set the following options to allow external connections and decrypt HTTPS traffic:

![fiddler_options_connections]({{ site.url }}/assets/fiddler_options_connections.png)

![fiddler_options_https]({{ site.url }}/assets/fiddler_options_https.png)
<br/><br/>

### Fiddler Root Certificate

The latest versions of iOS are getting picky when it comes to certificate generation. Head over to [http://www.telerik.com/fiddler/add-ons](http://www.telerik.com/fiddler/add-ons) and install the __CertMaker for iOS and Android__ package.

Remember to restart Fiddler at this point.

Navigate your iOS device to http://_yourproxy_:8888/ and follow the instructions to install the Fiddler root certificate.

### iOS Setup
Finally set up your iOS device to use Fiddler as a Proxy:

1. Tap Settings > General > Network > Wi-Fi.
2. Tap the settings for the Wi-Fi network.
3. Tap the Manual option in the HTTP Proxy section.
4. In the Server box, type the IP address or hostname of your Fiddler instance.
5. In the Port box, type the port Fiddler is listening on (usually 8888).

### Usage

I assume that you are familiar with Fiddler in general, however I have a small tips for you: Configure the filter to only show traffic from _Unknown / Remote Processes_.


![fiddler_filter]({{ site.url }}/assets/fiddler_filter.png)

### Note to developers

As a software developer, you should always assume that users have total control of their devices. Security-wise, you should treat mobile applications in the same way as web pages. Assume that the owner can tamper with the device and network communication, dump memory and debug code.

Happy hacking! Remember to be nice to Bob!

Sincerely,<br/>
Mallory
