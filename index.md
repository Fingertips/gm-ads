# GaultMillau 2018 ad guidelines

Even though this document has been carefully prepared, the correctness of the information provided can not be guaranteed and is subject to change. Please contact Thijs van der Vossen, thijs@fngtps.com in case you have any questions or concerns.

## Overview

The GaultMillau 2018 app will include containers for two different ad elements:

### 1. Home banner

The “home banner” element is included at the bottom of the app’s home view. When the user taps this ad element, a pre-defined URL will open in Mobile Safari.

Conceptually, this ad element can function as a “call to action” or a “start button” for the user to engage with a web-based experience outside of the app.

### 2. Editorial ad

The “editorial ad” element is included as a full page ad in the editorial content section of the app. 

Conceptually, this ad element functions in much the same way as a full-page magazine advertisement.

## Design considerations

Each ad element will be loaded from a pre-defined URL in an iOS WebView when the user navigates to a screen in the app that contains an ad element.

### Flexible containers requiring responsive design

Because of the large number of possible viewport dimensions*, as well as the dynamic nature of a modern iOS application using Auto Layout, no fixed viewport sizes can be given for the ad element viewport containers.

Both ads should therefore be designed and implemented as fully responsive elements using modern web development techniques.

The content for the “Home banner” element should display well inside a viewport container sized at any aspect ratio between 2:1 and 6:1.

![Home banner aspect ratios](home_banner.png)

The content for the “Editorial ad” element should display well inside a viewport container sized at any aspect ratio between 1:4 and 4:3

![Home banner aspect ratios](editorial_ad.png)

*Apple currently offers iOS devices with six different logical resolutions that can be used in both portrait and landscape orientation as well as a multitude of additional resolutions resulting from the Slide Over and Split View multitasking features.

### Motion and animation

The home banner element is included at the bottom of the app’s home view which contains its primary navigational elements. Motion can of course be used to draw attention to the element, but should not distract from the usage of the app itself.

Subtle animation cues could be used to draw attention to the ad element and to provide hints that the element is tappable.

The editorial ad element will be included as a single full page in between multiple pages of editorial content. As such, the visual experience should be reasonably straightforward in terms of motion, for example by using a minimal looped animation to provide visual interest or set the mood.

It’s best to think of this element as a natural extension of the traditional full-page glossy magazine print ad. Don’t think of this element as a TV commercial, web video ad, or fully-fledged interactive experience.

### Initialization

The ad elements might be pre-loaded long before they are presented to the user. Do not rely on page load events to trigger one-time animation because playback of these will likely be finished before the ad is presented to the user.

Don’t use any “page buildup” effects as this will result in a suboptimal user experience combined with the existing view and page navigation transitions already provided by the app itself. 

### Interactivity

The user will not be able to interact with the content of the ad elements.

## Deliverables

The content for the ad element will be loaded dynamically as web resources by the app when needed. Hosting of these files and assets is the responsibility of the advertiser.

The following three URLs should be delivered to the app developers:

1. The URL where the HTML page for the “Home banner” element is available.
2. The URL where the HTML page for the “Editorial ad” element is available.
3. The URL that should be opened in Mobile Safari when the “Home banner” is tapped.

For 1 and 2, please provide absolute URLs that can be loaded directly and that don’t require any further redirection.

## Implementation

Use modern web technology standards such as HTML5, CSS3, SVG, PNG, JPEG, and WOFF.

Animation is best implemented using hardware accelerated CSS3 transformations and transition. Don’t use JavaScript for frame-based animation or other resource-intensive techniques. 

Don’t add video playback or audio effects. Do not use WebGL.

### Suggestions and recommendations

The following suggestions and recommendations are non-normative, but might help with your implementation.

* Make sure to test in Mobile Safari on actual iPhone and iPad hardware devices. Don’t rely on testing in desktop Safari or the iOS simulator only.
* Use desktop Safari’s “Responsive Design Mode” to test how your responsive implementation adjusts to different viewport sizes.
* Do not attempt to render bitmap graphics at 1:1 physical resolution. Try to find a good balance between visual quality and file size.
* Use the `vw` and `vh` CSS3 relative units to size text and other elements relative to the width and height of the viewport.
* Use the `vmin` and `vmax` CSS3 relative units to make your layout adjust to extreme changes in viewport aspect ratio (e.g. going from portrait to landscape).
* Take file size and loading performance into consideration. Shorter load times result in better engagement. Compress image assets using [ImageOptim](https://imageoptim.com/mac). Try reducing the size of transparent PNG images using [ImageAlpha](https://pngmini.com).
* Use web fonts instead of text rendered as bitmap graphics. Test your implementation for accessibility, for example using VoiceOver.
* Limit your use of CSS media queries. If you use CSS media queries, only use expressions that target viewport size (such as `min-width`, `max-width`, `min-height`, and `max- height`). Do not use expressions that target device dimensions or device orientation.