
## Wordpress

Creating a new project:

- Download and install [WAMP](https://sourceforge.net/projects/wampserver/files/)

- Run WAMP, then go to http://localhost/phpmyadmin  make a user with username root, no password

- Log in and create a new database with the name of your project

- Download and extract the latest WordPress files from https://wordpress.org/download/

- Place the contents of the wordpress file in a new folder that you call whatever you want, example: 'project-name'. This is also your git repository, so make it now if you want.

- Place that folder in WAMP 'www' folder (Mine is at `C:\wamp64\www`) so it will be `C:\wamp64\www\project-name` 

- Create and download a bare bones theme from [underscores](https://underscores.me). Call it the name of your project. Don't forget to click advanced options and check `_sassify` and fill out the information.

- Extract the file and put it into "project-name/wp-content/themes" folder. Delete all the other default themes that come with wordpress. This themes folder is what you will want to push to github, so add a .gitignore file to  `C:\wamp64\www\project-name` that will ignore all the other folders and files except for the themes file (ask us or search google for a wordpress .gitignore file)

- Open your web browser and go to `localhost/project-name/wp-admin` (replace project-name with whatever you called your folder)

- Launch wordpress, select english, select the database you created earlier

- Go into appearances, themes. Select the theme you created.

Now every page in the 'template-pages' folder in that theme will show up as a template page when you create a new 'page' in wordpress. 
For example, you can make a file called homepage.php: `C:\wamp64\www\project-name\wp-content\themes\project-name\template-pages\homepage.php`
then at the top of the file you can put this: 

```
<?php

/*
Template Name: homepage
Template Post Type: page
*/

get_header("");

?>
```

And the page will show up as a template page with the name 'homepage' when you create a page in wordpress. 
For example, go to localhost/project-name/wp-admin and click on 'Pages' and add a new page, on the right click on the Templates dropdown and you should find the template that you just created! Yay!

- Go to dashboard, click on 'Set up your homepage' and set it to static page

You can also edit your header.php file, footer.php and mess around with everything else in general. Don't forget to compile your scss to a style.css file in the root of the theme folder (so you want it to be in  `C:\wamp64\www\project-name\wp-content\themes\project-name\style.css` Use the VSCode Extention "live sass compiler' as I explained in my <a href="windows.md">setup</a> readme. Good luck!

**Remember, everything you change in /wp-admin is only changed in your local machine, try to keep those changes minimal (ie: only to add a page)
What you want to change the most is your theme :)**
