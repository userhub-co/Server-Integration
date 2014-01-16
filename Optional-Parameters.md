Optional parameters that can be send in the body of a POST back request to UserHub
=================================================================================

* {android_id} - A 64-bit number (as a hex string) that is randomly generated on the device's first boot and should remain constant for the lifetime of the device.
* {android_id_sha1} - SHA1 hashed value of android_id as described above.
* {android_id_md5} - MD5 hashed value of android_id as described above.
* {app_ad_tracking_disabled} - Set to 1 if opted out of ad tracking on the application level. Set to 0 if user not opted out of ad tracking on the application level.
* {app_ad_tracking} - Opposite of above. Set to 1 if user not opted out of ad tracking on the application level. Set to 0 if opted out of ad tracking on the application level.
* {device_id} - The DEVICE ID of the Android device (IMEI for GSM phones, MEID for CDMA phones, SerialID for tablets without a cell radio).
* {device_id_sha1} - SHA1 hashed value of device_id as described above.
* {device_id_md5} - MD5 hashed value of device_id as described above.
* {device_id_sha256} - SHA256 hashed value of device_id as described above. The value should be generated based on the original value lower case. sha256(aaaaaaaa1111111)
* {ios_ad_tracking} - If the ios_ifa parameter is going to be used, then ios_ad_tracking parameter must be specified to indicate whether the user has limited ad with 0 being limited.
* {ios_ad_tracking_disabled} - Opposite of the above with 1 being limited ad tracking.
* {ios_ifa} - The IFA formatted as uppercase with hyphens. AAAAAA-BBBB-CCCC-11111-2222222222222
* {ios_ifa_sha1} - The IFA hashed with Sha1 algorithm. The value should be generated based on uppercase characters with separating hyphens. sha1(AAAAAA-BBBB-CCCC-11111-2222222222222)
* {ios_ifa_md5} - The IFA hashed with MD5 algorithm. The value should be generated based on uppercase characters with separating hyphens. md5(AAAAAA-BBBB-CCCC-11111-2222222222222)
* {ios_ifa_lower} - The IFA formatted as lowercase with hyphens. aaaaaa-bbbb-cccc-1111-222222222222
* {ios_ifa_sha1_lower} - The IFA hashed with Sha1 algorithm. The value should be generated based on uppercase characters with separating hyphens. sha1(aaaaaa-bbbb-cccc-1111-222222222222)
* {ios_ifa_md5_lower} - The IFA hashed with MD5 algorithm. The value should be generated based on lowercase characters with separating hyphens. md5(aaaaaa-bbbb-cccc-1111-222222222222)
* {ios_ifa_alphanumeric} - The IFA formatted as uppercase without colons. AAAAAABBBBCCCC111122222222222
* {ios_ifa_alphanumeric_lower} - The IFA formatted as lowercase without colons. aaaaaabbbbcccc11112222222222222
* {ios_ifa_alphanumeric_lower_sha1} - The IFA hashed with Sha1 algorithm. The value should be generated based on lowercase characters with no hyphens. sha1(aaaaaabbbbcccc11112222222222222)
* {ios_ifa_alphanumeric_lower_md5} - The IFA hashed with MD5 algorithm. The value should be generated based on lowercase characters with no hyphens. md5(aaaaaabbbbcccc11112222222222222)
* {ios_ifv} - The IFV formatted as uppercase with hyphens. AAAAAA-BBBB-CCCC-11111-2222222222222
* {ios_ifv_sha1} - The IFV hashed with Sha1 algorithm. The value should be generated based on uppercase characters with separating hyphens. sha1(AAAAAA-BBBB-CCCC-11111-2222222222222)
* {ios_ifv_md5} - The IFV hashed with MD5 algorithm. The value should be generated based on uppercase characters with separating hyphens. md5(AAAAAA-BBBB-CCCC-11111-2222222222222)
* {ios_ifv_lower} - The IFV formatted as lowercase with hyphens. aaaaaa-bbbb-cccc-1111-222222222222
* {ios_ifv_sha1_lower} - The IFV hashed with Sha1 algorithm. The value should be generated based on uppercase characters with separating hyphens. sha1(aaaaaa-bbbb-cccc-1111-222222222222)
* {ios_ifv_md5_lower} - The IFV hashed with MD5 algorithm. The value should be generated based on lowercase characters with separating hyphens. md5(aaaaaa-bbbb-cccc-1111-222222222222)
* {ios_ifv_alphanumeric} - The IFV formatted as uppercase without colons. AAAAAABBBBCCCC111122222222222
* {ios_ifv_alphanumeric_lower} - The IFV formatted as lowercase without colons. aaaaaabbbbcccc11112222222222222
* {ios_ifv_alphanumeric_lower_sha1} - The IFV hashed with Sha1 algorithm. The value should be generated based on lowercase characters with no hyphens. sha1(aaaaaabbbbcccc11112222222222222)
* {ios_ifv_alphanumeric_lower_md5} - The IFV hashed with MD5 algorithm. The value should be generated based on lowercase characters with no hyphens. md5(aaaaaabbbbcccc11112222222222222)
* {mac_address} - The MAC address of the phone's wifi adapter formatted as uppercase with colons. AA:BB:CC:DD:EE:FF
* {mac_address_alphanumeric_lower_md5} - The MAC address of the phone’s wifi adapter hashed with MD5 algorithm. The value should be generated based on lowercase characters with no colons. md5(aabbccddeeff)
* {mac_address_sha1} - The MAC address of the phone’s wifi adapter hashed with Sha1 algorithm. The value should be generated based on uppercase characters with separating colons. sha1(AA:BB:CC:DD:EE:FF)
* {mac_address_md5} - The MAC address of the phone’s wifi adapter hashed with MD5 algorithm. The value should be generated based on uppercase characters with : separating colons. md5(AA:BB:CC:DD:EE:FF)
* {mac_address_lower} - The MAC address of the phone's wifi adapter formatted as lowercase with colons. aa:bb:cc:dd:ee:ff
* {mac_address_sha1_lower} - The MAC address of the phone’s wifi adapter hashed with Sha1 algorithm. The value should be generated based on uppercase characters with separating colons. sha1(aa:bb:cc:dd:ee:ff)
* {mac_address_md5_lower} - The MAC address of the phone’s wifi adapter hashed with MD5 algorithm. The value should be generated based on lowercase characters with : separating colons. md5(aa:bb:cc:dd:ee:ff)
* {mac_address_alphanumeric} - The MAC address of the phone's wifi adapter formatted as uppercase without colons. AABBCCDDEEFF
* {mac_address_alphanumeric_lower} - The MAC address of the phone's wifi adapter formatted as lowercase without colons. aabbccddeeff
* {mac_address_alphanumeric_lower_sha1} - The MAC address of the phone’s wifi adapter hashed with Sha1 algorithm. The value should be generated based on uppercase characters with no colons. sha1(aabbccddeeff)
* {odin} - The ODIN of the device which is the the MAC address of the phone's wifi adapter in a binary array and then hashed with SHA1 algorithm.
* {open_udid} - The OpenUDID of the device.
* {tpid} - persistent cross-application unique device identifier that TRUSTe has created as a privacy-safe alternative to the deprecated UDID.
* {unid} - Non-specific device identifier, but a catch all for all of the unique identifiers for attribution set on click in tracking link.
* {user_id} - ID of user defined by advertiser.
 
