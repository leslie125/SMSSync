Welcome to *"SMSSync"*, its an android application that turns your android powered phone into an SMS gateway. It main use could be to push SMSes that come to the phone to a website you configure the application to send them to. You could filter out which messages to push to the website based on keywords or tags 

h1.Instructions

* To start the SMSSync Gateway, you'll need to specify a callback URL. This URL is where all incoming text messages will be transmitted to.
* For security you can specify at secret at the callback URL. If the secret doesn't match, the callback URL will ignore the transmission.
* Additionally, you can specify keywords with which to filter incoming messages. Only matching text messages will be sent to the SMSSync Gateway URL.

* The SMSSync sends the following variables via the POST method: 
    * *from*
    * *message*
    * *secret*

* In order for SMSSync to account for perfect transmission, the callback URL needs to give back a formatted JSON string such as its shown below to indicate if it received the message or not.
   * *Succeeded* 
<pre><code>{
      payload: {
          success: "true"
      }
}</code></pre>
  
   * *Failed*
<pre><code>{
      payload: {
          success: "false"
      }
}</code></pre>
        
* SMSSync supports execution of task sent from the configured callback URL. At the moment, it supports sending messages sent from the callback URL as SMS. This feature is targeted towards developers. If you are developer and you want SMSSync to send an SMS send a JSON formatted string as below to SMSSync with the variable task=sendsms. When SMSSync does an HTTP GET request with the URL http://<callback url>/smssync?task=sendsms, it should bring back the JSON string below.

   * *Response JSON data from the callback URL* 
<pre><code>{
    "payload": {
        "task": "send",
        "messages": [
            {
                "to": "000-000-0000",
                "message": "the message goes here" 
            },
            {
                "to": "000-000-0000",
                "message": "the message goes here" 
            },
            {
                "to": "000-000-0000",
                "message": "the message goes here" 
            }
        ]
    }
}</code></pre>

*Scan the QR below to install SMSSync on your Android powered phone*
[[http://qrcode.kaywa.com/img.php?s=6&#038;d=http%3A%2F%2Fmarket.android.com%2Fdetails%3Fid%3Dorg.addhen.smssync/whaever.png]]

*We appreciate your feedback*

Copyright © 2010 [[Ushahidi.com|http://www.ushahidi.com]]