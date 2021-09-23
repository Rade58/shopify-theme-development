# SCHEMA

YOU CAN EDIT FILE `config/settings_schema.json`

LIKE YOU SEE THIS FILE IS INSIDE CONFIGURATION FOLDER

**this is used for adding some settings (`SOME PART OF UI OF EDITOR`) into your editor; and what you add it is going to be seen in your editor like something that you can apply by editing inside editor**

## HOW IT WORKS, I'LL SHOW YOU FROM EXAMPLE

LETS ADD NEW COLOR BY ADDING NEW INPUT INTO ARRRAY OF "settings" FOR THE OBJECT NAMED AS `"t:settings_schema.colors.name"`

```
code config/settings_schema.json
```

```json
[
  {
    "name": "theme_info",
    "theme_name": "Dawn",
    "theme_version": "2.1.0",
    "theme_author": "Shopify",
    "theme_documentation_url": "https:\/\/help.shopify.com\/manual\/online-store\/themes\/os20\/themes-by-shopify\/dawn",
    "theme_support_url": "https:\/\/support.shopify.com\/"
  },

  {
  "name": "t:settings_schema.colors.name",
    "settings": [
      // OK THIS WAS HERE PREDEFINED FOR THE header (SO header USES COLOR CALLED "header")
      {
      "type": "header",
      "content": "t:settings_schema.colors.settings.header__1.content"
      },
      // ALSO YOU HAD THIS ALREDY DEFINED (ANY MANY MORE OTHER OBJECTS)
      {
        "type": "color",
        "id": "colors_solid_button_labels",
        "default": "#FFFFFF",
        "label": "t:settings_schema.colors.settings.colors_solid_button_labels.label",
        "info": "t:settings_schema.colors.settings.colors_solid_button_labels.info"
      },
      // HERE ARE MANY MORE OPTIONS
    ]
  }
  // I ADDED THIS, LIKE YOU SEE I ADDED NEW COLOR OPTIONS
  {
    "name": "lovely colors",
    "settings": [
      {
        "type": "color",
        "id": "beutiful-color-1",
        "default": "#183a52",
        "label": "some beutiful color 1",
        "info": "This is so nice"
      },
      {
        "type": "color",
        "id": "beutiful-color-2",
        "default": "#8a2650",
        "label": "some beutiful color 2",
        "info": "This is so nice times two"
      }
    ]
  },

]
```

**LETS NOW RUN OUR THEME**

```
shopify theme serve
```

**LETS OPEN EDITOR**

**IN EDITOR, CLICK ON `Theme settings` (LOWER LEFT CORNER)**

ON THE RIGHT YOU CAN FIND THE THING YOU ADD

THERE ARE TWO COLORS YOU CAN CHOOSE WHEN DEVELOPING THEME

**BUT ALSO YOU CAN CHANGE THAT COLOR ON THE SPOT USING COLOR PICKER INTRFACE**

**THAT INTERFACE IS MAJOR THING; THE COLORS I PROVIDED THROUGH SETTINGS WHILE DEFINING THIS OPTION IT WAS ONLY DEFAULT COLOR FOR THAT INTERFACE**