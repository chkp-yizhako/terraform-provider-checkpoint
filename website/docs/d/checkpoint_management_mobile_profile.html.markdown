---
layout: "checkpoint"
page_title: "checkpoint_management_mobile_profile"
sidebar_current: "docs-checkpoint-resource-checkpoint-management-mobile-profile"
description: |-
Use this data source to get information on an existing Check Point Mobile Profile.
---

# checkpoint_management_mobile_profile

Use this data source to get information on an existing Check Point Mobile Profile.

## Example Usage


```hcl
resource "checkpoint_management_mobile_profile" "mobile_profile" {

  name = "My Mobile Profile"
  applications  {
    enable_print_mails = true
    calendar_from_the_last_unit = "weeks"
  }
  harmony_mobile {
    enable_harmony_mobile_sdk = true
    os_integrity_compromised =  "ignore"
  }

  security {
    session_timeout = 2
    session_timeout_unit = "weeks"
    activate_passcode_lock = false
    allow_store_credentials = true
    hide_ssl_connect_anyway_button = true
    block_jailbroken = "block"

  }

}

data "checkpoint_management_mobile_profile" "data" {
  uid = "${checkpoint_management_mobile_profile.mobile_profile.id}"
}*/
```

## Argument Reference

The following arguments are supported:

* `name` - (Optional) Object name. 
* `uid` - (Optional) Object unique identifier.
* `applications` -  Applications settings.applications blocks are documented below.
* `client_customization` - Client customization settings.client_customization blocks are documented below.
* `data_leak_prevention` - Data leak prevention settings.data_leak_prevention blocks are documented below.
* `harmony_mobile` - Integrations settings.harmony_mobile blocks are documented below.
* `security` - Security settings.security blocks are documented below.
* `tags` -  Collection of tag identifiers.tags blocks are documented below.
* `color` - Color of the object. Should be one of existing colors. 
* `comments` -Comments string. 
* `domains_to_process` - Indicates which domains to process the commands on. It cannot be used with the details-level full, must be run from the System Domain only and with ignore-warnings true. Valid values are: CURRENT_DOMAIN, ALL_DOMAINS_ON_THIS_SERVER.domains_to_process blocks are documented below.
* `ignore_warnings` - Apply changes ignoring warnings. 
* `ignore_errors` -  Apply changes ignoring errors. You won't be able to publish such a changes. If ignore-warnings flag was omitted - warnings will also be ignored. 


`applications` supports the following:

* `enable_print_mails` -  Allow to print mails. 
* `max_attachments_size` - Maximum size of attachments allowed for downloading -  you can choose a unit (gbs, kbs, mbs, bytes) in "max-attachments-unit" field. 
* `calendar_from_the_last` -  How far back to see your Calendar from the current date - you can choose a unit (day, week, month) in "calendar-from-the-last-unit" field. 
* `calendar_from_the_last_unit` - Unit for "calendar-from-the-last" numeric value. 
* `calendar_to_the_following` -  How much ahead to see your Calendar from the current date - you can choose a unit (day, week, month) in "calendar-to-the-following-unit" field. 
* `calendar_to_the_following_unit` -  Unit for "calendar-to-the-following" numeric value. 
* `mail_from_the_last` - How far back to see your emails from the current date - choose a unit (day, week, month) in "mail-from-the-last-unit" field. 
* `mail_from_the_last_unit` -  Unit for "mail-from-the-last" numeric value. 
* `synchronize_contacts` - Contacts synchronization method - from the mail server to device and the app and vice versa or from the mail server to device and the app or from the mail server to the app. 
* `allow_push_notification` -  Allow to receive push notifications of mails and meetings. 
* `allow_calendar_sync` -  Allow synchronization between business calendar to device calendar. 
* `allow_contacts_from_global_address_list` -  Allow to add additional contacts from Global Address List to the app. 
* `allow_contacts_from_local_phone` - Allow to add additional contacts from local phone to the app. 
* `save_local_web_cache` -  Configure whether local cache data generated by web browser should be preserved. 
* `allow_caching_docsec_credentials` -  Allow store encrypted document credentials in application secure storage. 
* `allow_caching_docsec_keys` -  Allow store encrypted document keys in application secure storage. 


`client_customization` supports the following:

