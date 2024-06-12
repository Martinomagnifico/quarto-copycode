# CopyCode

## For Quarto

A quarto extension for [Reveal.js](https://revealjs.com) that automatically shows a 'copy' button in code blocks.

[![Screenshot](https://martinomagnifico.github.io/reveal.js-copycode/screenshot.png)](https://martinomagnifico.github.io/quarto-copycode/demo.html)

In presentations we can show blocks of code. This plugin for Reveal.js adds a 'copy' button to each of those. Because you might just want to copy a piece of code during such a presentation.

[Demo](https://martinomagnifico.github.io/quarto-copycode/demo.html)

It's easy to set up. If your code blocks are set up like this:

```html
<pre>
  <code>
    Here is the code
  </code>
</pre>
```

…then install the plugin and a 'Copy' button is automatically added to any `pre` code block.

Quarto already has copy-code buttons, but those are quite small, and thus not very visible for presentations. This extension replaces those buttons for use in (Reveal.js) Quarto presentations.


## Basics

There are really only three steps:

1. Install CopyCode
2. Copy your code from a code block
3. Paste your code somewhere



## Setup

### Installation with Quarto

```console
quarto add martinomagnifico/quarto-copycode
```

### Other installations

The original plugin is also published to npm. To use CopyCode in a normal Reveal.js installation, or for more information about the original plugin, go to [Martinomagnifico/reveal.js-copycode](https://github.com/Martinomagnifico/reveal.js-copycode)


### Styling

The styling of CopyCode is automatically inserted from the included CSS styles, either loaded through NPM or from the plugin folder.

If you want to change the CopyCode style, you do a lot of that via the Reveal.js options. Or you can simply make your own style and use that stylesheet instead. Linking to your custom styles can be managed through the `csspath` option of CopyCode.


## Now change it

#### Change the visibility per element:

```` md
```{.html data-cc="false"}
<code>
    Here is the code
</code>
```
````

Or show only on hover:

```` md
```{.html data-cc="hover"}
<code>
    Here is the code
</code>
```
````
This can also be set globally. See [Global options](#global-options) below.


#### Change the display of icons per element:

Icons only:

```` md
```{.html data-cc-display="icons"}
<code>
    Here is the code
</code>
```
````
Or both text and icons:

```` md
```{.html data-cc-display="both"}
<code>
    Here is the code
</code>
```
````

This can also be set globally. See [Global options](#global-options) below.


#### Change the text per element:

```` md
```{.html data-cc-copy="Copy HTML" data-cc-copied="Done"}
<code>
    Here is the code
</code>
```
````

This can also be set globally. See [Global options](#global-options) below.




## Global options

There are a few options that you can change in the YAML options. The values below are default and do not need to be set if not changed.

``` yaml
format:
  revealjs:
    //...
    copycode:
      button: 'always'
      display: "text"
      text:
        copy: "Copy"
        copied: "Copied!"
      plaintextonly: true
      timeout: 1000
      style:
        copybg: "orange"
        copiedbg: "green"
        copycolor: "black"
        copiedcolor: "white"
        copyborder: ""
        copiedborder: ""
        scale: 1
        offset: 0
        radius: 0
      tooltip: true
      iconsvg:
        copy: ""
        copied: ""
      csspath: ""
```

* **`button`**: Set to `always` by default. But can be set to `hover` to only show the button on hover.
* **`display`**: The copy buttons display only text by default, but this setting can be changed to `icons` to only show icons (based on the GitHub icons) or to `both` to show both text and icons.
* **`text`**: This is an object that contains options for text in the buttons
	* **`copy`**: The text for each copy button.
	* **`copied`**: The text for each copy button when the copy action is successful.
* **`plaintextonly`**: Set this to false to allow copying of rich text and styles.
* **`timeout`**: The time in milliseconds for the "Copied!"-state to revert back to "Copy".
* **`style`**: This is an object that contains options for text in the buttons
	* **`copybg`**: The background color.
	* **`copiedbg`**: The background color in the Copied state.
	* **`copycolor`**: The text color.
	* **`copiedcolor`**: The text color in the Copied state.
	* **`copyborder`**: A CSS 'border' rule. Can be, for example "1px solid gray".
	* **`copiedborder`**: A CSS 'border' rule. Can be, for example "1px solid green".
	* **`scale`**: The scale of the buttons.
	* **`offset`**: The offset (in em) from the top and the right.
	* **`radius`**: The border-radius  (in em) of the buttons.
* **`tooltip`**: Show a tooltip at the Copied state, for the icons-only display version.
* **`iconsvg`**: This option is an object with placeholders for SVG icons for the 'copy' and 'copied' state. If left empty, it will use the default icons.
	* **`copy`**: An SVG string (`<svg>...</svg>`) can be pasted here.
	* **`copied`**: An SVG string (`<svg>...</svg>`) can be pasted here.
* **`csspath`**: CopyCode will automatically load the styling. If you want to customise the styling, you can link to your own CSS file here. 

The global options make CopyCode very customizable. To make the buttons look more like the standard GitHub copy-buttons, you can tweak the above configuration like this:

``` json
copycode: { timeout: 1200, button: "hover", display: "icons", style: { copybg: "rgba(255,255,255,128)", copiedbg: "white", copyborder: "2px solid gray", copiedborder: "2px solid green", copiedcolor: "green", offset: 0.5, radius: 0.2} }
```



## Manual styling

Just change the provided stylesheet and do not override it from the config.


## Like it?

If you like it, please star this repo.


## License
MIT licensed

Copyright (C) 2023 Martijn De Jongh (Martino)
