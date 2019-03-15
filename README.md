# Google Analytics Optimizely Integration Using GTM 2.0

Supporting files for setting up the integration between Optimizely and Google Analytics when done via Google Tag Manager. For a detailed overview of the integration setup refer to [Optimizely's documentation](https://help.optimizely.com/Integrate_Other_Platforms/Integrate_Optimizely_X_with_Google_Universal_Analytics_using_Google_Tag_Manager).

## Content
- *Optimizely Integration Code* (html/js): code used inside the custom HTML Tag named "Optimizely Integration Code".
- *GTM Import Container* (json): JSON file that you can import to GTM to create all the necessary Tags, Triggers and Variables used by this integration.

## Instructions when using the JSON file
1) Download the JSON file
2) Upload it to GTM using _Admin > Import Container_
3) Update `Optimizely Campaign Decided` & `Optimizely Referrer Override` with your own Google Analytics Setting Variable (or use the override option to specify the GA Tracking ID)
4) Publish the workspace

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

## Issues?
If you run into any issues while setting up the integration, reach out to Optimizely via a [Support ticket](https://help.optimizely.com/Account_Settings/File_online_tickets_for_support).

## Credits
[Spencer Smitherman](https://gist.github.com/Bigspencey) is the autor of the original 11-step process and the v1.0 of integration code
[Nebo Agency](www.neboagency.com) first came up with the idea of using the _Import Container_ functionality to simplify the process.
