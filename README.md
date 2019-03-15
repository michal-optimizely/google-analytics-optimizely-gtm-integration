# Google Analytics Optimizely Integration Using GTM 2.0

Supporting files for setting up the integration between Optimizely and Google Analytics when done via Google Tag Manager. For a detailed overview of the integration setup refer to [Optimizely's documentation](https://help.optimizely.com/Integrate_Other_Platforms/Integrate_Optimizely_X_with_Google_Universal_Analytics_using_Google_Tag_Manager).

## Content
- *Optimizely Integration Code* (html/js): code used inside the custom HTML Tag named "Optimizely Integration Code".
- *GTM Import Container* (json): JSON file that you can import to GTM to create all the necessary Tags, Triggers and Variables used by this integration.

## Instructions when using the JSON file
1) Download the JSON file
2) Upload it to your GTM using _Admin > Import Container_. Use the *Merge* import option.
3) Update `Optimizely Campaign Decided` & `Optimizely Referrer Override` tags with your own *Google Analytics Setting Variable* (or use the override option to specify the GA Tracking ID)
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

## Updates in v2.0 integration code
The integration code was simplified by using the [getDecisionString method](https://developers.optimizely.com/x/solutions/javascript/reference/index.html#function_getdecisionstring) for collecting the integration string instead of the set of multiple older APIs and concatonating the result together manualy. This also means this integration now adheres to the naming conventions for third-party integrations as outlined [here](https://help.optimizely.com/Integrate_Other_Platforms/Naming_conventions_for_third-party_integrations).  
Lastly, v2.0 also implements [this suggestion](https://gist.github.com/Bigspencey/67931877400e121554c22a979109a496#gistcomment-2679566) to avoid the risk of throwing an error on pages without Optimizely snippet implemented.

## Issues?
If you run into any issues while setting up the integration, reach out to Optimizely via a [Support ticket](https://help.optimizely.com/Account_Settings/File_online_tickets_for_support).

## Credits
[Spencer Smitherman](https://gist.github.com/Bigspencey) is the autor of the original 11-step process and the v1.0 of integration code.  
[Nebo Agency](www.neboagency.com) first came up with the idea of using the _Import Container_ functionality to simplify the process.
