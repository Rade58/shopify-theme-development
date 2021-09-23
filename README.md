# DEVELOPING HEADER NAVIGATIONAL BAR WITH BOOTSTRAP

**LETS FIRST CREATE `sections` FOLDER; WHERE WE ARE GOING TO PUT OUR COMPONENTS IF I CAN CALL THEM LIKE THAT; BUT WAIT, WE DON'T NEED TO DO THAT BECAUSE I CAN SE THAT THAT FOLDER IS ALREADY CREATED AND THAT IT HAS BUNCH OF LIQUID FILES**

I PLACED THERE FILE CALLED `1_header.liquid`

```
touch sections/1_header.liquid
```

[FIND SOME NAVIGATION COMPONENT FROM BOOTSTRAP](https://getbootstrap.com/docs/5.1/components/navs-tabs/#base-nav)

COPY IT INSIDE MENTIONED FILE

NOW LET'S GO TO [LIQUID REFERENCE](https://shopify.dev/api/liquid/objects/linklist) AND LETS TRY WRITING FOR LOOP

IF YOU DON'T KNOW WHAT YOU ARE WRITING READ IT FROM REFERENCE

ALSO **KNOW IN YOUR HEAD THAT ONLY THIS IS POSSIBLE BECAUSE SOMEONE (ME OR SOMEONE ELSE) DID ADD NAVIGATION, THROUGH STORE DASBOARD INSIDE (YOU KNOW WHAT WE SPOKE IN PREVIOUS BRANCH (ADDING NAVIGATION ITEMS INSIDE MENUES)))**

```liquid
<nav class="nav-my">

<ul class="nav nav-list" >
  {% for link in linklists.main-menu.links %}

    {% assign child_list_handle = link.title | handleize %}

    {% if linklists[child_list_handle].links != blank %}
      
    <li class="nav-item">
      <a 
        href="{{link.url}}"
        class="nav-link"
        aria-current="page" 
      >
        {{ link.title }}  
      </a>
    </li>
    
      [{% for childlink in linklists[child_list_handle].links %}

      <li class="nav-item">
        <a 
          href="{{link.url}}"
          class="nav-link"
          aria-current="page" 
        >
          {{ link.title | escape }}  
        </a>
      </li>

      
      {% endfor %}]

    {% else %}

    <li class="nav-item">
      <a 
        href="{{link.url}}"
        class="nav-link active"
        aria-current="page" 
      >
        {{ link.title }}  
      </a>
    </li>

    {% endif %}
    
  {% endfor %}
</ul>
 </nav>
```

## WE NEED TO PLACE THI SECTION INSIDE BODY OF OUR THEME

```
code layout/theme.liquid
```

**NOT GOING TO SHOW YOU ENTIRE CODE, JUST KNOW THAT I ADDED THIS INSIDE body TAG, ON THE BEGINING**

```liquid
{% section '1_header' %}
```

YES IT WORKED, I ALREDY RUNNED `shopify theme serve` SO I COULD SEE CHANGES

BUT SO FAR I'M HATING THIS SYNTAX, IT IS SO CONTRA INTUITIVE

HOPEFULLY I'LL GROW TO LOVE IT
