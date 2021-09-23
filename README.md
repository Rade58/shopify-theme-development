# FOR LOOPS AND SOME OTHER LIQUID THINGS

**WHEN "STORE MANAGER" (I CALLED IT LIKE THIS), STORE OWNER, ANYONE WHO HAS ACCESS TO THE DASBOARD OF THE STORE, ANYONE WHO KNOWS HOW TO OPERATE DASBOARD, DECIDES TO ADD SOMETHING, SOME INFO, IN INTENTION TO ADD DATA TO THE PART OF THE WEBSITE; WE WANT THAT TO REFLECT ON THE UI OF THE STORE, WE WANT THAT DATA TO BE RENDERED**

IDEA IS THAT HE ADS DATA AND WE AS A DEVELOPERS IN A THEME DEFINE DISPLAYING THAT DATA

**ONE OF THE EXAMPLES FOR THIS IS NAVIGATION**

## GO TO DASBOARD OF YOUR STORE AND IN LEFT MENU FOR (Online Store) YOU CAN FIND `Navigation`

YOU CAN SEE **Menus**

I HAVE TWO MENUS: Main (WITH ITEMS Home, Catalog, Contact), AND Footer (WITH ITEMS Search)

**AND EVERY OF THAT MENUES HAS `HANDLE` `AND HANDLES ARE USED TO ACCESS ATTRIBUTES OF LIQUID OBJECTS`**

YOU CAN CLICK ON Main OR Footer AND ADD OR REMOVE ITEMS FOR THESE NAVIGATION ELEMENTS

I AM GOING TO ADD NEW MENU, I CALLLED IT Products AND I ADDED ITEM THAT IS BASICALLY NAVIGATION THAT LEADS TO PAGE OF AALL PRODUCTS (JUST TO SHOW YOU THAT YOU CAN DO THIS)

**LETS ADD SOME NAVIGATION ITEMS TO THE MENU, THAT WAS HERE EARLIER**

FOR EXAMPLE LETS ADD NAVIGATION OF THE SINGLE PRODUCT (YOU CAN MAR IT "Product of the day" OR SOMETHING LIKE THAT, WHAT EVER YOU THINK OF`)

## OK NOW YOU CAN START YOUR STORE, TO SEE IF YOU HAVE ANY CHANGIS IN ANIMATION SEGMENT

```
shopify theme serve
```

GO ON LOCALHOST AND SEE

AND YES, I DO HAVE A NAVIGATION ITEM I ADDED, I CLICK ON THE LINK AND I AM TAKEN TO THE PAGE OF THAT SINGLE PRODUCT

## IN DASBOARD WE COULD ALSO ADD A PAGE IN `Pages` SECTION OF YOUR `Online Store`; AND WE CAN ADD LINK FOR THAT PAGE

YOU KNOW HOW TO DO IT, NO NEED FOR ME TO EXPLAIN HOW

# NOW IT IS PRETTY SUGESTIVE THAT YOU HAVE FOR LOOP SOMEWHERE IN YOUR CODEBASE, IF MAGICALLY WHEN WE ADD NAVIGATION ITEM, THAT ITEM SHOWS ON YOUR STORE ON LOCALHOST

NAVIGATION IS PLACED IN THE HEADER (ALSO IN SOME DRWER) AND I CAN SEE THIS PARTS INSIDE COEBASE

I ALSO OPENED INSPECTOR IN BROWSER AND FIND PART OF THE UI I WANT AND I SAW THE CLASSES AMD OPENED EADER LIQUID FILE AND FOUND WHAT I WAS SEARCHING

**OR GO BACK TO DASBORD AND NAVIGATION AND CHECK THE HANDLES, AND YOU CAN SEARCH CODEBASE BY USING THESE HANDLES**

I EXTRACTED THIS FROM `sections/header.liquid`

IT IS AN UNORDERED LIST WITH LIST ITEM AND LIST ITEMS ARE WRAPPED INTO FOR LOOP 

```liquid
<ul class="header__submenu list-menu list-menu--disclosure caption-large motion-reduce" role="list" tabindex="-1">
  {%- for childlink in link.links -%}
    <li>
      {%- if childlink.links == blank -%}
        <a href="{{ childlink.url }}" class="header__menu-item list-menu__item link link--text focus-inset caption-large{% if childlink.current %} list-menu__item--active{% endif %}"{% if childlink.current %} aria-current="page"{% endif %}>
          {{ childlink.title | escape }}
        </a>
      {%- else -%}
        <details>
          <summary class="header__menu-item link link--text list-menu__item focus-inset caption-large">
            {{ childlink.title | escape }}
            {% render 'icon-caret' %}
          </summary>
          <ul class="header__submenu list-menu motion-reduce">
            {%- for grandchildlink in childlink.links -%}
              <li>
                <a href="{{ grandchildlink.url }}" class="header__menu-item list-menu__item link link--text focus-inset caption-large{% if grandchildlink.current %} list-menu__item--active{% endif %}"{% if grandchildlink.current %} aria-current="page"{% endif %}>
                  {{ grandchildlink.title | escape }}
                </a>
              </li>
            {%- endfor -%}
          </ul>
        </details>
      {%- endif -%}
    </li>
  {%- endfor -%}
</ul>
```

IT IS PRETTY OVERWELMING BUT HOPEFULLLY I'LL LEARN THIS SYNTAX


