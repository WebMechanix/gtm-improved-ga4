# Improved GA4 Tag Template for GTM
A GA4 tag template with an improved UI which allows for greater flexibility than the provided GA4 tag templates from Google.

## Preface
This tag template won't be for everyone. This template is geared more toward GTM power users with advanced implementation practices that require a more robust UI for how variables are used inside of GA4 config and event commands. This tag template took inspiration from [Simo Ahava's original Facebook Pixel tag template](https://www.simoahava.com/custom-templates/facebook-pixel/) that used a similar UI pattern. GA4 and Facebooks data model are similar (at least in a sense of how their JS APIs work) so this pattern made sense to me.

## What it does

1. Loads the gtag.js library
2. Registers an arguments queue on the the default `dataLayer` global.
3. Implements a better UI that accepts a variable that returns a JavaScript object with the fields/parameters/properties you want to set for either a config or event tag type. This object will be merged with any additional fields you set via a normal key:value table. Any object key conflicts will always use the explicitly defined value in the key:value table.
4. (Experimental) Implements a better UI for setting GA4 tags to specific groups for use with the [`gtag()` groups and routes API](https://developers.google.com/tag-platform/gtagjs/routing). This can greatly reduce tag duplication when sending data to more than one measurement ID for more complex implementations.
5. (Experimental) Provides simple UI to add common values to the event payload without explictly defining them.

## Limitations

### dataLayer
Google's Sandboxed Javascript doesn't allow for the ability to customize what global variable is used for the arguments queue. If you need to specify an non-default dataLayer global, you will need to edit the template file `dataLayerName` constant to your needs.

### gtag.js is loaded from www.googletagmanager.com
Google's Sandboxed Javascript doesn't allow for the ability to customize what domain and path is used to loag the `gtag.js` library. If you wish to load the `gtag.js` file in a non-default way (e.g. proxy through a SGTM container or other 1st party means) you will need to edit the template file at this time.

### Built-in consent checks
This tag template has not yet been adjusted to use built in consent checks for things like consent-mode that the default GA4 tag templates do.
