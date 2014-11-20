# A Google Spreadsheet-Powered Slider

A super simple, easy-to-edit slider created from a Google spreadsheet. Move through slides by clicking, using left and right arrow keys, or (on mobile) swiping. Works well as a photo slideshow embedded inline. Here's an example slide from the wild:

<p align="center">
  <img width="50%" src="https://raw.githubusercontent.com/motherjones/simple-slider/master/img/screenshot.png" alt="screenshot"/>
</p>

## Examples in the Wild

["This Newsman Ink That Runs Through My Veins": An interactive photoessay about the Philadelphia Inquirer](http://www.motherjones.com/media/2013/07/interactive-philadelphia-inquirer-newspaper-photo-will-steacy)

[Why Your Supermarket Sells Only 5 Kinds of Apples](http://www.motherjones.com/environment/2013/04/heritage-apples-john-bunker-maine)

[Your Smartphone's Dirty, Radioactive Secret](http://www.motherjones.com/environment/2012/11/rare-earth-elements-iphone-malaysia)

## How it works

*MoJo staffers:* Before you get started, following [these instructions](https://github.com/motherjones/story-tools#starting-a-new-project).

In its simplest form, this slider is a collection of slides, where each slide consists of a `title`, `middle image`, and some caption `text`. Accordingly, you'll need to create a Google Spreadsheet with a `title`, `middle image`, and `text` column, filling each row with your story content. We'll go over how to set up and format your spreadsheet below, but here's a snapshot of what your data should look like:

|**title**|**middle image**|**text**|
|---|------|----|
|`Baldwin` | `http://assets.motherjones.com/environment/2013/04/baldwin.jpg` | `One of the most popular apples in the US until freakish winter weather in 1933-34 knocked it into obscurity. <span class="credit">USDA</span>`|

## Set up your Google Spreadsheet

*MoJo staffers:* Make a copy of [this template]( https://docs.google.com/spreadsheet/pub?key=0AswaDV9q95oZdDZFSWpEZHlNRUlHWmVqa3JqalZsZXc&output=html) and move the copy into the relevant beat folder in the Mother Jones Google Drive. Rename the spreadsheet as you see fit. Change the owner of the spreadsheet to MoJo Data in `Share > Advanced`.

In order for the slider to be able to read your spreadsheet, you'll need to make your new spreadsheet public. Go to `File` and click on `Publish to the web,` then click on `Start publishing`. 

A URL will appear. It will something like this: `https://docs.google.com/spreadsheet/pub?key=0Arenb9rAosmbdG5GWHFXbWJlN1hTR2ZmN3lZMVZkOHc&output=html`

Copy that link. This is your spreadsheet ID or url, which you will use to connect your spreadsheet to the slider.

## Modify your project files

*MoJo staffers:* By now you should have a local clone of this project repo on your machine, by following [these instructions](https://github.com/motherjones/story-tools#starting-a-new-project)

**In index.html (required):**

Paste the link you just copied into your html file, in the place of public_spreadsheet_url. The code you are looking for in the index.html file looks like this:

```

$('#slideshow').slideshow('public_spreadsheet_url');

```

**In style.css (optional):**

You're welcome to use our default slider style (found in demo/style.css), or style to your own taste. Again, we do think the slider looks nicest if you use only one of the image OR video columns (the demo uses only `middle image`).

## Formatting your spreadsheet data

The `title`, `text` columns should have plain text or html. You can add hyperlinks and styled text—for source credits—by wrapping them in <a href=""></a> and <span class="credit"></span>, as shown in the [How it works](https://github.com/motherjones/simple-slider/blob/master/README.md#how-it-works) section.

The `source` column is for *MoJo staffers* when bulletproofing our data and tracking the origin of each row's data. You're welcome to adopt this practice.

Once you've got the data formatted properly. Now you're ready to stage the slider.

## Staging the inline-slider (for MoJo staff only)

*MoJo staffers:* When you're done, upload to s3 and embed in the shell [(how to)](https://github.com/motherjones/story-tools#starting-a-new-project).

## Use JSON instead (optional)

If your prefer, you can store your slider data in a JSON file instead of a Google spreadsheet. Simply model your JSON after this example:

```

var slideshow = jQuery.slideshow([
	{
		backgroundimage: 'http://i.imgur.com/QYMjo.jpg',
		topimage: 'http://i.imgur.com/QYMjo.jpg',
		topvideoembed: '<iframe width="960" height="720" src="http://www.youtube.com/embed/TZzzXutPfks" frameborder="0" allowfullscreen></iframe>',
		title: 'Goats and Kittens That Faint',
		middleimage: 'http://i.imgur.com/QYMjo.jpg',
		middlevideooembed: '<iframe width="960" height="720" src="http://www.youtube.com/embed/TZzzXutPfks" frameborder="0" allowfullscreen></iframe>',
		text: 'Awwww-inspiring animals',
		bottomimage: 'http://i.imgur.com/QYMjo.jpg',
		bottomvideoembed: '<iframe width="960" height="720" src="http://www.youtube.com/embed/TZzzXutPfks" frameborder="0" allowfullscreen></iframe>'
	}	
]);

```

## Questions?

Hit us up by email, or Twitter: [@jaeahjlee](https://twitter.com/jaeahjlee) or [@tasneemraja](https://twitter.com/tasneemraja)

## License
Copyright (c) 2012 Mother Jones
