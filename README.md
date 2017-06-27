How to Install and handle nodes?
=================================
Take a look in this video: https://www.youtube.com/watch?v=TlzqGhfdbEM&t=83s

I made some changes in this node, because I want to you it on my raspberry pi and using the push in a other region.

To install this you try to use following steps:
```
  pi@raspberrypi:~/node-red-contrib-ibmpush-custom $ sudo npm link
  pi@raspberrypi:~/node-red-contrib-ibmpush-custom $ ls
  CLA.md  ibmpush  LICENSE  node_modules  package.json  README.md
  pi@raspberrypi:/ $ cd /usr/lib/node_modules
  pi@raspberrypi:/usr/lib/node_modules $ ls
  node-red  node-red-contrib-ibmpush-custom  npm
  pi@raspberrypi:~ $ cd /.node-red
  pi@raspberrypi:~/.node-red $ ls
  flows_raspberrypi_cred.json  lib           package.json
  flows_raspberrypi.json       node_modules  settings.js
  pi@raspberrypi:~/.node-red $ npm link node-red-contrib-ibmpush-custom
/home/pi/.node-red/node_modules/node-red-contrib-ibmpush-custom -> /usr/lib/node_modules/node-red-contrib-ibmpush-custom -> /home/pi/node-red-contrib-ibmpush-custom
  pi@raspberrypi:~/.node-red $ sudo reboot
  Connection to 192.168.178.58 closed by remote host.
  Connection to 192.168.178.58 closed.
```
Input:

![Input](https://github.com/thomassuedbroecker/node-red-contrib-ibmpush/blob/images/nodered-input-config.png)

Input working with EU-GB

![Working](https://github.com/thomassuedbroecker/node-red-contrib-ibmpush/blob/images/nodered-working.png)

node-red-contrib-ibmpush
========================
Sends push notifications to mobile devices in [Node-RED](http://nodered.org) using IBM Push Notification for Bluemix

Install
-------
Install from [npm](http://npmjs.org)
```
npm install node-red-contrib-ibmpush
```

Usage
-----

`msg.payload` is used as the alert in the Notification.

**Mobile Push Properties**

*Application Mode* - Select the mode of operation for the IBM Push Notification. You can override this property by providing ```msg.mode```

*Application ID and Secret* - mandatory only when used in *non-Bluemix environment* and must be copied from the IBM Push Notification service in Bluemix. If used in *Bluemix environment*, these properties will be automatically read and these properties are not displayed in the configuration screen.

**Notification Type**

Type of notification to be pushed.

- Broadcast - Send notifications to all the registered devices
- By Tags - Send notifications to devices subscribed to that tag. Can take multiple values seperated by comma(,)
- By DeviceIds - Send notifications to devices by their device ID. Can take multiple values seperated by comma(,)
- Only Android devices - Send notifications to all the registered Android devices
- Only iOS devices - Send notifications to all the registered iOS devices

*Notification Identifiers* - Used when notifications are sent *By Tags and By DeviceIds*. This can take multiple values seperated by comma(,). Example: GoldCoupons,SilverCoupons. You can override this property by providing ```msg.identifiers```

Visit this [link](https://console.ng.bluemix.net/docs/services/mobilepush/c_overview_push.html) for more information on IBM Push Notification for Bluemix

=======
