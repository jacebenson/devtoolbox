+++
# A Demo section created with the Blank widget.
# Any elements can be added in the body: https://sourcethemes.com/academic/docs/writing-markdown-latex/
# Add more sections by duplicating this file and customizing to your requirements.

widget = "blank"  # See https://sourcethemes.com/academic/docs/page-builder/
headless = true  # This file represents a page section.
active = true  # Activate this widget? true/false
weight = 20 # Order that this section will appear.

title = "What is this?"
subtitle = ""

[design]
  # Choose how many columns the section has. Valid values: 1 or 2.
  columns = "1"

[design.background]
  # Apply a background color, gradient, or image.
  #   Uncomment (by removing `#`) an option to apply it.
  #   Choose a light or dark text color by setting `text_color_light`.
  #   Any HTML color name or Hex value is valid.

  # Background color.
  # color = "navy"
  
  # Background gradient.
  gradient_start = "DarkGreen"
  gradient_end = "ForestGreen"
  
  # Background image.
  # image = "image.jpg"  # Name of image in `static/img/`.
  # image_darken = 0.6  # Darken the image? Range 0-1 where 0 is transparent and 1 is opaque.

  # Text color (true=light or false=dark).
  text_color_light = true

[design.spacing]
  # Customize the section spacing. Order is top, right, bottom, left.
  padding = ["20px", "0", "20px", "0"]

[advanced]
 # Custom CSS. 
 css_style = ""
 
 # CSS class.
 css_class = ""
+++

