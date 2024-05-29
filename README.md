# ProcessWire Auto Links Textformatter Module

Licensed under MPL 2.0.

## What it does

This Textformatter module automatically links your specified phrases/words
to your specified URLs. This is an potential SEO and accessibility tool for
creating automatic contextual links with little effort. If there are pages
that you commonly link to in your site from your textarea/rich text fields,
then this Textformatter can save you some effort, automatically linking
to those URLs. 

Because this module is a Textformatter module, the work it does happens at
runtime. That means that this module can easily be applied to existing sites.


## Usage example

We'll use processwire.com as an example. Throughout processwire.com, we 
routinely use the terms "API", "selector", "template", "template file", 
"$page", "$pages" and more. In the past, I've spent significant time in 
the page editor manually linking these terms to the appropriate pages, as it is 
a helpful cross-reference for users. For example, when the term "API" 
appears, I want to automatically link to the API reference pages at
<https://processwire.com/api/ref/>.

With the Auto Links Textformatter module, I can now automatically link to
all my important terms from all existing and future body copy. If one of
those links happens to change in the future, no problem, as I only have
to update it in one place. This benefits users of processwire.com, 
myself (in time savings) and facilitates crawlers that analyze contextual links.
We hope that you find Auto Links to be a benefit to your site(s) and 
time saver for you and/or your site editors. 

## Requirements

- ProcessWire 3.0.200 or newer. 
- PHP’s must be compiled with mb_string (as it usually is by default). 

## How to install and use

1. Copy all the files for this module to /site/modules/TextformatterAutoLinks/ 

2. In your admin, go to Modules > Refresh. 

3. Click the "Install" button next to TextformatterAutolinks

4. Set up is performed from the module configuration screen
   (Modules > Configure > TextformatterAutoLinks). This is where you will
   add your automatic links. Follow the on-screen instructions to complete 
   this step. Or if you prefer, you can come back and do this later. 

5. Determine which Textarea fields where you want Auto Links to be inserted. 
   Locate those fields in Setup > Fields and edit them. The most likely 
   scenario is that you would apply it to just your "body" field. When
   editing your field, go to the "Details" tab and select "Auto Links 
   Textformatter" from the "Textformatters" select box. If you have other 
   Textformatters selected, you may wish to make Auto Links the last one 
   in the list by dragging and dropping as needed. Save. 

6. Test out your Auto Links by viewing a page that contains the terms.

## Configuration

Following is a description of the settings available on the module 
configuration screen: 

### Terms to link

Enter one per line of: "term=URL", where "term" is the text/phrase you want 
to automatically link, and "URL" is the URL/path you want it to link to. 

If your ProcessWire installation runs from a subdirectory, do not include that 
in the path as it will be prepended automatically. 

You may also specify a page ID (number) for the URL to determine it automatically 
at runtime. 

To automatically expand your term to include other words that start with the 
same characters, append an asterisk `*` to the end of your term, i.e. `wine-*`
would match "wine-growing", "wine-region", etc. 

**Example 1:**   
`Hello World=/hello/world/`  
This would link the term "Hello World" to /hello/world/.

**Example 2:**   
`World*=/hello/world/`  
This would link all words starting with "World" (i.e. "World", "Worldwide", etc.) 
to /hello/world/.

Term text is not case sensitive. If preferred, terms may also be specified 
manually via `$config->TextformatterAutolinks = [ "term" => "URL" ];` in your 
/site/config.php file.

### Phrases to exclude

Sometimes a term appears in a phrase where you do not want it linked. Enter any 
phrases (containing terms above) where the link should be prevented.

For example, if you wanted the term “contact” linked, but not when it appears 
in “contact sports”, you would enter “contact sports” here.

### Maximum links per term

Use this option to prevent the same term from being linked too many times in 
the same block of text. Specify a value of 1 or higher. The default is 5.

### Maximum terms to link

Use this option to prevent too many terms from being linked in the same text.
Leave blank (or 0) for no maximum. The default is 20.

### Minimum link distance

Use this option to prevent the same term from being linked more than once when 
it appears in close range. Specify value in number of characters, the default
is 100. 

### Allowed tags whitelist

Enter a list of HTML tags (without brackets) that AutoLinks is allowed to 
generate links within, each separated by a space. When specified, links will 
only be generated if the terms appear somewhere within one of the given HTML 
tags. If left blank, terms will be linked within any HTML tags. For example:
`p li h3`. 

### Link markup for internal links

This is the markup used for links that do not begin with a 
scheme/protocol, such as `/about/contact/`. It should contain the variable
placeholders `{href}` and `{text}`, i.e. `<a href="{href}">{text}</a>`. 

### Link markup for external links

This is the markup used for links that DO begin with a scheme/protocol, 
such as `https://processwire.com/api/ref/`. It should contain the variable
placeholders `{href}` and `{text}`, i.e. 
`<a target="_blank" rel="nofollow" href="{href}">{text}</a>`.

---
Copyright 2014-2024 by Ryan Cramer Design, LLC