Macros for data from Publisher's click
--------------------------------------

These are values collected on click of a tracking link and available to send in the server postback.

* {advertiser_ref_id} - an optional parameter specified with SDK implementation used for reconciliation; e.g. an order number if tracking a purchase.
* {advertiser_sub_ad_name} - Name of advertiser Sub Ad. Default is value passed into tracking link on click lower case with non-UTF8 characters removed.
* {advertiser_sub_ad} - Value of advertiser_sub_ad passed into tracking link on click.
* {advertiser_sub_adgroup_name} - Name of advertiser Sub Adgroup. Default is value passed into tracking link on click lower case with non-UTF8 characters removed.
* {advertiser_sub_adgroup} - Value of sub_adgroup passed into tracking link on click.
* {advertiser_sub_campaign_name} - Name of advertiser Sub Campaign. Default is value passed into tracking link on click lower case with non-UTF8 characters removed.
* {advertiser_sub_campaign} - Value of advertiser_sub_campaign passed into tracking link on click.
* {advertiser_sub_keyword_name} - Name of advertiser Sub Keyword. Default is value passed into tracking link on click lower case with non-UTF8 characters removed.
* {advertiser_sub_keyword} - Value of advertiser_sub_keyword passed into tracking link on click.
* {advertiser_sub_placement_name} - Name of advertiser Sub Placement; e.g. “top right unit”, or “promoted”. Default is value passed into tracking link on click lower case with non-UTF8 characters removed.
* {advertiser_sub_placement} - Value of advertiser_sub_placement passed into tracking link on click.
* {advertiser_sub_publisher_name} - Name of advertiser Sub Publisher. Default is value passed into tracking link on click lower case with non-UTF8 characters removed.
* {advertiser_sub_publisher} - Value of advertiser_sub_publisher passed into tracking link on click.
* {advertiser_sub_site_name} - Name of advertiser Sub Site. Default is value passed into tracking link on click lower case with non-UTF8 characters removed.
* {advertiser_sub_site} - Value of advertiser_sub_site passed into tracking link on click.
* {campaign_id} - ID of the Campaign in the platform.
* {campaign_name} - Name of Campaign in the platform.
* {campaign_url_id} - the ID of the campaign URL, also called a destination URL.
* {click_device_brand} - Brand name of device determined on click from the user agent using ScientiaMobile.
* {click_device_model} - Model name of device determined on click from the user agent using ScientiaMobile.
* {postback_publisher_id} - ID of the publisher that the server postback is linked to.
* {publisher_id} - ID of the Publisher in the platform that was attributed the install or event.
* {publisher_name} - Name of Publisher in the platform.
* {publisher_ref_id} - Value of the reference ID from a third-party system (third-party click ID) included in tracking link on click.
* {publisher_sub_ad_name} - Name of Sub Ad. Default is value passed into tracking link on click lower case with non-UTF8 characters removed.
* {publisher_sub_adgroup_name} - Name of Sub Adgroup. Default is value passed into tracking link on click lower case with non-UTF8 characters removed.
* {publisher_sub_campaign_name} - Name of Sub Campaign. Default is value passed into tracking link on click lower case with non-UTF8 characters removed.
* {publisher_sub_keyword_name} - Name of Sub Keyword. Default is value passed into tracking link on click lower case with non-UTF8 characters removed.
* {publisher_sub_placement_name} - Name of Sub Placement passed into tracking link on click. Default is value passed into tracking link on click lower case with non-UTF8 characters removed.
* {publisher_sub_publisher_name} - Name of Sub Publisher. Default is value passed into tracking link on click lower case with non-UTF8 characters removed.
* {publisher_sub_site_name} - Name of Sub Site. Default is value passed into tracking link on click lower case with non-UTF8 characters removed.
* {publisher_sub1} - Value of the sub 1 parameter included in tracking link on click.
* {publisher_sub2} - Value of the sub 2 parameter included in tracking link on click.
* {publisher_sub3} - Value of the sub 3 parameter included in tracking link on click.
* {publisher_sub4} - Value of the sub 4 parameter included in tracking link on click.
* {publisher_sub5} - Value of the sub 5 parameter included in tracking link on click.
* {session_id} - ID of the session in the platform.
* {site_name} - Name of mobile app (site); used in lieu of the site_ID.
* {sub_ad} - Value of sub_ad passed into tracking link on click.
* {sub_adgroup} - Value of sub_adgroup passed into tracking link on click.
* {sub_campaign} - Value of sub_campaign passed into tracking link on click.
* {sub_keyword} - Value of sub_keyword passed into tracking link on click.
* {sub_placement} - Value of sub_placement passed (e.g. “top right unit”, or “promoted”) placed into tracking link on click.
* {sub_publisher} - Value of sub_publisher passed into tracking link on click.
* {sub_site} - Value of sub_site passed into tracking link on click.
* {tracking_id} - ID of the tracking session created on click of tracking link by platform.
 
