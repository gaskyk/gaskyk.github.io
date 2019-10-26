---
layout: single
title:  "Making the Chrome extension: AI is fancy maths"
date:   2019-10-26 08:38:07 +0000
---
![BBC article about AI]({{site.url}}/assets/BBC_fancy_maths.png)

## Overview

Inspired by a [tweet by Vicki Boykis](https://twitter.com/vboykis/status/1053809224369741826), I thought it would be fun to create a Chrome extension which replaces every instance of *AI* or *artificial intelligence* with *fancy maths*. After all, that is what it is! I describe how to do this below.

## Files required

There are two files required for a simple Chrome extension such as this; `content.js` and `manifest.json`. I looked at a couple of examples of something similar in this [9to5Google article](https://9to5google.com/2015/06/14/how-to-make-a-chrome-extensions/) and this entertaining [Brexit means Breadsticks Github repository](https://github.com/nkhil/Brexit_means_Breadsticks), then adapted these.

You can see that `content.js` requires editing on lines 22 to 24, which takes the text you have on the page, and the text you want to replace it with. You can incorporate regular expressions into these as I have done (`\b` indicates a word boundary).

**Content.js**

```
// This makes an array of everything inside the body tag
var elementsInsideBody = [...document.body.getElementsByTagName('*')];

// A function that loops through every single item
function findAndReplace(){
  elementsInsideBody.forEach(element =>{
    element.childNodes.forEach(child =>{
      if(child.nodeType === 3){
        replaceText(child);
      }
    });

  });
}

// \b accounts for a word boundary (regular expression)
function replaceText (node) {
  let value = node.nodeValue;
  value = value.replace(/\bAI\b/gi, 'fancy maths');
  value = value.replace(/Artificial intelligence/gi, 'Fancy maths');
  value = value.replace(/artificial intelligence/gi, 'fancy maths');
  node.nodeValue = value;
}

window.onload = findAndReplace();
```

The `manifest.json` file only requires editing of the Chrome extension name and description.

**Manifest.json**

```
{
"manifest_version": 2,
	"name": "AI is fancy maths",
	"version": "0.1",
	"description": "Turns every mention of AI on any website into 'fancy maths'",
	"content_scripts": [
		{
			"matches": ["*://*/*"],
			"js": ["content.js"],
			"run_at":"document_end"
		}
	]
}
```

## Enabling the extension

To get the extension working, go to [chrome://extensions/](chrome://extensions/). You will need to ensure *developer mode* is turned on at the top right hand side of the page, as this reveals extra options. In *Load unpacked*, simply select the folder which houses the `content.js` and `manifest.json` files.

![Chrome extension page]({{site.url}}/assets/chrome_extensions.png)

## Get the code

The code is available on [Github](https://github.com/gaskyk/chrome_ext_ai).