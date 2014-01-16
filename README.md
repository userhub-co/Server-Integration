UserHub Server to Server Integration
===================================

UserHub (http://www.userhub.co) delivers new highly valuable users to your mobile application. We've built proprietary artificial intelligence and machine learning algorithms to seek out and target only the highest value users for yor mobile application, targeting users on a variety of RTB (Real Time Bidding) networks like `MoPub`.  We pick from over 100 million monthly engaged devices, and deliver only ones that matter to you. 

UserHub relies on your systems to tell us when users that we deliver are highly valuable, so our machine learning algorithms can fine-tune in real time. UserHub integration requires *no* modification of your mobile app. Instead, you simply call our server from your server with user-events. Our API for the server-to-server integration is documented within this page.

TL;DR
--------------
On each install, and other valuable user events, please POST to:

<code>
https://api.userhub.co/event?client={your-network-or-advertiser-userhub-id}
</code>

POST as much of these parameters as you can to us in the body (`ios_ifa` [device ID], `ref_id` [click ID], and `event_name` [e.g. 'Install'] are the most important, which let us look back at the conversion event).

ref_id={ref_id}&event_name={event_name}&device_id_md5={device_id_md5}&device_id_sha1={device_id_sha1}&android_id={android_id}&android_id_md5={android_id_md5}&android_id_sha1={android_id_sha1}&mac_address={mac_address}&mac_address_sha1={mac_address_sha1}&mac_address_md5={mac_address_md5}&odin={odin}&open_udid={open_udid}&ios_ifa={ios_ifa}&ios_ifa_md5={ios_ifa_md5}&ios_ifa_sha1={ios_ifa_sha1}&ios_ad_tracking={ios_ad_tracking}&ios_ad_tracking_disabled={ios_ad_tracking_disabled}&unid={unid}&user_id={user_id}&tracking_id={tracking_id}&publisher_id={publisher_id}&publisher_name={publisher_name}&campaign_id={campaign_id}&campaign_name={campaign_name}&sub_publisher={sub_publisher}&sub_site={sub_site}&sub_campaign={sub_campaign}&sub_adgroup={sub_adgroup}&sub_ad={sub_ad}&publisher_sub_publisher_name={publisher_sub_publisher_name}&publisher_sub_site_name={publisher_sub_site_name}&publisher_sub_campaign_name={publisher_sub_campaign_name}&publisher_sub_adgroup_name={publisher_sub_adgroup_name}&publisher_sub_ad_name={publisher_sub_ad_name}&sub1={sub1}&sub2={sub2}&sub3={sub3}&sub4={sub4}&sub5={sub5}&advertiser_id={advertiser_id}&advertiser_name={advertiser_name}&site_id={site_id}&site_name={site_name}&site_ref_id={site_ref_id}&app_name={app_name}&mobile_app_type={mobile_app_type}&sdk={sdk}&event_id={event_id}&payout={payout}&revenue={revenue}&revenue_usd={revenue_usd}&currency_code={currency_code}&device_ip={device_ip}&device_brand={device_brand}&device_model={device_model}&device_carrier={device_carrier}&os_version={os_version}&country_code={country_code}&language={language}&package_name={package_name}&package_app_name={package_app_name}&package_app_version={package_app_version}&advertiser_ref_id={advertiser_ref_id}&conversion_user_agent={conversion_user_agent}&conversion_referral={conversion_referral}&timestamp={timestamp}&conversion_timestamp_milliseconds={conversion_timestamp_milliseconds}&session_timestamp={session_timestamp}&session_user_agent={session_user_agent}&session_referrer={session_referrer}


And if you can, please POST all user events you're able to so our machine learning engine can optimize around user LTV.


Detailed Overview
===============================================

There are two main events which occur during advertising, which we outline here: the user going to the app store, and then the user installing, opening, and generating revenue events during usage of the advertiser's app.

The Click Through: Redirecting to the App Store
-----------------------------------------------

Every time a user clicks on a banner driving app installs for your application, UserHub will redirect that user to the app store. UserHub can implement this redirect via your own tracking server. As a result, UserHub can pass relevant information to you that can be used for both attribution and algorithm learning. If you do not want the redirect to pass your servers then UserHub will simply redirect to the app store. In all cases UserHub requires you to send a POST back request for every install you register

UserHub will call your server as follows:

<code>
http://your-server.com/redirect?redirect_url=app_store_url_&ref_id=unique_id&ios_ifa=ios_ifa
</code>

Your server needs to keep the `ref_id` and `ios_ifa` id stored and redirect the request to the app store using the `redirect_url` provided in this request. As soon as the installation completes, and the user opens the app for the first time your server should call the UserHub server with a POST request as follows:

<code>
https://api.userhub.co/event?client={your-network-or-advertiser-userhub-id}
</code>

The `your-network-or-advertiser-userhub-id` is an ID that is provided by us that identifies your company in the POST back. In the body of the request you can add information that enables us to verify the install, and helps us improve our performance in finding engaged users for your app. As a minimum we require that you send us:

1. a network/advertiser identifier that identifies your company to us.
2. an IDFA on iOS, or a device id, Android ID, Android serial nmber on Android.
3. an `event_name`, defaulting to 'Install' that describes the kind of event this callback represents
4. *OPTIONAL* a secret hash that verifies the request is coming from you, for added security

The UserHub server will respond with one of the following HTTP status codes:

* `200`:  Your request was well formed and was properly processed by UserHub’s server.
* `400`:  At least one required HTTP POST parameter was not supplied.
* `404`:  Your specified `your-network-or-advertiser-userhub-id` doesn’t correspond to a known UserHub client.
* `403`:  *OPTIONAL* If a secret hash is supplied, but doesn't match the expected value.


The Install / Event: Sending data in the body of the POST back request
-----------------------------------------------------------------------

In order to attribute installs and increase the efficiency of the UserHub algorithm we need you to send us a POST back request for every install that you receive. All POST back requests need to be directed to:

<code>
https://api.userhub.co/event?client={your-network-or-advertiser-userhub-id}
</code>

Data can be send in the body of the request. As a minimum we require the following:

* `event_name` - type of event being logged, like ‘Install’
* `your-network-or-advertiser-userhub-id` - your UserHub client ID provided by us
* `ref_id` - The original UserHub reference id for the advertisement/click-thru generating this user
* At least *one* unique identifier documented below:
	* `ios_ifa` (or `ios_ifa_md5` / `ios_ifa_sha1`) -  With iOS 6+, Apple’s Identifier for Advertisers.
	* `android_id` (or `android_id_md5` / `android_id_sha1`) - This is the parameter for ANDROID ID on Android devices only. It is a 64-bit number (as a hex string) that is randomly generated on the device's first boot and should remain constant for the lifetime of the device.
	* `device_id` (or `device_id_md5` / `device_id_sha1`) - The DEVICE ID of the Android device (IMEI for GSM phones, MEID for CDMA phones, SerialID for tablets without a cell radio).
	* `odin` - The ODIN of the device. To be generated or retrieved using the official implementation.
	* `open_udid` - The OpenUDID of the device. To be generated or retrieved using the official implementation.
	* `mac_address` (or `mac_address_md5` / `mac_address_sha1`) - Mac address of the Wifi network card on the device
	* `user_id` - Unique user ID of user defined by you. Example value: `tom12345`

Optional parameters for events (for a full list of optional parameters see [here](Optional-Parameters.md)):

* `secret_hash` - a secret hash that you need to create using data provided by UserHub
* `device_brand` - Brand for user's device (phone) such as "Apple" or "Samsung".
* `device_model` - Model for the user's device (phone) recorded on conversion such as "Droid Pro".
* `os_version` - Version of operating system on the user's device (phone).
* `device_ip` - IP address of the user's device (phone) recorded on conversion.
* `device_carrier` - Carrier (service provider) for the device such as "Verizon Wireless".
* `revenue` (or `revenue_usd`) - Amount of revenue for sale on this event. Example value: 3.10
* `currency_code` - 3 letter code of currency of amount value. Example value: USD
* `country_code` - 2 letter code of country. Example value: "CA" for Canada. Default value is US.
* `datetime` - If datetime is not set, current datetime will be used. UTC formatted asssss yyyy-mm-dd hh:mm:ss


Event registration
------------------


You can use the same POST back URL to send UserHub relevant event data that will enable us to train the machine learning algorithm and provide you with more engaged users. When you send us an event, please be sure to add a revenue value to it, as this value will be used for learning purposes. An example event would be:

<code>
https://api.userhub.co/event?client={your-network-or-advertiser-userhub-id}
</code>

* `event_name` - ‘order’
* `revenue` - Amount of revenue for sale on install. Example value: 10.10
* `currency_code` - 3 letter code of currency of amount value. Example value: USD
* `country_code` - 2 letter code of country. Example value: "CA" for Canada. Default value is US.
* `ref_id` - The original UserHub reference id for the advertisement/click-thru generating this user
* At least *one* unique identifier documented below:
	* `ios_ifa` (or `ios_ifa_md5` / `ios_ifa_sha1`) -  With iOS 6+, Apple’s Identifier for Advertisers.
	* `android_id` (or `android_id_md5` / `android_id_sha1`) - This is the parameter for ANDROID ID on Android devices only. It is a 64-bit number (as a hex string) that is randomly generated on the device's first boot and should remain constant for the lifetime of the device.
	* `device_id` (or `device_id_md5` / `device_id_sha1`) - The DEVICE ID of the Android device (IMEI for GSM phones, MEID for CDMA phones, SerialID for tablets without a cell radio).
	* `odin` - The ODIN of the device. To be generated or retrieved using the official implementation.
	* `open_udid` - The OpenUDID of the device. To be generated or retrieved using the official implementation.
	* `mac_address` (or `mac_address_md5` / `mac_address_sha1`) - Mac address of the Wifi network card on the device
	* `user_id` - Unique user ID of user defined by you. Example value: `tom12345`


Questions?
----------


Contact your UserHub account manager at support@userhub.co, and we will help you ASAP.
