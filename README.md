## Welcome to GitHub Pages

!(https://github.com/pmlove3/ir-theory/blob/eca490c05ec25165e1cfdf3e5dbb9d61c34d0747/2020-07-12-23-54-59.html)

You can use the [editor on GitHub](https://github.com/pmlove3/ir-theory/edit/master/README.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/pmlove3/ir-theory/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.


<p><a class="weatherwidget-io" href="https://forecast7.com/en/35d23n80d84/charlotte/?unit=us" data-label_1="CHARLOTTE" data-label_2="WEATHER" >CHARLOTTE WEATHER</a>
<script>
!function(d,s,id){var js,fjs=d.getElementsByTagName(s)[0];if(!d.getElementById(id)){js=d.createElement(s);js.id=id;js.src=&#8216;https://weatherwidget.io/js/widget.min.js&#8217;;fjs.parentNode.insertBefore(js,fjs);}}(document,&#8216;script&#8217;,&#8216;weatherwidget-io-js&#8217;);
</script></p>



When it comes to embedding widgets in my markdown, I could just embed the HTML
right in the content. Embedding HTML is a totally valid approach:
 
<iframe
	src="//player.vimeo.com/video/96794772?color=ff3366"
	width="700"
	height="394"
	frameborder="0"
	webkitallowfullscreen
	mozallowfullscreen
	allowfullscreen
></iframe>
 
The problem with this is that tightly couples the "intent" of the widget to the
"implementation" of the widget. Plus, it's quite verbose. Instead, what I'd like
to do is provide a _description_ of the widget; and then hide the implementation
behind some sort of post-processing.
 
The first approach that I thought of was to use an HTML Comment to embed simple
markers that could be replaced with a RegEx pattern:
 
<!-- vimeo: 96794772 -->
 
The above approach is nice when there is a single token to work with (such as
the video ID) because the pattern is really easy to match. But, if the data is
more complex and has several attributes, it might be nice to work with a complex
data structure. For this, I could use a Script tag to embed JSON (JavaScript
Object Notation) directly in the content:
 
<script type="markdown/widget">
	{
		"type": "vimeo",
		"vimeo": {
			"id": "96794772",
			"color": "ffffff"
		}
	}
</script>
 
In this case, we're still using a RegEx pattern to match the payload between the
open `<script>` and the close `</script>`. But, the contents ultimately get
parsed using the `deserializeJson()` function.
 
But, then I wondered, could I just do the same thing with an HTML Comment and a
bit less ceremony:
 
<!-- json:
	{
		"type": "vimeo",
		"vimeo": {
			"id": "96794772",
			"color": "ff00ff"
		}
	}
-->
 
This approach works quite well and has less syntax. But, isn't quite as
attractive, visually speaking. That said, any of these approach is sufficient
and fills me with hope that migrating to Markdown will be easier than I thought



<script>var pfHeaderImgUrl = '';var pfHeaderTagline = '';var pfdisableClickToDel = 0;var pfHideImages = 0;var pfImageDisplayStyle = 'right';var pfDisablePDF = 0;var pfDisableEmail = 0;var pfDisablePrint = 0;var pfCustomCSS = '';var pfBtVersion='2';(function(){var js,pf;pf=document.createElement('script');pf.type='text/javascript';pf.src='//cdn.printfriendly.com/printfriendly.js';document.getElementsByTagName('head')[0].appendChild(pf)})();</script><a href="https://www.printfriendly.com" style="color:#6D9F00;text-decoration:none;" class="printfriendly" onclick="window.print();return false;" title="Printer Friendly and PDF"><img style="border:none;-webkit-box-shadow:none;box-shadow:none;" src="//cdn.printfriendly.com/buttons/printfriendly-pdf-button-nobg-md.png" alt="Print Friendly and PDF"/></a>


