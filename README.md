# SHOPIFY CLI

IT IS GOOD FOR US TO DO SOME THINGS FIRST

# FIRST WE WANT TO DUPLICATE OUR THEME, BECAUSE WE DON'T WANT TO EDIT CURRENT PUBLISHED THEME

***

(AUTHOR OF WORKSHOP DIDN'T DO THIS)

IT DOESNT MATTER ANYWAY SINCE WE ARE GOING TO HAVE OUR ENVIROMENT LOCALY

***

IN DASBORD CLICK ON ACTIONS AND DUPLICATE THEME, WHEN THAT IS DONE, YOU CAN RENAME A COPY, BY GIVING IT SOME NAME YOU THINK OF TO "MARK IT" AS A DEVELOPMENT THEME

I RENAMED BOTH THEMES

THE CURRENTLY DEPLOYD I GAVE A NAME: `<something>`, AND I NAMED A COPY AS `<something>-dev`

**WE CAN SAY THAT WE ARE GOING TO USE COPY FOR DEVELOPING AND FOR STAGING, BUT YOU CAN USE WHAT EVER YOU WANT**

**I'M SAYING THAT BECAUSE LOCAL DEVELOPMENT WON'T BE MAGICALY APPLIED ON YOUR DEPLOYED THEME OR COPY OF THAT THEME, YOU WILL DEELOP LOCALY UNTILL YOU DECIDE TO PUSH OR PUBLISH**

## WE CAN PREVIEW THE THEME WE COPIED (TALKING ABOUT DASBOARD OF COURSE)

IT WILL BE THE SAME URL AS PUBLISHED THEME (URL OF PUBLISHED STORE)

BUT YOU WILL HAVE SOME EXTRA STUFF AS A QERY STRING IN ADRESS BAR, ALSO YOU WILL HAVE A BOTTOM BAR TELLING YOU WHAT THEME WE ARE PREVIEEWING

YOU CAN SHARE THIS PREVIEW LIKE YOU SEE, YOU HAVE A BUTTON TO COPY A LINK

AGAIN, WE HAVE GENERATED PASSWORD AND ANYONE HO WOULD LIKE TO SEE IT NEEDS TO ENTER THE PASSWORD (ALREADY I EXPLAIN YOU WHERE IS THAT PASSWORD LOCATED)

# LETS INSTALL SHOPIFY CLI NOW

***
***

**BUT NOT SO FAST, WE NEED RUBY INSTALLED ON OUR COMPUTER**

**AND BEFORE RUBY INSTALL `build-essential`** (I HAD PROBLEMS INSTALLING SHOPIFY CLI WITHOUT THIS)

```
sudo apt-get install build-essential
```

NOW INTALL RUBY WITH `apt-get`

<https://www.ruby-lang.org/en/documentation/installation/#apt>

```
sudo apt-get install ruby-full
```

```
ruby -v
```

I GUESS IT IS INSTALLED

***
***

ALO INSTALL THIS RUBY PACKAGE (JUST IN CASE AND DON'T ASK ME WHY, BECAUSE I DON'T KNOW)

```
sudo gem install wdm
```

***
***

NOW TO INSTALL SHOPIFY CLI

INSTALL IT WITH apt LIKE IS SHOWN HERE (MAKE SURE TO DOWNLOAD FILE FROM GITHUB (MAKE SURE TO DOWNLOAD .deb PACKAGE) AND THEN INSTALL IT WITH apt) (THEY DID IT LIKE THAT)

<https://shopify.dev/themes/tools/cli/installation>

```
sudo apt install <path to file>
```

DON'T FORGET TO VERIFY

```
shopify version
```

HERE YOU HAVE COMMAND REFERENCES:

<https://shopify.dev/themes/tools/cli/core-commands>

**UPDATING SHOPIFY CLI IS THE SAME; IF A NEW VERSION IS PUBLISHED DOWNLOAD IT FROM MENTIONED PLACE AND INSTALLIT THE SAME WAY**

<https://shopify.dev/apps/tools/cli/troubleshooting>

FROM UPPER LINK YOU CAN FIND OUT HOW TO TROUBLESHOOT OR UNINSTALL CLI ALSO

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

**LOG OF NOW, BECAUSE WE ARE GOING TO ENCOUNTER SOME PROBLEMS WE NEED TO FIX**

## I ENCURAGE YOU TO CHECK DOCUMENTATION FOR CLI

<https://shopify.dev/themes/tools/cli/core-commands>

FOR EXAMPLE YOU CAN POPULATE STORE WITH DATA AND DO ALL KIND OF THINGS, THAT ARE VERY HELPFUL

## WE WOULD USE `shopify init` TO CLONE REPO (WE WOULD USE THIS IF WE ARE STARTING FROM SCRATCH), BUT WE WILL CONNECT TO AN EXISTING THEME

WE RE GOING TO EXECUTE `shopify theme serve` (BUT NOT JUST YET, **YOU NEED TO READ NEXT INFORMATIONS**)

FIRST GO INTO SHOPIFY STORE DASBORD AND FIND ID OF YOUR THEME (DO THIS FOR THEME YOU COPIED, BECAUSE LETS PLAY WITH THAT THEME, BUT IT DOESSN'T MATTER ANYWAYS)

CLICK ON `Theme` (LEFT MENU) --> YOU SHOUD SEE YOUR PUBLISHED THEME AND A LITTLE BIT LOWER YOU HAVE COPY THEME WE MADE, CLICK ON `Customize` FOR MENTIONED THEME

**THE THING WE NEED IS NUMBER INSIDE URL, LIKE THI `/45246246512/`**

WE ARE PULLING (RETREIVING THEME FROM SHOPIFY) (MAKE SURE TO NAVIGATE IN YOUR FILE SYSTEM WHERE YOU WANT (BUT IF YOU ARE NOT IN THAT FOLDER, YOU CAN SPECIFY IT IN COMMAND))

***
***

WHEN I WAS DOING THIS THERE WAS A PROBLEM, AND PROBLEM WAS THAT YOU COULDN'T PULL A THEME IF YOU WERE NOT STAFF AT YOUR STORE (IT DOESN'T MATTER IF YOU ARE OWNER, THE STAFF MEMBER LIST SHOULDN'T BE EMPTY AND OUR I EMPTY (SE THAT AT `Settings` --> `Users And Permissions`))

[THIS IS A WORKAROUND](https://github.com/Shopify/shopify-cli/issues/1361#issuecomment-879426041)

>> This happens because when you create a Development store, it won't properly link your Shopify Partners account to the new created store.

>> This is what I do to solve the problem on my side:

>> 1.- Logout from the Development store admin dashboard
>> 2.- Login again by visiting the direct URL. Example: `https://[store-name].myshopify.com/admin`

>> Here use your Shopify Partners account (the one that you used to create the development store). Don't worry if you see an error message or if you have to login again. Ideally you should see the admin dashboard again.

>> 4.- Login to your Shopify account (not Partners). Go to: https://shopify.com/login

>> At this point you should see the new Development store listed. This means it is now linked to your account.

>> Go back to the CLI and try again. You may have to do shopify whoami and/or shopify logout shopify login

***
***

I DID IT LIKE THIS: **I OPENED NEW PARTNER ACCOUNT** (JUST IN CASE)

IN MY STORE (OUR STORE WE ALREADY MADE FOR THIS PROJECT) DASBOARD I GAVE A PERMISSION TO THE NEW USER (`Settings` (bottom left) ==>  `Users and permissions` --> `Add Staff`) **I ADDED A STAFF MEMBER**

**I LOGGED OUT FROM EVERYTHING AND I WENT TO MY STORES URL `https://<store name>.myshopify.com/admin` (DONT FORGET SLASH ADMIN)**

**I LOGED IN WITH MY NEWLLY CREATED ACCOUNT (SO I'M IN A STORE AS A STAFF MEMBER)**

***
***

***
***

**LETS FIRST LOGIN LOCALLY, LIKE I SAID WE ARE LOGGING IN WITH AN NEW ACCOUNT (STAFF MEMBER)**

```
shopify login --store <name of the store>.myshopify.com
```

***
***

NOW WE CAN PULL

WE ARE GOING TO PULLL HERE IN OUR PROJECT

```
shopify theme pull --themeid=<number I mentioned> <path where you want to put your theme on your filesystem (OR NOTHING IF YOU ALREAY NAVIGATED TO THAT PATH)>
```

## SO WE PULLED OUR THEME IN OUR PROJECT FOLDER

WE HAVE ALL THE FILES

WE CAN COMMIT AND PUSH OUR THEME TO GITHUB (I GUESS IT IS SAFE)

# RUNNING OUR THEME

READ HERE: <https://shopify.dev/themes/tools/cli/theme-commands#serve>

OUR THEME IS IN OUR PROJECT FOLDER SO WE CAN RUN

```
shopify theme serve
```

**YOU ARE GETTING 3 THINGS**

- LOCALHOST WHERE YOUR DEVELOPMENT THEME IS BEING SERVED

- LINK TO AN INSTANCE OF THEME EDITOR (YOU AN ONLY **UNDEPLOY THIS BY RUNNING `shopify logout`**)

- AND PREVIEW LINK

## IMPORTANT THING ABOUT LOCALHOST

**IF YOU TRY OPENING IT YOU'LL BE PROPTED FOR PASSWORD**

THAT IS NOT YOUR ACCOUNTS PASSWORD, THAT IS THE PSSWORD GENERATED IN YOUR STORE

IN YOUR STORE YOU CAN VIEW IT AND CHANGE IT BY GOING TO `Online Store`(left menu) ==> `Preferences` ==> `Password protection`

I CHANGED PASSWORD OF THE STORE SO IT IS ESIER FOR ME TO DEVELOP

SAME PASSWORD YOU NEED TO ENTER FOR THE PREVIEW LINK

## THEME STAYS ON YOUR COMPUTER AS YOU IMAGINE, BUT IF YOU WANT TO PUSH OR PUBLISH THEME, YOU CAN USE THESE COMMANDS

[`push`](https://shopify.dev/themes/tools/cli/theme-commands#push)

[`publish`](https://shopify.dev/themes/tools/cli/theme-commands#publish)

BUT BEFORE MENTIONED COMMANDS YOU ALSO WANT TO CHECK FOR ERRORS

AND THIS CHECKS FOR ERRORS

[`check`](https://shopify.dev/themes/tools/cli/theme-commands#check)

# OK, NOW I OPENED EDITOR AND TRIED TO CHANGE SOME STUFF

IT WORKED, I EDITED AND SAVED

AND I RELOADED LOCALHOST, AND I CAN SEE THE CHANGES I MADE WERE APPLIED

# THERE IS A ONE PROBLEM AND THAT IS AN ERROR MESSAGE THAT IS SHOWN AFTER I SERVE THE THEME

IT LOOKS LIKE THIS

```
[Note] You cannot use gems with Shopify CLI.
[LoadError] cannot load such file -- 2.7/ffi_c
       They are disabled.
       Please don't modify the CLI locally.
       If you would like to contribute to the CLI project, please refer to
       https://github.com/Shopify/shopify-cli/blob/main/.github/CONTRIBUTING.md

```

I DON'T KNOW IT'S IMPACT (MAYBE THE IMAPACT IS THAT I NEED TO RELOAD LOCALHOST TO SEE CHANGES)

ONY THING I FOUND IS SOME PEOPLE POSTING QUESTIONS ABOUT THIS ERROR

<https://githubmemory.com/repo/Shopify/shopify-app-cli/issues?cursor=Y3Vyc29yOnYyOpK5MjAyMS0wNy0yNFQwODoxNDo0OSswODowMM44vcis&pagination=next&page=2>

<https://community.shopify.com/c/technical-q-a/wsl-shopify-cli-3-0-ffi-c-loaderror/m-p/1271505>

GITHUB ISSUE

<https://github.com/Shopify/shopify-cli/issues/1405>

# I'M INTERESTED WOULD LOCALHOST SHOW US AUTHOMATIC CHANGE IF WE EDIT SOME FILE

I DID THAT AND SEEMS TO WORK, I CHANGED SOME CSS INSIDE SOME LIQUID FILE, AND CHANGE WAS IMMEDIATE

# YOU CAN TRY PUSHING CHANGES

ADD SOME `style` ATTRIBUTE AND BUT BACKGROUND COLOR ON SOMETHING

AND THEN PUSH

```
shopify theme push
```

NOW GO TO THE DASBOARD **CLICK ON PREVIEW OF OUR COPY OF OUR THEME, SINCE WE PUSHED THERE, AND WE EXPECT CHNGES TO BE MADE THERE**

AND I CAN SEE THAT CHANGES ARE REALLY APPLIED

THAT MEANS THAT WE "REPUBLISHED" COPY OF OUR THEME, SINCE WE COULD SEE CHANGES ON OUR COPIED THEME, WHICH HAS ITS PREVIEW LINK LIKE I SAID

WE FORGOT TO CHECK OUR THEME FOR ERRORS AND OTHER STUFF, BEFORE PUBLISHING

LETS TRY THIS NOW

```
shopify theme check
```

I SEE AROUND 70 OFFENSES; YES THEY CALL THEM LIKE THAT

**I NEED BETTER TERMS TO USE WHEN TALKING ABOUT PUBLISHING, BECAUSE WE DID MAKE CHANGES AND WE MAKE THEM IN THEME THAT IS A COPY**

THEY CALL ALSO THIS THEMS AS **`UNPUBLISHED THEMES`** BECAUSE THEY ARE NOT SERVED TO THE PUBLICK, AND ONLY YOU HAD TO DECIDE TO HOOM YOU WANT TO SHOW IT BY SENDING THEM LINK OF PREVIEW AND BY GIVING THEM THE PASSWORD FOR THE THEME

# IF YOU WANT TO CREATE NEW "UNPUBLISHED" COPY OF YOUR THEME, YOU CAN DO THAT THROUGH COMMAND LINE, BY ADDING `--unpublished` FLAG

YOU SETT UP A NEW NAME AND YOU HAVE MULTIPLE COPIES, OR MULTIPLE UNPUBLIHED VERSIONS YOU CAN SEND TO THE CLIENTS AS A PREVIEWS

# I CAN USE CLI TO PUBLISH THEMES AS WELL

THIS SHOULD CHANGE AND REPUBLISH OUR DEPLOYED THEME

LETS TRY DOING THIS

```
shopify theme publish
```

AND STILL YOU ARE GOING TO BE PROMPTED ABOUT WHAT THEME YOU WANT TO PUBLISH

SO YOU CAN PICK WHAT THEME YOU WNT TO PUBLISH IN PLACE OF OUR DEFAULT THEME

WE ONLY HAVE ONE, AND WE PICKET THAT 

I WENT TO THE DASBOARD AND NOW YOU CAN SEE THAT COPIED THEME BECAME YOUR DEFAULT THEME

# IN DOCS I ALSO CAN SEE MANY OTHER COMMANDS AND OPTIONS

FOR EXAMPLE `delete`

YES YOU CAN DELETE THEME FROM CLI

LEARN ABOUT OTHER THEMES ON YOUR OWN

<https://shopify.dev/themes/tools/cli/theme-commands#delete>

# YOU CAN ALWAYS SEE WHO YOU ARE AND IN WHAT STORE YOU ARE LOGGED IN BY EXECUTING THIS

```
shopify whoami
```
