# SHOPIFY CLI

IT IS GOOD FOR US TO DO SOME THINGS FIRST

# FIRST WE WANT TO DUPLICATE OUR THEME, BECAUSE WE DON'T WANT TO EDIT CURRENT PUBLISHED THEME

IN DASBORD CLICK ON ACTIONS AND DUPLICATE THEME, WHEN THAT IS DONE, YOU CAN RENAME A COPY, BY GIVING IT SOME NAME YOU THINK OF TO "MARK IT" AS A DEVELOPMENT THEME

I RENAMED BOTH THEMES

THE CURRENTLY DEPLOYD I GAVE A NAME: `<something>`, AND I NAMED A COPY AS `<something>-dev`

**WE CAN SAY THAT WE ARE GOING TO USE COPY FOR DEVELOPING AND FOR STAGING**

## WE CAN PREVIEW THE THEME WE COPIED

IT WILL BE THE SAM URL AS PUBLISHED THEME (URL OF PUBLISHED STORE)

BUT YOU WILL HAVE SOME EXTRA STUFF AS A UERY STRING IN ADRESS BAR, ALSO YOU WILL HAVE A BOTTOM BAR TELLING YOU WHAT THEME WE ARE PREVIEEWING

YOU CAN SHARE THIS PREVIEW LIKE YOU SEE, YOU HAVE A BUTTON TO COPY A LINK

AGAIN, WE HAVE GENERATED PASSWORD AND ANYONE HO WOULD LIIKE TO SEE IT NEEDS TO ENTER THE PASSWORD (ALREADY I EXPLAIN YOU THAT)

# LETS INSTALL SHOPIFY CLI NOW

INSTALL IT WITH apt LIKE IS SHOWN HERE (MAKE SURE TO DOWNLOAD FILE AND THEN INSTALL IT WITH apt)

<https://shopify.dev/themes/tools/cli/installation>

DON'T FORGET TO VERIFY

```
shopify version
```

HERE YOU HAVE COMMAND REFERENCES:

<https://shopify.dev/themes/tools/cli/core-commands>

# LOGING IN TO CLI

MAKE SURE YOU ARE LOGGED IN AS A STORE OWNER IN YOUR SHOPIFY DEVELOPMENT STORE

WE ARE SINCE WE DIDN'T USE ANY OTHER ACCOUNT TO LOG IN IN OUR STORE AND WE DIDN'T GIVE PERMISSIONS TO ANYONE

TO CHECK PERMISSION AND THAT YOU ARE ACTUALLY SIGNED IN AS AN OWNER IN STORE DASBOARD CLICK ON `Online Store`(left menu) --> Settings --> `Users And Permissions`; AND FROM HER YOU CAN SEE ESTORE OWNER AND I AM LOGGED IN AS ONE (STORE OWNER NAME (EMAIL IN MAY CASE) SHOULD MACH ONE IN RIGHT TOP CORNER (PROFILE CIRCLE))

WE NEED TO PROVIDE STORE URL (OUR DOMAIN `<something>.myshopify.com`)

```
shopify login --store <something>.myshopify.com 
```

BROWSERS WINDOW WILL POP UP AND YOU WILL SIGN IN AND THAT IS IT

YOU USE `shopify logout` TO LOG OUT FROM YOUR CURRENT STORE