Macros for data from Conversion
-------------------------------

These are values collected on conversion (install, event, open, etc.) and available to send in the server postback.

* {ad_network_id} - ID of the ad network’s account in the platform.
* {advertiser_id} - ID of the advertiser's account in the platform.
* {advertiser_name} - Name of advertiser's account in platform.
* {amount} - Revenue generated from the conversion as a floating point number.
* {app_version} - The version of the app itself.
* {conversion_referral} - Referral URL to the conversion. On Android app installs, this is the Google Install Referrer.
* {conversion_user_agent} - User-agent for the device that created the conversion.
* {country_code} - Two character abbreviated country code that user is located in on conversion.
* {currency_code} - Currency code of revenue using ISO 4217 currency codes.
* {device_brand} - Brand for user's device (phone) such as "Apple" or "Samsung".
* {device_carrier} - Carrier (service provider) for the device such as "Verizon Wireless".
* {device_ip} - IP address of the user's device (phone) recorded on conversion.
* {device_model} - Model for the user's device (phone) recorded on conversion such as "Droid Pro".
* {device_type} - Type of device used by user; possible values of desktop, android phone, android tablet, iOS phone, iOS tablet, windows phone, windows tablet, other, unknown.
* {event_id} - ID of the Event in the platform.
* {event_items_json} - JSON display payload of site event items.
* {event_name} - Name of event in the platform.
* {fb_app_id} - Facebook app user id, only available for users who originated on Facebook.
* {iap_receipt} - Value of receipt passed from Android or iOS SDK used to validate IAP server-side.
* {iap_receipt_md5} - MD5 hash of the above. This hash is be a unique value per purchase and can be used like an ID for the purchase.
* {is_assist} - Set to 1 if publisher assisted with, but is not responsible for, conversion; set to 0 otherwise.
* {is_reengagement} - Set to 1 if the event is with re-engagement; set to 0 otherwise.
* {is_view_through} - Set to 1 if a view-through conversion; set to 0 otherwise.
* {language} - Name of the language used on the user's device (phone).
* {match_type} - Attribution method used; possible values include fingerprint, fb_integration, identifier, referrer, identifier_post.
* {mobile_app_type} - Type of mobile app, i.e. 'web', 'ios', or 'android'.
* {nonwindowed_attribution} - Set to 1 if click occurs outside of publisher attribution window, but inside MAT’s attribution window; set to 0 otherwise.
* {os_jailbroke} - Set to 1 if iOS device has been jailbroken; set to 0 otherwise.
* {os_version} - Version of operating system on the user's device (phone).
* {package_app_name} - Name of application defined in the package like "Words with Friends".
* {package_app_version} - Version of the application defined in the package like 2.1.
* {package_name} - Name of the package for Android or Bundle ID on iOS such as "com.zynga.words"
* {payout} - Payout amount for publisher. Always in USD.
* {retry_attempts} - Number of times the server postback is attempted.
* {revenue_usd} - Revenue generated from the conversion using the current day's exchange rate.
* {revenue} - Revenue generated from the conversion as a floating point number.
* {sdk} - Type of SDK; 'ios' or 'android'.
* {site_event_id} - ID of the event displayed in the platform.
* {site_id} - ID of the Site (mobile app) in the platform.
* {store_app_id} - Value of store App ID set in platform. For iOS apps, its the Apple iTunes App ID.
* {user_agent} - User-agent for the device that created the conversion.

