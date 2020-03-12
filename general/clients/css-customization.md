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

You can learn more about CSS using sites like [w3school](https://www.w3schools.com/css/default.asp). Below are some very basic details that will let you do rudimentary edits to the ready made modifications below. 

### Colors

CSS supports multiple color formats, most typically hex is used. But simply text works too. To get "yellow" you can simply write "yellow", this will use preset yellow color. For more specificity, see below.

Some examples of hex color codes.

`#5dd000` Green <br> 
`#0000d0` Blue <br>
`#d00000` Red <br>
`#00000058` Transparent black

Go [here](https://htmlcolorcodes.com/color-picker/) for a hex color chart.

### Comments

A section of code or text inbetween `/*` and `*/` indicate a comment, and will be ignored. This allows you to add descriptions for what any particular section of code does to make it easily identifiable. It can also be used to disable code without deleting it. For example

`/*This might be added above code to tell you what it does*/`

### CSS Chaining

CSS can be chained together to modify different sections together. An example of this is the "Border color" mod. It lists elements to be modified, and then ends with a single edit that gets applied to them all.

## Modifications list

To apply any one of these, copy paste the CSS code into the "Custom CSS" field. To use multiple modifications, simply add them one after another into the field. Any applied code will remain in the field. To remove a modification remove the code for it from the field. Changes apply immediately when the settings page is saved, and do not require a restart of the server.

#### Played Indicator:

This will affect the played/watched indicator. Replace the color hex with any value you like.

**Without mod**

![normal](https://user-images.githubusercontent.com/4365015/76570964-20338580-64bf-11ea-9f59-4c4ffa1ec0d5.png)

**Green**

```css
.playedIndicator { background: #5dd000; }
```

![green](https://user-images.githubusercontent.com/4365015/76570998-32152880-64bf-11ea-86cb-f10cf07102b7.png)

**Transparent dark using RGBA hex value**

```css
/*Make watched icon dark and transparent*/
.playedIndicator {background: #00000058;}
```

![transparent](https://user-images.githubusercontent.com/4365015/76571011-39d4cd00-64bf-11ea-911e-62062a55f6e4.png)

#### Make top menu transparent

Self explanatory

```css
/*Top menu transparency*/
.skinHeader.focuscontainer-x.skinHeader-withBackground.skinHeader-blurred {background:none; background-color:rgba(0, 0, 0, 0);}
.skinHeader.focuscontainer-x.skinHeader-withBackground.skinHeader-blurred.noHomeButtonHeader {background:none; background-color:rgba(0, 0, 0, 0);}
```

#### Enlarge tab buttons

Enlarges the tab buttons, suggested, genres, etc. By default they are really damn tiny, especially on mobile.

```css
/*Adjust both "size-adjust" and "size" to modify size*/
.headerTabs.sectionTabs {text-size-adjust: 110%;  font-size: 110%;}
.pageTitle {margin-top: auto; margin-bottom: auto;}
.emby-tab-button {padding: 1.75em 1.7em;}
```

**The enlarged tab buttons and transparent menu look like this:**
![](https://user-images.githubusercontent.com/4365015/76572252-3858d400-64c2-11ea-9b99-c564d8ee7763.png)

#### Minimalistic login page

This looks even better now together with the transparent top menu.

```css
/*Narrow the login form*/
#loginPage .readOnlyContent, #loginPage form {max-width: 22em;}

/*Hide "please login" text, margin is to prevent login form moving too far up*/
#loginPage h1 {display: none}
#loginPage .padded-left.padded-right.padded-bottom-page {margin-top: 50px}

/*Hide "manual" and "forgot" buttons*/
#loginPage .raised.cancel.block.btnManual.emby-button {display: none}
#loginPage .raised.cancel.block.btnForgotPassword.emby-button {display: none}
```

![](https://user-images.githubusercontent.com/4365015/76572504-ed8b8c00-64c2-11ea-8b69-f47ac7386242.png)

#### Stylized episode previews

The episode previews in season view are sized based on horizontal resolution, this leads to a lot of wasted space on the episode summary and a high vertical page requiring a lot of scrolling to browse. This code reduces the height of episode entries to reduce the need for vertical scrolling on large screens.

```css
/*Size episode preview images in a more compact way*/
.listItemImage.listItemImage-large.itemAction.lazy {height: 110px;}
.listItem-content {height: 115px;}
.secondary.listItem-overview.listItemBodyText {height: 61px; margin: 0;}
```

![](https://user-images.githubusercontent.com/4365015/76573431-51fb1b00-64c4-11ea-936e-d96502cb753d.png)

#### Stylized and smaller cast info

This will drastically change the style of cast info. Into something very similar to how plex does it. The Purple Haze theme already has rounded cast info, but at the same large size as everything else, this override will lead to somewhat smaller thumbnails, and also works with all other themes.

```css
/*Shrink and square (or round) cast thumnails*/
#castContent .card.overflowPortraitCard.personCard.card-hoverable.card-withuserdata {width: 4.2cm !important; font-size: 90% !important;}
#castContent .card.overflowPortraitCard.personCard.card-withuserdata {width: 4.2cm !important; font-size: 90% !important;}

/*Correct image aspect ratio behaviour, set border-radius to zero for square tiles*/
#castContent .cardContent-button.cardImageContainer.coveredImage.cardContent.cardContent-shadow.itemAction.lazy {background-size: cover; !important; border-radius: 2.5cm;}
#castContent .cardContent-button.cardImageContainer.coveredImage.defaultCardBackground.defaultCardBackground1.cardContent.cardContent-shadow.itemAction {background-size: cover; !important; border-radius: 2.5cm;}
#castContent .cardContent-button.cardImageContainer.coveredImage.defaultCardBackground.defaultCardBackground2.cardContent.cardContent-shadow.itemAction {background-size: cover; !important; border-radius: 2.5cm;}
#castContent .cardContent-button.cardImageContainer.coveredImage.defaultCardBackground.defaultCardBackground3.cardContent.cardContent-shadow.itemAction {background-size: cover; !important; border-radius: 2.5cm;}
#castContent .cardContent-button.cardImageContainer.coveredImage.defaultCardBackground.defaultCardBackground4.cardContent.cardContent-shadow.itemAction {background-size: cover; !important; border-radius: 2.5cm;}
#castContent .cardContent-button.cardImageContainer.coveredImage.defaultCardBackground.defaultCardBackground5.cardContent.cardContent-shadow.itemAction {background-size: cover; !important; border-radius: 2.5cm;}
#castContent .cardScalable {width: 3.8cm !important; height: 3.8cm !important; border-radius: 2.5cm;}
#castContent .cardOverlayContainer.itemAction {border-radius: 2.5cm;}

/*Center the mouseover buttons*/
#castContent .cardOverlayButton-br {bottom: 4%; right: 15%; width: 70%;}
#castContent .cardOverlayButton.cardOverlayButton-hover.itemAction.paper-icon-button-light {margin:auto;}
```

![](https://user-images.githubusercontent.com/4365015/76574436-f1b8a900-64c4-11ea-8382-1b207f0d872f.png)

#### Background Color

```css
.backgroundContainer, .dialog, html { background-color: #0fd0d0; }
```

#### Darken the background

This darkens the background on blue radiance/purple haze, edit the percentage depending how dark you want it. Lower is darker.

```css
/*Darken background, only works with blue radiance*/
.backgroundContainer {background-color: #000000; filter: brightness(50%);}
```

#### Right Header

```css
.headerRight { color: yellow; }
```

![image](https://user-images.githubusercontent.com/20715731/73962770-0d84ca00-48dd-11ea-9b50-563f8b4aa33b.png)

#### Console Panel

```css
.mainDrawer-scrollContainer { color: yellow; }
```

![image](https://user-images.githubusercontent.com/20715731/73963663-c13a8980-48de-11ea-9342-d1e89690e7b1.png)

#### General Page

```css
.dashboardGeneralForm { color: yellow; }
```

![image](https://user-images.githubusercontent.com/20715731/73964979-49ba2980-48e1-11ea-8ddf-51e1c54e32d4.png)


#### Border Color

This will change the border color for text fields.

```css
.emby-input, .emby-textarea, .emby-select { border-color: #fdbe7d; }
```

![image](https://user-images.githubusercontent.com/20715731/73950017-39965000-48c9-11ea-9c0e-7687420a282e.png)

#### Full Header Mod

```css
.skinHeader, .mainDrawer, .emby-input, .emby-textarea, .emby-select, .navMenuOption-selected, .cardBox, .paperList { 	background: #ff9475; }
```

![image](https://user-images.githubusercontent.com/20715731/73949397-5f6f2500-48c8-11ea-9eca-bc1eb61f1281.png)

#### Hotdogs and Catsup:

An example of a color theme.

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

**Sample:**

![image](https://user-images.githubusercontent.com/20715731/73948929-a3adf580-48c7-11ea-8bf1-eaaba2873be7.png)

# Community Links

Some links to places where custom CSS has been discussed and shared.

https://www.reddit.com/r/jellyfin/comments/fgmu6k/custom_css_updated_for_1050/

https://www.reddit.com/r/jellyfin/comments/crxqk5/easy_jellyfin_custom_css/

https://emby.media/community/index.php?/topic/18046-custom-css-with-emby-web-app/
