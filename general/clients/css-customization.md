---
uid: clients-css-customization
title: CSS Customization
---


# CSS Customization

In general settings, the "Custom CSS" field can be used to enter any override, that will then apply to the CSS stylesheet of Jellyfin.

[Custom CSS](https://developer.mozilla.org/en-US/docs/Web/CSS) provides interface customization such as changing colors, layout, item size and behavior. Below is a list of various modifications that can be applied. The CSS modifications work on both the web client, and the android app. The code will apply in the order that it is written so code can override previously stated custom CSS. To learn more see [CSS Specificity](https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity). To implement these changes, go to Dashboard > General > Custom CSS. An additional source for specificity is [specifishity](https://specifishity.com/).

![image](https://user-images.githubusercontent.com/20715731/73392971-d1cc7d80-42a8-11ea-8552-3d311655ea37.png)

If you have little or no experience with CSS, various resources and tutorials can be found online, together with using the below modifications as examples it is quite easy to get started making your own changes to your Jellyfin instance.


## General information about CSS

You can learn more about CSS using sites like [w3school](https://www.w3schools.com/css/default.asp). Below are some very basic details the will let you do rudimentary edits to the ready made modifications below. 

### Colors Codes:

Below are a few examples of hex color codes. These express RGB (sometimes RGBA) color using three (or a fourth for alpha) hex values. Go here [here](https://htmlcolorcodes.com/color-picker/) for a hex color chart.

Green: `#5dd000`<br>
Blue: `#0000d0`<br>
Red: `#d00000`<br>

### Comments:

A section of code or text inbetween `/*` and `*/` indicate a comment, and will be ignored. This allows you to add descriptions for what any particular section of code does to make it easily identifiable. It can also be used to disable code without deleting it. For example

`/*This might be added above code to tell you what it does*/`

## List of modifications

To apply any one of these, copy paste the CSS code into the "Custom CSS" field. To use multiple modifications, simply add them one after another into the field. Any applied code will remain in the field. To remove a modification remove the code for it from the field. Changes apply immediately when the settings page is saved, and do not require a restart of the server.

#### Modifying played Indicator:

The below code will affect the played indicator. Replace the color hex with any value you like.

`.playedIndicator { background: #5dd000; }`

Before:

![image](https://user-images.githubusercontent.com/20715731/73392328-97aeac00-42a7-11ea-817f-7234b8a78783.png)

Green Mod:

![image](https://user-images.githubusercontent.com/20715731/73392302-86659f80-42a7-11ea-9a9a-222cbbe466c6.png)

A color with RGBA data will also work.

`/*Make watched icon dark and transparent*/
.playedIndicator {background: #00000058;}`

#### Background Color:

`.backgroundContainer, .dialog, html { background-color: #0fd0d0; }`

#### Right Header

`.headerRight { color: yellow; }`

![image](https://user-images.githubusercontent.com/20715731/73962770-0d84ca00-48dd-11ea-9b50-563f8b4aa33b.png)

#### Console Panel

`.mainDrawer-scrollContainer { color: yellow; }`

![image](https://user-images.githubusercontent.com/20715731/73963663-c13a8980-48de-11ea-9342-d1e89690e7b1.png)

#### General Page

`.dashboardGeneralForm { color: yellow; }`

![image](https://user-images.githubusercontent.com/20715731/73964979-49ba2980-48e1-11ea-8ddf-51e1c54e32d4.png)

### CSS Chaining

CSS can be chained together to modify different sections together.

#### Border Color

`.emby-input, .emby-textarea, .emby-select { border-color: #fdbe7d; }`

![image](https://user-images.githubusercontent.com/20715731/73950017-39965000-48c9-11ea-9c0e-7687420a282e.png)

#### Full Header Mod

`.skinHeader, .mainDrawer, .emby-input, .emby-textarea, .emby-select, .navMenuOption-selected, .cardBox, .paperList { 	background: #ff9475; }`

![image](https://user-images.githubusercontent.com/20715731/73949397-5f6f2500-48c8-11ea-9eca-bc1eb61f1281.png)

#### Hotdogs and Catsup:

```css
.skinHeader, .mainDrawer, .emby-input, .emby-textarea, .emby-select, .navMenuOption-selected, .cardBox, .paperList {
	background: #ff9475;
}

.emby-input, .emby-textarea, .emby-select {
	border-color: #fdbe7d;
}

.backgroundContainer.withBackdrop, .backdropContainer, .backgroundContainer {
	background: #fdbe7d;
}

#myPreferencesMenuPage .listItemBodyText,
.emby-tab-button[data-index="0"],
#myPreferencesMenuPage > div > div > div > a:nth-child(odd),
.button-submit,
.mainAnimatedPage *:nth-child(odd),
.dashboardGeneralForm *:nth-child(odd),
.mainDrawer-scrollContainer *:nth-child(odd),
.headerRight *:nth-child(odd) {
	color: red;
}

#myPreferencesMenuPage .listItemIcon,
.emby-tab-button[data-index="1"],
#myPreferencesMenuPage > div > div > div > a:nth-child(even),
.mainAnimatedPage *:nth-child(even),
.dashboardGeneralForm *:nth-child(even),
.mainDrawer-scrollContainer *:nth-child(even),
.headerRight *:nth-child(even)
.cancel {
	color: yellow;
}
```

Sample:

![image](https://user-images.githubusercontent.com/20715731/73948929-a3adf580-48c7-11ea-8bf1-eaaba2873be7.png)

More Community Links:

https://www.reddit.com/r/jellyfin/comments/bqa065/sharing_my_custom_css_for_modifying_the_ui/

https://www.reddit.com/r/jellyfin/comments/crxqk5/easy_jellyfin_custom_css/

https://emby.media/community/index.php?/topic/18046-custom-css-with-emby-web-app/