Date and Time macros
--------------------

These are date and time values collected on conversion (install, event, open, etc.) and available to send in the server postback.

* {conversion_date} - Conversion date formatted as YYYY-MM-DD.
* {conversion_datetime-120} - Conversion date (minus 120secs) and time formatted as YYYY-MM-DD HH:MM:SS.
* {conversion_datetime-300} - Conversion date (minus 300secs) and time formatted as YYYY-MM-DD HH:MM:SS.
* {conversion_datetime} - Conversion date and time formatted as YYYY-MM-DD HH:MM:SS.
* {conversion_time} - Conversion time formatted as HH:MM:SS.
* {conversion_timestamp} - Conversion time formatted as UNIX timestamp.
* {conversion_timestamp_milliseconds} - Conversion time formatted as UNIX timestamp in epoch milliseconds.
* {conversion_timestamp-120} - Conversion time minus 120secs formatted as UNIX timestamp.
* {conversion_timestamp-300} - Conversion time minus 300secs formatted as UNIX timestamp.
* {date} - Date as formatted as YYYY-MM-DD.
* {datetime} - Date and time formatted as YYYY-MM-DD HH:MM:SS.
* {impression_date} - Impression date formatted as YYYY-MM-DD.
* {impression_datetime} - Impression date and time formatted as YYYY-MM-DD HH:MM:SS.
* {impression_time} - Impression time formatted as HH:MM:SS.
* {impression_timestamp} - Impression time formatted as UNIX timestamp.
* {impression_timestamp_milliseconds} - Impression time formatted as UNIX timestamp in epoch milliseconds.
* {session_date} - Date of session created on click formatted as YYYY-MM-DD.
* {session_datetime} - Date and time of session created on click formatted as YYYY-MM-DD HH:MM:SS.
* {session_device_ip} - IP address of the device that started the tracking session.
* {session_referrer} - Referrer for the device that started the tracking session.
* {session_time} - Time of session created on click formatted as HH:MM:SS.
* {session_timestamp} - Time of session created on click formatted as UNIX timestamp.
* {session_timestamp_milliseconds} - Time of session created on click formatted as UNIX timestamp in epoch milliseconds.
* {session_user_agent} - User-agent for the device that started the tracking session.
* {time} - Time formatted as HH:MM:SS.
* {timestamp} - Time formatted as UNIX timestamp.
* {timestamp_milliseconds} - Time formatted as UNIX timestamp in epoch milliseconds.