This is a [scoped app](https://docs.servicenow.com/bundle/newyork-application-development/page/build/applications/concept/c_ApplicationScope.html) in ServiceNow to give administrators and Developers a some utililities that I found useful based on [Jim Coyne's Developer Toolbox](https://community.servicenow.com/community?id=community_blog&sys_id=b3c843aadb892b40fece0b55ca961906).

# Why?

- Easy install, Easy uninstall
- Why not?

# What are the features?

## Open Source Activity Formatter

If you want a better level of programmable control of the activity formatter in UI16.

![Open Source Activity Formatter](/img/osaf.jpg)

## Variable Parser

This is to give admins/developers a way to not depend on [GlideappVariablePoolQuestionSet](https://community.servicenow.com/community?id=community_question&sys_id=7df197eddbdcdbc01dcaf3231f961900).

It's really just a script include to do what I did [way, way back when](https://jace.pro/post/2018-02-15-print-out-variables/).

This is contained within the `variableHelper` Script include and here's a sample of what it does;

```js
// Run this
var vh = new x_8821_dev_toolbox.variableHelper();

var current = new GlideRecord('change_request');
current.get('c286d61347c12200e0ef563dbb9a71df');
var vars = vh.getVariables(current);
var printable = JSON.stringify(vars, '', ' ');
gs.info(printable);

var current = new GlideRecord('sc_req_item');
//current.get('257c82740f4b1300fc69cdbce1050ea2');
current.setLimit(1);
current.orderByDesc('sys_created_on');
current.query();
if (current.next()) {
    var vars = vh.getVariables(current);
    var printable = JSON.stringify(vars, '', ' ');
    gs.info(printable);
}
```

```sh
x_8821_dev_toolbox: [
 {
  "label": "Server to reboot",
  "value": "AS400",
  "order": "100"
 },
 {
  "label": "Desired date and time of reboot",
  "value": "2016-08-10 21:42:16",
  "order": "200"
 },
 {
  "label": "Reason for reboot",
  "value": "broken",
  "order": "400"
 }
]
x_8821_dev_toolbox: [
 {
  "label": "Item name",
  "value": "Make a new Tweet!  Yea this is silly",
  "order": "1"
 },
 {
  "label": "What group owns this item?",
  "value": "US Presidents Group 1",
  "order": "3"
 },
 {
  "label": "Search terms",
  "value": "twitter, tweet, tweeting, social",
  "order": "4"
 },
 {
  "label": "What process does this follow?",
  "value": "One approval and one task",
  "order": "12"
 },
 {
  "label": "Task 1 Group",
  "value": "Service Desk",
  "order": "14"
 },
 {
  "label": "Task 1 Short Description",
  "value": "Service Desk gets all the ... hard work",
  "order": "15"
 },
 {
  "label": "Task 1 Description",
  "value": "Tweet this message out at this time :(",
  "order": "16"
 },
 {
  "label": "Approval 1 Group",
  "value": "Change Management",
  "order": "22"
 },
 {
  "208934368172635": [
   {
    "label": "Question",
    "value": "What would you like to tweet?",
    "order": "5"
   },
   {
    "label": "Type",
    "value": "6",
    "order": "6"
   },
   {
    "label": "Default Value",
    "value": "",
    "order": "7"
   },
   {
    "label": "Table",
    "value": "",
    "order": "8"
   },
   {
    "label": "Reference Qualifer",
    "value": "",
    "order": "9"
   },
   {
    "label": "Choices",
    "value": "",
    "order": "10"
   }
  ],
  "208934372249576": [
   {
    "label": "Question",
    "value": "When would you like it tweeted?",
    "order": "5"
   },
   {
    "label": "Type",
    "value": "10",
    "order": "6"
   },
   {
    "label": "Default Value",
    "value": "",
    "order": "7"
   },
   {
    "label": "Table",
    "value": "",
    "order": "8"
   },
   {
    "label": "Reference Qualifer",
    "value": "",
    "order": "9"
   },
   {
    "label": "Choices",
    "value": "",
    "order": "10"
   }
  ],
  "208934375008859": [
   {
    "label": "Question",
    "value": "How much did you enjoy this item?",
    "order": "5"
   },
   {
    "label": "Type",
    "value": "5",
    "order": "6"
   },
   {
    "label": "Default Value",
    "value": "",
    "order": "7"
   },
   {
    "label": "Table",
    "value": "",
    "order": "8"
   },
   {
    "label": "Reference Qualifer",
    "value": "",
    "order": "9"
   },
   {
    "label": "Choices",
    "value": "Meh, It is okay, It is great, I am writing about it in my family tree, It is terrible, It is mediocre",
    "order": "10"
   }
  ]
 }
]
```

## Item maker

<video width="320" height="240" controls="">
  <source src="img/item-item.mp4" type="video/mp4">
</video>

## Utility UI Actions and Context Menus;

### Context Menus

| Context Item                           | Table    | Availability                       | Type        |
| -------------------------------------- | -------- | ---------------------------------- | ----------- |
| Add Data to Table                      | `global` | User is Admin, Property is checked | List Header |
| Create a Module from this Query        | `global` | User is Admin, Property is checked | List Header |
| GlideRecord Script - Background Script | `global` | User is Admin, Property is checked | List Header |
| GlideRecord Script - Preview           | `global` | User is Admin, Property is checked | List Header |
| Grab Grouped Information               | `global` | User is Admin, Property is checked | List Header |
| Show JSON                              | `global` | User is Admin, Property is checked | List Row    |
| Show Schema Map                        | `global` | User is Admin, Property is checked | List Header |
| Show Schema Map (Old)                  | `global` | User is Admin, Property is checked | List Header |

### UI Actions

| UI Action                       | Table             | Availability                       | Type      |
| ------------------------------- | ----------------- | ---------------------------------- | --------- |
| Add Multiple 'Question Choices' | `item_option_new` | User is Admin, type == "5"         | Form Link |
| Set Name from Question          | `item_option_new` | User is able to write              | Form Link |
| GlideRecord Script - Background | `task`            | User is Admin, Property is checked | Form Link |
| GlideRecord Script - Preview    | `task`            | User is Admin, Property is checked | Form Link |
| GlideRecord Script - Xplore     | `task`            | User is Admin, Property is checked | Form Link |
| Replace Text*                   | `task`            | User is Admin, Property is checked | Form Link |
| Show Contents of g_scratchpad   | `task`            | User is Admin, Property is checked | Form Link |
| Show JSON                       | `task`            | User is Admin, Property is checked | Form Link |
| Show Schema Map                 | `task`            | User is Admin, Property is checked | Form Link |
| Show Schema Map (Old)           | `task`            | User is Admin, Property is checked | Form Link |
| Switch to List View             | `task`            | User is Admin, Property is checked | Form Link |

* "Replace Text" requires a change on\
  `/sys_db_object_list.do?sysparm_query=nameINsys_journal_field%2Csys_audit%2Csys_history_set`\
  To allow for create, update, read and deletes.
