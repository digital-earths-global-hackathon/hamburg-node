This repository edits the website. The finished version is rendered at https://digital-earths-global-hackathon.github.io/hamburg-node/

This website is rendered using [Hugo](https://gohugo.io), the theme usded is called [Hugo Scroll](https://themes.gohugo.io/themes/hugo-scroll/).



## Setting up your own website
Here are some hints on how to set up the website for your hackathon location ([Copy](#copy), [Edit](#edit)) and how to add content to the website ([Add content](#add-content)).

### Copy
Create your own copy of the repository.
?? forking or cloning? 

### Edit

Here are the locations in the repository where you need to change the variable values to adjust the website to another location.

```content/homepage/``` is the location for website content files.

```content/images/``` is the location for the image files used on the website.

```content/_index.md```: change header information in this file:

- change values for ```header_headline:``` and ```header_subheadline:``` to match your node's location. 

- ```header_image:``` points to the logo displayed in the header. You only need to change this if you want to exchange the website logo.

```config.toml```: 
- set ```baseURL``` to the url your page is deployed at.
- use ```title``` to change the website title displayed in the browser
- ```[params]```:
  - you can keep the ```favicon``` as it is or change to an icon you'd like to use
  - ```title``` change to match your node location
  - ```keywords``` add or change

### Add content

As a first step you can change the text in the already included files of this repository. And if you want to change the order of the menu items or add additional pages, follow the instructions below. The markdown files with the website content are located under ```content/homepage/```

#### Main page content

Every page contains a front matter section:

```
---
title: "Registration"
weight: 2
header_menu: true
---
```

- ```title:``` title of the section
- ```weight:``` location in the navigation menue (the lower the number the further in the front)
- ```header_menu:``` if set to *true*, the section will be referenced in the menu at the top of the page

Additional options for the front matter:
- ```header_menu_title:``` if you want to change the title in the header menu (e.g. shorten it)
- ```navigation_menu_title:``` if you want to change the title in the navigation menu

#### Separate subpages

You can also create a **dedicated page** that contains more information.
- ```detailed_page_path:``` can be used to give the path to a subpage which contains more detailed information. If this option is used, the link in the header menu will refer to the subpage.
- ```detailed_page_homepage_content:``` if this is set to *true* or missing, the content of the file will still be rendered on the main page.

See an example website of the original Hugo-Scroll theme [here](https://zjedi.github.io/hugo-scroll/).

To create a subpage which is only linked to from the header menu, you can add a markdown file to ```content/homepage/subpage.md``` with the following front matter:

```
title: "This is a subpage"    # Subpage title
weight: 98                    # to be last in the menu
header_menu_title: "Subpage"  # to shorten the title in the header menu
header_menu: true             # entry in the header menu
detailed_page_homepage_content: false  # only create the link, don't render this file
detailed_page_path: /extra_page/ # path to file with subpage content
```

The content you want to present on a subpage will need to be in the file ```content/extra_page.md```. This page is now only accessible via the link in the header menu. The file ```content/extra_page.md``` could look like this:

```
---
title: Extra Page
---

This is the extra page content. Where more detailed information can be given.
```

If you also want to have the subpage represented on the main page, you need to set ```detailed_page_homepage_content:``` to *true* and add the content to ```content/homepage/subpage.md```. For example: 

```
---
title: "This is a subpage"    # Subpage title
weight: 98                    # to be last in the menu
header_menu_title: "Subpage"  # to shorten the title in the header menu
header_menu: true             # entry in the header menu
detailed_page_homepage_content: true  # only create the link, don't render this file
detailed_page_path: /extra_page/
---

This is the subpage content on the main page. You can link to the full subpage from here as well: [subpage](extra_page).
```


## Building locally

To work locally with this project, you'll have to follow the steps below:

1. Fork, clone or download the project.
2. Install `git`.
3. [Install](https://gohugo.io/getting-started/installing/) Hugo.

4. Preview your project:

   ```shell
   hugo server
   ```

5. Add content.
6. Optional. Generate the website:

   ```shell
   hugo
   ```

Read more at Hugo's [documentation](https://gohugo.io/getting-started/).

<!-- ## Use a custom theme

Hugo supports a variety of themes.

Visit <https://themes.gohugo.io/> and pick the theme you want to use. In the
Pages example, we use <https://themes.gohugo.io/themes/gohugo-theme-ananke/>.


## Did you fork this project?

If you forked this project for your own use, please go to your project's
**Settings** and remove the forking relationship, which won't be necessary
unless you want to contribute back to the upstream project. -->

