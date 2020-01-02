# Optimizely & Google Analytics via GTM analytics integration

Supporting files for setting up the integration between Optimizely and Google Analytics when GA is implemented via Google Tag Manager. For a detailed overview of the integration setup refer to [Optimizely's documentation](https://help.optimizely.com/Integrate_Other_Platforms/Integrate_Optimizely_X_with_Google_Universal_Analytics_using_Google_Tag_Manager).

## Content
- *Optimizely Integration Code* (html/js): code used inside the custom HTML Tag named "Optimizely Integration Code". Included here only for reference purposes.
- *GTM Import Container* (json): a JSON file that you can import into GTM. It includes all the necessary Tags, Triggers and Variables used by this integration.

## Instructions when using the JSON file
1) Download the *gtm-import-container.json* file.
2) Upload it to your GTM using _Admin > Import Container_. Use the *Merge* import option to avoid overwriting and/or deleting any existing properties. 
   If you're updating the integration from previous version, select the option to 'Overwrite conflicting tags, triggers and variables.' (Note this won't fully work if updating from version 1.0 due to some discrepancies in the names of individual properties; you will need to manually delete the old properties in that case.)
3) `Optimizely Campaign Decided` & `Optimizely Referrer Override` tags need to be updated to know what GA tracking ID they should be using. 
   [repeat this for both tags] Open the tag settings and find the **Google Analytics Settings** field. You have two options:
  * You can use the [Google Analytics Setting Variable](https://support.google.com/tagmanager/answer/9207621?hl=en). This variable needs to be created manually and populated with the GA tracking ID, it's not provided by default. 
  If you select this option, make sure to leave the **Tracking ID* field right below the *Enable overriding settings in this tag* option empty.
  * If you don't have/don't want to use the Google Analytics Setting Variable, keep the *Enable overriding settings in this tag* option checked and enter your own GA tracking ID in the **Tracking ID** field right below (it will be pre-populated with a value 'UA-000000-0' - this is not correct and needs to be overwritten with your own GA tracking ID).
4) Publish the workspace. 
5) In Optimizely, enable the Google Analytics integration for any experiment you want to analyze in GA.

## Properties created in GTM via this import

Tags: 
- `Optimizely Campaign Decided`
- `Optimizely Integration Code`
- `Optimizely Referrer Override`

Triggers:
- `Optimizely Campaign Decided`
- `Optimizely Referrer Override`

Variables:
- `optimizely-dimension-number`
- `optimizely-dimension-value`
- `optimizely-referrer`

## Changelog
- **Version 2.0:**
  - The integration code was simplified by using the [getDecisionString method](https://developers.optimizely.com/x/solutions/javascript/reference/index.html#function_getdecisionstring) for collecting the integration string instead of the set of multiple older APIs and concatonating the result together manualy. This also means this integration now adheres to the naming conventions for third-party integrations as outlined [here].(https://help.optimizely.com/Integrate_Other_Platforms/Naming_conventions_for_third-party_integrations).  
  - Implemented [this suggestion](https://gist.github.com/Bigspencey/67931877400e121554c22a979109a496#gistcomment-2679566) to avoid the risk of throwing an error on pages without Optimizely snippet implemented.
- **Version 2.1:**
  - Removed automatic logging (no impact on the functionality of the integration).
  - Removed custom variable unrelated to this integration from the exported GTM container.

## Issues?
If you run into any issues while setting up the integration, reach out to Optimizely via a [Support ticket](https://help.optimizely.com/Account_Settings/File_online_tickets_for_support).

## Credits
[Spencer Smitherman](https://gist.github.com/Bigspencey) is the autor of the original 11-step process and the v1.0 of integration code.  
[Nebo Agency](www.neboagency.com) first came up with the idea of using the _Import Container_ functionality to simplify the process.
