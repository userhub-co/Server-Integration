AdGoji Server to Server Integration
===================================

AdGoji (http://www.adgoji.com) delivers installs and engaged users of your iOS or Android App. AdGoji uses unique artificial intelligence algorithms to find these users / installs on the largest Real-Time-Bidding platforms in the world. 

If you want to increase the effectiveness of your campaigns on AdGoji you can integrate with AdGoji to track unique installs of your app using a server-to-server solution. This requires no modification of your mobile app. This document describes the api for the server-to-server integration with AdGoji.

Quick overview
--------------


Every time a user clicks on a banner driving app installs for your application, AdGoji will redirect that user to the app store. AdGoji can implement this redirect via your own tracking server. As a result, AdGoji can pass relevant information to you that can be used for both attribution and algorithm learning. If you do not want the redirect to pass your servers then AdGoji will simply redirect to the app store. In all cases AdGoji requires you to send a POST back request for every install you register

AdGoji will call your server as follows:

```http://your-server.com/redirect?redirect_url=<app store url here>&request_id=<a-unique-request-id-here>&ios_ifa=<IOS ADVERTISER ID HERE>```

Your server needs to keep the `request_id` and `ios_ifa` id stored and redirect the request to the app store using the `redirect_url` provided in this request. As soon as the installation completes, and the user opens the app for the first time your server should call the AdGoji server with a POST request as follows:

<code>
https://rtb-bidder.adgoji.com/event?client={adgoji-unique-advertiser-id}
</code>

The `adgoji-unique-advertiser-id` is an ID that is provided by us that identifies your POST back. In the body of the request you can add information that enables us to verify the install, and helps us improve our performance in finding engaged users for your app. As a minimum we require that you send us:

1. an `advertiser-id` on iOS, or a device id, Android ID, Android serial nr on Android.
2. a secret hash that verifies the request is coming from you.
3. an app identifier that identifies the app the install was created for.

The AdGoji server will respond with one of the following HTTP status codes:

* `400`:  At least one required HTTP POST parameter was not supplied.
* `403`:  Your security hash doesn’t match the expected value.
* `404`:  Your specified app identifier doesn’t correspond to an app registered with AdGoji.
* `200`:  Your request was well formed and was properly processed by AdGoji’s server.


Sending data in the body of the POST back request
-------------------------------------------------


In order to attribute installs and increase the efficiency of the AdGoji algorithm we need you to send us a POST back request for every install that you receive. All POST back requests need to be directed to:

<code>
https://rtb-bidder.adgoji.com/event?client={adgoji-unique-advertiser-id}
</code>

Dat can be send in the body of the request. As a minimum we require the following:

* action - ‘conversion’
* secret_hash - a secret hash that you need to create using data provided by AdGoji
* site_id - ID of mobile app displayed in platform
* site_event_name or site_event_id
	* The site event ID is the ID of the event displayed in platform.
 	* The site event name is the name of the event that can be dynamically created.
* At least one unique identifier documented below:
	* device_id - The DEVICE ID of the Android device (IMEI for GSM phones, MEID for CDMA phones, SerialID for tablets without a cell radio).
	* android_id - This is the parameter for ANDROID ID on Android devices only. It is a 64-bit number (as a hex string) that is randomly generated on the device's first boot and should remain constant for the lifetime of the device.
	* odin - The ODIN of the device. To be generated or retrieved using the official implementation.
	* ios_ifa -  With iOS 6+, Apple’s Identifier for Advertisers.
	* user_id - Unique user ID of user defined by advertiser. Example value: tom12345

Optional parameters for events (for a full list of optional parameters see [here](Optional-Parameters.md)):

* request_id - The original request id that we send you in combination with the ios_ifa during the redirect to the app store
* device_brand - Brand for user's device (phone) such as "Apple" or "Samsung".
* device_model - Model for the user's device (phone) recorded on conversion such as "Droid Pro".
* os_version - Version of operating system on the user's device (phone).
* device_ip - IP address of the user's device (phone) recorded on conversion.
* device_carrier - Carrier (service provider) for the device such as "Verizon Wireless".
* revenue - Amount of revenue for sale on install. Example value: 10.10
* currency_code - 3 letter code of currency of amount value. Example value: USD
* country_code - 2 letter code of country. Example value: "CA" for Canada. Default value is US.
* datetime. - If datetime is not set, current datetime will be used. UTC formatted asssss yyyy-mm-dd hh:mm:ss


Event registration
------------------


You can use the same POST back URL to send AdGoji relevant event data that will enable us to train the machine learning algorithm and provide you with more engaged users. When you send us an event, it is important to add a value to it, as this value will be used for learning purposes. An example event would be:

<code>
https://rtb-bidder.adgoji.com/event?client={adgoji-unique-advertiser-id}
</code>

* action - ‘order’
* revenue - Amount of revenue for sale on install. Example value: 10.10
* currency_code - 3 letter code of currency of amount value. Example value: USD
* country_code - 2 letter code of country. Example value: "CA" for Canada. Default value is US.
* secret_hash - a secret hash that you need to create using data provided by AdGoji
* site_id - ID of mobile app displayed in platform
* site_event_name or site_event_id
	* The site event ID is the ID of the event displayed in platform.
 	* The site event name is the name of the event that can be dynamically created.
* At least one unique identifier documented below:
	* device_id - The DEVICE ID of the Android device (IMEI for GSM phones, MEID for CDMA phones, SerialID for tablets without a cell radio).
	* android_id - This is the parameter for ANDROID ID on Android devices only. It is a 64-bit number (as a hex string) that is randomly generated on the device's first boot and should remain constant for the lifetime of the device.
	* odin - The ODIN of the device. To be generated or retrieved using the official implementation.
	* ios_ifa -  With iOS 6+, Apple’s Identifier for Advertisers.
	* user_id - Unique user ID of user defined by advertiser. Example value: tom12345


Questions?
----------


Contact your AdGoji account manager, and we will help you immediately.

