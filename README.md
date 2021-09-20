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

## I ENCURAGE YOU TO CHECK DOCUMENTATION FOR CLI

<https://shopify.dev/themes/tools/cli/core-commands>

FOR EXAMPLE YOU CAN POPULATE STORE WITH DAT AND DO ALL KIND OF THINGS, THAT ARE VERY HELPFUL

## WE WOUL USE `shopify init` TO CLONE REPO (WE WOULD USE THIS IF WE ARE STARTING FROM SCRATCH), BUT WE WILL CONNECT TO AN EXISTING THEME

WE RE GOING TO EXECUTE `shopify theme serve`

FIRST GO INTO SHOPIFY STORE DASBORD AND FIND ID OF YOUR THEME (DO THIS FOR THEME YOU COPIED)

CLICKK ON `Theme` (LEFT MENU) --> YOU SHOUD SEE YOUR PUBLISHED THEME AND A LITTLE BIT LOWER YOU HAVE COPY THEME WE MADE, CLICK ON `Customie` FOR MENTIONED THEME

**THING WE NEED IS NUMBER INSIDE URL, LIKE THI `/45246246512/`**

WE ARE PULLING (RETREIVING THEME FROM SHOPIFY) (MAKE SURE TO NAVIGATE IN YOUR FILE SYSTEM WHERE YOU WANT (BUT IF YOU ARE NOT IN THAT FOLDER, YOU CAN SPECIFY IT IN COMMAND))

***
***

WHEN I WAS DOING THIS THERE WAS A PROBLEM, AND PROBLEM WAS THAT YOU COULDN'T PULL A THHEME IF YOU WERE NOT STAFF AT YOUR STORE

[THIS IS A WORKAROUND](https://github.com/Shopify/shopify-cli/issues/1361#issuecomment-879426041)

>> This happens because when you create a Development store, it won't properly link your Shopify Partners account to the new created store.

>> A partial solution was mentioned here #1309 (comment)

>> This is what I do to solve the problem on my side:

>> 1.- Logout from the Development store admin dashboard
>> 2.- Login again by visiting the direct URL. Example: `https://[store-name].myshopify.com/admin`

>> Here use your Shopify Partners account (the one that you used to create the development store). Don't worry if you see an error message or if you have to login again. Ideally you should see the admin dashboard again.

>> 4.- Login to your Shopify account (not Partners). Go to: https://shopify.com/login

>> At this point you should see the new Development store listed. This means it is now linked to your account.

>> Go back to the CLI and try again. You may have to do shopify whoami and/or shopify logout shopify login

***
***

NOW WE CAN PULL

```
shopify theme pull --themeid=<number I mentioned> <path where you wwant to put your theme on your filesystem>
```
