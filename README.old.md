# Developer Toolbox

This is a scoped application for Service-now to allow some utilities to be easily added and maintained on instances.

---

## Features

- Rewrite Journal content
- Variable Helper
- Add Data to Table
- Create Module from this Query
- GlideRecord Script - Background Script
- GlideRecord Script - Preview
- "Email Scripts" Related List
- "Set Name from Question" Tool
- "Set Value from Label" Tool
- "Set Value from Text" Tool
- "Show Contents of g_scratchpad" Tool
- "Show Schema Map" Tools

### Rewrite Journal Content

This adds a UI Action for admins to replace text on `task` for users with
the `admin` role.  This is what the feature looks like in action;
![](screenshot.gif)

### Variable Helper

This script include makes it easier to get the variables on
catalog items, their tasks, and other records;

```js
//example mail script
(function runMailScript(current, template, email, email_action, event) {
    template.print('<span style="font-size: 10pt; font-family: arial, geneva;">');
    template.print("<B>Additional details</B>:<br />"); 
    printVars();
    function printVars(){
        var vh = new x_8821_glide_utils.variableHelper();
        var vars = vh.getVariables(current);
        for (var i = 0; i < vars.length; i++) {
            template.space(6);
            template.print(' ' + "<b>" + vars[i].label + ": " + "</b>" + vars[i].value + "\n" + "<br/>");
        }
    }
})(current, template, email, email_action, event);
```

---



## Setup

1. Open Studio on your environment
1. Import from source
1. Paste in the following url: `https://gitlab.com/jacebenson/servicenow-glideutils.git`

---

## Usage

After you import this you can start to use it by in the following ways;

- Pull up an task, you with admin role, will see a "Replace Text" UI Action that works.

## Inspiration

Thanks Jim Coyne for starting this.  

[Community Post](https://community.servicenow.com/community?id=community_blog&sys_id=b3c843aadb892b40fece0b55ca961906)