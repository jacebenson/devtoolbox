---
# The Hugo Grayscale theme is a one page theme designed to be the front page to your site.  Its content is populated via the front-matter in content/_index.md.  The page consists of, in order:
# * a navbar at top linking to the other sections, and other arbitrary links
# * an intro section presenting a header title and into text with background image
# * an about section presenting a header and text with black background
# * a download section presenting header and text with background image
# * a contact section presenting header and text with black background
# 
# The section names show up as the links in the navbar, so you may wish to rename them if, for example, you're not using it for the purpose suggested by the default section name.
# 
# The background images are selected by filename - the intro section image must be named "intro-bg.jpg" and placed in the "static/img/" directory for your site.  Similarly, the downloads section image must be named "downloads-bg.jpg" and placed in the "static/img/" directory for your site.  See the default images in the theme's static directory for file size reference.

title: "Dev Toolbox"
date: 2018-09-09T00:00:00-00:00
copyright: "Jace Benson"
#mapsapikey: xxx

socialhandles:
    twitter: "jacebenson"
    github: "jacebenson/devtoolbox"
    discord: "https://discordapp.com/invite/QaMwnGd"

#menu:
#    -
#        url: "https://discord.gg/QaMwnGd"
#        name: "Discord"

intro:
    header: "Dev Toolbox"
    text: "A grouping of useful utilities in Servicenow"

about:
    header: "About Scoped Dev Toolbox"
    text: '<p>Dev Toolbox is a scoped app to capture tests for all the Out of Box servicenow applications. With this you have a place to start your own tests instead of starting from scratch. Once installed you’ll be able to run a batch of tests against the instance. One key detail about all of these tests, they are all self-contained. Meaning, you don’t need to load up any demo users, companies or groups to try these tests. They are all included in this scoped application.</p>
    <div style="text-align:left;padding:10px">
    <h2>Features</h1>
    <ul>
    <li>Rewrite Journal content</li>
    <li>Variable Helper</li>
    <li>Add Data to Table</li>
    <li>Create Module from this Query</li>
    <li>GlideRecord Script - Background Script</li>
    <li>GlideRecord Script - Preview</li>
    <li>"Email Scripts" Related List</li>
    <li>"Set Name from Question" Tool</li>
    <li>"Set Value from Label" Tool</li>
    <li>"Set Value from Text" Tool</li>
    <li>"Show Contents of g_scratchpad" Tool</li>
    <li>"Show Schema Map" Tools</li>
    </ul>
    <h2>Rewrite Journal Content</h2>
    <p>This adds a UI Action for admins to replace text on `task` for users with
    the `admin` role.  This is what the feature looks like in action;</p>
    <img src="screenshot.gif"/>
    <h2>Variable Helper</h2>
    <p>This script include makes it easier to get the variables on
    catalog items, their tasks, and other records;</p>
    <code>
    //example mail script<br/>
    (function runMailScript(current, template, email, email_action, event) {<br/>
    &nbsp;&nbsp;template.print("<span style=\"font-size: 10pt; font-family: arial, geneva;\">");<br/>
    &nbsp;&nbsp;template.print("Additional details:&lt;br />"); <br/>
    &nbsp;&nbsp;printVars();<br/>
    &nbsp;&nbsp;function printVars(){<br/>
    &nbsp;&nbsp;&nbsp;&nbsp;var vh = new x_8821_glide_utils.variableHelper();<br/>
    &nbsp;&nbsp;&nbsp;&nbsp;var vars = vh.getVariables(current);<br/>
    &nbsp;&nbsp;&nbsp;&nbsp;for (var i = 0; i < vars.length; i++) {<br/>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;template.space(6);<br/>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;template.print(" " + "&lt;b>" + vars[i].label + ": " + "&lt;/b>");<br/>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;template.print(vars[i].value + "\n" + "&lt;br/>");<br/>
    &nbsp;&nbsp;&nbsp;&nbsp;}<br/>
    &nbsp;&nbsp;}<br/>
    })(current, template, email, email_action, event);
    </code>
    </div>
    '

download:
    rename: "Install"
    header: "Install Scoped \"Dev toolbox\""
    text: '<p>You can install it using this url: <a href="https://github.com/jacebenson/devtoolbox.git">https://github.com/jacebenson/devtoolbox.git</a>
    </p>'

contact:
    header: "Contact Us"
    text: '<p>Feel free to leave us a comment (via issues) on <a href="https://github.com/jacebenson/devtoolbox/issues/new">github</a> to give some feedback about this theme!</p>'
---
