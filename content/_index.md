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
    text: '<p>Dev Toolbox is a scoped app to capture tests for all the Out of Box servicenow applications. This is a scoped application for Service-now to allow some utilities to be easily added and maintained on instances.
    </p>
    <div style="text-align:left;padding:10px">
    <h2>Features</h1>
    <ul>
    <li>Standard Catalog Item generation</li>
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

    
    
    <h2 id="sc_item"> Standard Catalog Item generation </h2>
    <p>What does this even mean</p>
    <p>Well, here is the thing.  I do not know about you, but I find nearly 80% of all
    my catalog work is a simple, make an item that has 0-2 approvals, and 1-2 tasks
    eitehr in line or in parrellel.</p>
    <p>So how does that help me</p>
    <p>I have created an item that lets the user define the inputs of the item, its workflow,
    and this generates all that as someone in your development environment.  I am still working on the 
    "Put all of it into an update set" and the part where it uses the variables to move/progress the workflow
    properly.  But its happening</p>  

    <video src="item.mp4" controls poster="poster.jpg">
    </video>
    The way this works.

    <ol>
    <li>Two properties.
      <ul>
        <li>`x_8821_dev_toolbox.InstanceBasicAuth` - Expects a JSON obj with username and password</li>
        <li>`x_8821_dev_toolbox.InstanceCreateItem` - Expects a full url with trailing `/`</li>
      </ul>
    </li>
    <li>You request the item, it makes Table API calls to the `sc_cat_item`, `item_option_new`, and `question_choice` tables to create the item.
    </li>
    <li>It also makes a call to the Table API to the `catalog_script_client` to make the "task variables" read only and hidden as they don't need to be on the forms.
    <li>When the item is created it associates to one the workflows listed in the scope.  Those workflows use the variables;
    <ul>
    <li>`approval_1_group`</li>
    <li>`approval_2_group`</li>
    <li>`task_1_group`</li>
    <li>`task_1_short_description`</li>
    <li>`task_1_description`</li>
    <li>`task_2_group`</li>
    <li>`task_2_short_description`</li>
    <li>`task_2_description`</li>
    </ul>
    </li>
    To run the selected workflows.
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
