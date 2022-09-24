# Improved GA4 Tag Template for GTM
A GA4 tag template with an improved UI which allows for greater flexibility than the provided GA4 tag templates from Google.

## Preface
This tag template won't be for everyone. This template is geared more toward GTM power users with advanced implementation practices that require a more robust UI for how variables are used inside of GA4 config and event commands. This tag template took inspiration from Simo Ahava's original Facebook Pixel tag template that used a similar UI pattern. GA4 and Facebooks data model are similar (at least in a sense of how their JS APIs work) so this pattern made sense to me.

## What it does

1. Loads the gtag.js library
2. Registers an arguments queue on the the default `dataLayer` global. **Please note** - Google's Sandboxed Javascript doesn't allow for the ability to customize what global variable is used for the arguments queue. If you need to specify an non-default dataLayer global, you will need to edit the template file `dataLayerName` constant to your needs.
3. Implements a better UI that accepts a variable that returns a JavaScript object with the fields you want to set. This object will be merged with any additional fields you set via a normal key:value table. Any object key conflicts will always use the explicitly defined value in the key:value table.
4. Implements a better UI for setting GA4 tags to specific groups for use with the `gtag()` groups and routes API. This can greatly reduce tag duplication when sending data to more than one measurement ID for more complex implementations.
