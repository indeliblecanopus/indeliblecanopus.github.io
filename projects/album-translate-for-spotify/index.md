---
layout: default
tags: [appscript, spotify-api]
---

# Album Translate for Spotify

Google Workspace Add-on to help you translate Spotify® album tracks and search within the artist's translated discography. 
This add-on is free and open-source project provided under MIT license. You can find the source code on [Github](https://github.com/indeliblecanopus/album-translate-for-spotify){:target="_blank"}.


## Premise

Sometimes, I try to (re)search Jazz artists to listen to on Spotify and often need to look through the artist's albums, quickly spot familiar standards and easily add them to the queue. However, many artists list their track names in different languages, and copy-pasting track names into translation services seems quite a time waste, so decided to write this add-on.

## Features


The add-on currently supports two core functions, which, going forward, we'll refer to as `Translate` and `Search` features.


### Translate Feature


`Translate` feature is supposed to be utilized when users need to translate all track names for a given album and display them in the add-on user GUI. You only need to insert an album URL in the translate field and click the `Translate` button to display results. 


This function utilizes Google Translate service which, so corresponding daily quota limits apply as listed [here](https://developers.google.com/apps-script/guides/services/quotas){:target="_blank"}. Add-on tries to minimize translate calls by concatenating track names per album, however, sometimes this does not yield correct results and the add-on reverts back to translating each track name in the album one by one.    


**Note**: Currently, this feature is set to target only English translation.


### Search Feature


`Search` feature is meant to be utilized when users want to search for a given track name in an artist's discography, which contains some albums listed in non-English language. You will need to provide an artist URL and track name to search for this function, however, it does not display results immediately. The search is run as the background process that ultimately is supposed to store results internally, which later can be displayed by the user with the `Show Results` button.


Consider that, this feature similar to the `Translate` utilizes quota-limited service and uses relatively much more translation calls depending on the size of the artist's discography. In case the `Search` background task fails, the corresponding message will be displayed when you click Show Results. Otherwise, all translated and matched track names will be displayed.  


**Note**: Currently, this feature is set to target only English translation. Hence, the track name to search should be specified in English.


### Playback Feature (Optional)


`Playback` feature is optional and users can choose to enable it by marking a corresponding checkbox initially, during the add-on authorization. The feature can be utilized to add multiple tracks to the current player queue. You can choose tracks from the displayed results of either `Translate` or `Search` features.


**Note**: This feature is limited (by Spotify) to only users with Premium subscription plans.


## Privacy Policy

You can check privacy policy for this add-on [here](privacy-policy).

