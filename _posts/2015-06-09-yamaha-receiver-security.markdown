---
layout: post
title:  "Yamaha receiver security"
date:   2015-06-09 00:00:00
categories: security
---
I recently discovered that a lot of Yamaha receivers are found unprotected on the internet. A MAC filter is the only available form of protection (and only a minority has this enabled). The web interface allows total control of the devices.

### Fingerprint

You can use the following details to identify Yamaha receivers using the [Shodan search engine](http://shodan.io/).

    HTTP/1.1 406 Not Acceptable
    Server: AV_Receiver/3.1 (RX-A2010)
    Content-Length: 0
    Connection: close

### Accessing the Radio playlists

Using [Yamaha vTuner service](http://yradio.vtuner.com/setupapp/yamaha/asp/AuthLogin/SignIn.asp) will allow you to add new custom radio channels to the receiver. This way you can totally control the device by setting up a custom radio stream. The receiver will play the music as well as display the channel name (manually added by you) on the display.

To connect to a device you need the MAC address. This shouldn't be to difficult. All the MAC addresses are using the same vendor prefix of __00:a0:de__. The second half of the MAC address can usually be found as part of the default name. In the UI you can fetch the name by opening _Settings_ and the _Rename_ tab.

![yamaha_mac]({{ site.url }}/assets/yamaha_mac.png)

To add custom radio channels, you'll need to enter an email address. This will link the device to that account/email address. The rightful owner can only regain access to vTuner by emailing support and make them manually reset the device.

![yamaha_channel]({{ site.url }}/assets/yamaha_channel.png)

### Conclusion

Please make sure that your Yamaha device is behind a firewall. Network enabled home devices should never be connected directly to the internet without any form of protection. The security is usually really bad, and the devices usually contains a lot of personal information. Almost any basic wireless router on the market will give you basic firewall settings.