* `app_theme_color_dark` -  Configure the application display colors in Dark mode. 6 hex digits that define RGB color - relevant for IOS. 
* `app_theme_color_light` -  Configure the application display colors in light mode. 6 hex digits that define RGB color - relevant for IOS. 
* `allow_calendar` -  Allow sync business calendar to device calendar. 
* `allow_contacts` -  Enable/Disable contacts app. 
* `allow_mail` -  Enable/Disable email app. 
* `allow_notes_sync` -  Allow sync business notes to device notes. 
* `allow_saved_file_apps` - Allow the appearance of 'Saved file app' in the app list. 
* `allow_secure_chat` -  Enable/Disable Messages app (depends on Mail app). 
* `allow_tasks` -  Enable/Disable Tasks app. 
* `certificate_expire_message` -  message to show users when certificate is expired - for admin to fill - can contain only English characters, digits, comma, spaces and points. 


`data_leak_prevention` supports the following:

* `open_extension_with_external_app` -  Open the following extensions from your app with external apps when they cannot be opened with Capsule viewer.open_extension_with_external_app blocks are documented below.
* `share_protected_extension` -  Share protected files extensions to external apps.share_protected_extension blocks are documented below.
* `share_unprotected_extension` -  Share unprotected files extensions to external apps.share_unprotected_extension blocks are documented below.
* `allow_copy_paste` -  Allow copy paste of mail content. 
* `block_forward_attachments` -  Allow share mail attachments with external mails. 
* `block_screenshot` -  If true - you can't make a screenshot from your app. 
* `allowed_domains_forward_attachment` -  exclusion of domains which attachments are allowed to be sent, even that shared policy prevents sharing these kinds of attached files - can contain only English characters, digits, comma, spaces and points. 
* `accept_protected_file_extensions` -  Accept protected files with these extensions from external apps to your app.accept_protected_file_extensions blocks are documented below.
* `accept_unprotected_file_extensions` - Accept unprotected files with these extensions from external apps to your app.accept_unprotected_file_extensions blocks are documented below.
* `allow_import_from_gallery` - Allow import media from gallery. 
* `allow_taking_photos_and_videos` -  Allow the camera to be used from your app. 
* `offer_capsule_as_viewer` - Offer Capsule as a viewer for external protected documents. 


`harmony_mobile` supports the following:

* `protect_policy_enabled` -  Enable/disable Protect Application- cannot be enable if Harmony SDK is enable. 
* `protect_high_risk_action` -  What is the action if there is high risk found by Harmony Mobile. 
* `protect_high_risk_message` -  The message can contain only English characters, digits, comma, spaces and points. 
* `protect_medium_risk_action` -  What is the action if there is medium risk found by Harmony Mobile. 
* `protect_medium_risk_message` -  The message can contain only English characters, digits, comma, spaces and points. 
* `protect_not_activated_action` -  What is the action if there is policy violation (configuration for Harmony Mobile). 
* `protect_not_activated_message` -  The message can contain only English characters, digits, comma, spaces and points. 
* `enable_harmony_mobile_sdk` -  Enable/disable Harmony SDK - cannot be enable if Harmony Mobile Application is enable. 
* `compromised_behavior` -  Device configuration - response to malicious behavior (configuration for Harmony SDK). 
* `harmony_mobile_sdk_license` - License for Harmony Mobile Sdk (configuration for Harmony SDK) - can contain only English characters, digits, comma, spaces and point. 
* `malware_behavior` - Behavior when App is identified as malicious (configuration for Harmony SDK). 
* `man_in_the_middle_attack` -  Behavior when there is a network man-in-the-middle attack (configuration for Harmony SDK). 
* `os_integrity_compromised` -  Behavior when Device OS is compromised (configuration for Harmony SDK). 
* `suspicious_app` -  Behavior when App is suspected as malicious (configuration for Harmony SDK). 
* `suspicious_enterprise_certificate` - Behavior when a certificate profile has been installed allowing the installing of apps on device from unknown source - iOS only (configuration for Harmony SDK). 


`security` supports the following:

* `session_timeout` - Session timeout - you can choose a unit (day, week, month) in "session-timeout-unit" field. 
* `session_timeout_unit` -  Unit for "session-timeout" numeric value. 
* `activate_passcode_lock` -  Require passcode to the application. 
* `allow_store_credentials` -  Allow storing the credentials on the device. 
* `passcode_profile` -  Passcode Policy object identified by the name.
* `report_jailbroken` -  Issue log when device is detected as jail broken. 
* `block_jailbroken` -  Action upon detection of jail broken devices. 
* `block_3rd_party_keyboard` -  Block 3rd party keyboard. 
* `hide_ssl_connect_anyway_button` -  Hide connect button on critical SSL trust failures. 
