# Casper Dark (DS)

> Based on the default theme ([Casper][casper]) for [Ghost][ghost].
> 
> Merged with [upstream][upstream-repo] v2.11.1 on 2019/08/29

*Disclosure: I'm new to all of this CSS, HTML, etc. shenanigans; aside from a private BookStack instance, this is my first venture into any kind of theming.*

That being said, ***I put Casper in the dark*** and added a few tricks/features; primarily focused on presenting technical documentation. I've attached a couple screenshots, or you can check the theme out on [my site](https://shnosh.io). While this is a bit of an experimental work in progress, I thought it was sufficiently *done enough* for sharing; I expect there will be changes as I learn, tweak, and (hopefully) optimize over time.

**[Changelog](changelog.md)**

# Installation

1. Download the files using the [GitHub .zip download][zip-dl] option.
2. Navigate to **Settings > Design** on your Ghost admin interface.
3. Click **Upload a theme** (near bottom).
4. Either drag the .zip file onto the dialogue, or click the center to browse to the .zip.
5. Click **Activate Now**.

# Features

## PrismJS & Custom "One Dark" Theme

PrismJS is packaged with my custom [One Dark][prismjs-onedark] theme and the following languages and plugins;

<details><summary>Expand for Languages</summary>

- markup
- css
- clike
- javascript
- apacheconf
- bash
- batch
- css-extras
- markup-templating
- git
- handlebars
- http
- ini
- php
- json
- markdown
- django
- nginx
- sql
- powershell
- scss
- python
- rest
- sass
- yaml
- tcl
- visual-basic
- regex
</details>

<details><summary>Expand for Plugins</summary>

- line-highlight
- line-numbers
- toolbar
- highlight-keywords
- unescaped-markup
- command-line
- show-language
- copy-to-clipboard

</details>

**Screenshot**

![screenshot-prismjs-onedark][ss-prismjs-onedark]

### Hack for `command-line` plugin

The PrismJS `command-line` plugin includes a hack that allows multiple prompts to be defined per code-block ([source][prismjs-cmdline-hack]).

```html
<pre class="command-line language-bash" data-prompt="1,4|NXOSv#;2-3|NXOSv(config)#">
<code>conf
feature nxapi
end
copy ru st</code></pre>
```

### Result

![screenshot-prismjs-cmdline][ss-prismjs-cmdline]

---

## Styled `<details>` (Accordions)

Styling for HTML5 `<details>` elements, used as accordions.

### Usage

```html
<details><summary>Expand for <desc>Dynamic Variable Example</desc></summary>
 
`gi_ints` is a list of GigabitEthernet interfaces, which scales with the number of switches in the stack.

| Switch Count | `gi_ints` |
| :-: | :- |
|  1  | `gi1/0/1-36` |
|  2  | `gi1/0/1-36,gi2/0/1-36` |
|  3  | `gi1/0/1-36,gi2/0/1-36,gi3/0/1-36` |
|  4  | `gi1/0/1-36,gi2/0/1-36,gi3/0/1-36,gi4/0/1-36` |

</details>
```

### Result

**Closed (default)**

![screenshot-details-closed][ss-details-closed]

**Open**

![screenshot-details-open][ss-details-open]

---

## Custom Callouts

5 custom callout styles (inspired by [BookStack callouts][bookstack-callouts]).

- Generic (white)
- Info (blue)
- Success (green)
- Warning (orange)
- Danger (red)

### Callouts with `<p>`

```html
<p class="callout">This is a plain callout.</p>
<p class="callout info">This is an informational callout.</p>
<p class="callout success">This is a success callout</p>
<p class="callout warning">This is a warning callout</p>
<p class="callout danger">This is a danger callout</p>
```

### Callout with `<div>`

*Can be used to include line-breaks and markdown in the callout; markdown requires a blank space after the `<div>` (ignore `\` in the code block).*

```html
<div class="callout info">

This is an informational callout with some `inline-code`

> **And a blockquote.**
> 
> With *markdown* formatting; e.g. ~~strikethrough~~

\```bash
# And a code block.
sudo nano /etc/hostname
\```

And a list
- Item 1
- Item 2
  - Sub-item
</div>
```

### Results

![screenshot-callouts][ss-callouts]

---

## Steps Tables

Custom format for single column Markdown tables used to outline process steps.

### Usage

*Wrap the table in a `<div>` tag; markdown requires a blank space after the `<div>`.*

```html
<div class="steps-table">

| How to hold up three fingers.   <!-- Header  -->
| -                               <!-- Separator line -->
| Hold up **one** finger.         <!-- Step -->
| ![step1][1-finger]              <!-- Image -->
| Hold up **two** fingers.        <!-- Step -->
| ![step2][2-fingers]             <!-- Image -->
| Hold up **three** fingers.      <!-- Step -->
| ![step3][3-fingers]             <!-- Image -->
</div>

<!-- Use reference style links to keep table rows concise. -->
[1-finger]: https://i.imgur.com/tjeG9rD.png
[2-fingers]: https://i.imgur.com/rCbyQrV.png
[3-fingers]: https://i.imgur.com/1kbc5eN.png
```

### Result

![steps-table][ss-steps-table]

# Screenshots

## Home

![screenshot-desktop-home][ss-d-home]

## Post

![screenshot-desktop-post-2-top][ss-d-post]



[upstream-repo]: https://github.com/TryGhost/Casper
[ghost]: http://github.com/tryghost/ghost/
[casper]: https://github.com/TryGhost/Casper
[zip-dl]: https://github.com/derek-shnosh/casper-dark-ds/archive/master.zip
[prismjs-onedark]: https://github.com/derek-shnosh/prism-theme-one-dark-ds
[clipboardjs]: https://github.com/zenorocha/clipboard.js/
[prismjs]: https://github.com/PrismJS/prism
[bookstack-callouts]: https://www.bookstackapp.com/blog/beta-release-v0-11-0/
[prismjs-cmdline-hack]: https://github.com/PrismJS/prism/issues/1021#issuecomment-477791027
[steps-table-eg]: https://shnosh.io/securecrt-echo-paste/#securecrtconfiguration
[ss-steps-table]: assets/images/screenshot-steps-table.png
[ss-callouts]: assets/images/screenshot-callouts.png
[ss-details-closed]: assets/images/screenshot-details-closed.png
[ss-details-open]: assets/images/screenshot-details-open.png
[ss-d-home]: assets/images/screenshot-desktop-home.png
[ss-d-post]: assets/images/screenshot-desktop-post.png
[ss-prismjs-onedark]: assets/images/screenshot-prismjs-one-dark.png
[ss-prismjs-cmdline]: assets/images/screenshot-prismjs-cmd-line.png