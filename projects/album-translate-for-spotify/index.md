---
layout: default
tags: [appscript, spotify-api]
---

# Album Translate for Spotify

Google Workspace Add-on to help you translate Spotify® album tracks and search within the artist's translated discography.
This add-on is free and open-source project provided under MIT license. You can find the source code on [Github](https://github.com/indeliblecanopus/album-translate-for-spotify).

## Premise

Sometimes, I try to (re)search Jazz artists to listen to on Spotify and often need to look through the artist's albums, quickly spot familiar standards and easily add them to the queue. However, many artists list their track names in different languages, and copy-pasting track names into translation services seems quite a time waste, so decided to write this add-on.

## Features

The add-on currently supports two core functions, which, going forward, we'll refer to as `Translate` and `Search` features.

### Translate Feature

`Translate` feature is supposed to be utilized when users need to translate all track names for a given album and display them in the add-on GUI. You only need to insert an album URL in the corresponding text input field and click the `Translate` button to display results.

This function utilizes Google Translate service for which corresponding daily quota limits apply as listed [here](https://developers.google.com/apps-script/guides/services/quotas). Add-on tries to minimize translate service calls by concatenating track names per album, however, sometimes this does not yield correct results and the add-on reverts back to calling API for each track name in the album one by one.

**Note**: Currently, this feature is set to target only English translation.

### Search Feature

`Search` feature is meant to be utilized when users want to search for a given track name within artist's discography in non-English language. You will need to provide an artist URL and track name to for this feature. Note though, this feature does not display results immediately and the search is run as a background task the results of which can later be displayed by the user with the `Show Results` button. You can close the add-on afte search task is submitted and open at a later time to display results.

Consider that, this feature similar to the `Translate` utilizes quota-limited API service and uses much more translation calls depending on the size of the artist's discography. In case the `Search` background task fails, the corresponding message will be displayed when user clicks `Show Results` button. If taks is successful, all translated and matched track names will be displayed.

**Note**: Currently, this feature is set to target only English translation. Hence, the track name to search should be specified in English.

### Playback Feature (Optional)

`Playback` feature is optional and users can choose to enable it by marking a corresponding checkbox during the initial add-on authorization process. This feature can be utilized to add multiple tracks to the queue of the active Spotify player. You can select which tracks to add to the queue from the results of either `Translate` or `Search` features.

**Note**: This feature is limited (by Spotify) to users with Premium subscription plans.

### Library Feature (Optional)

`Library` feature is optional and users can choose to enable it by marking a corresponding checkbox during the initial add-on authorization process. The feature can be utilized to add multiple tracks to the user's library. You can select tracks from the results of either `Translate` or `Search` features.

## Privacy Policy

You can check privacy policy for this add-on [here](privacy-policy).
