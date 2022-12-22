# Git repository template for Wordpress projects
The main goal of the template is to strictly separate two areas of the Wordpress project, one that is developed by us(devs) 
the development part and second one that is independent of us, we will never touch and change it, non-development part. Here
you can see examples of both parts:
   1. development part:
      - custom theme.
      - custom plugin.
   2. non-development part:
      - Wordpress core.
      - third-party plugins.
      - folders to store some data, e.g. `wp-conten/uploads/`, some log files.

So the main idea is not to touch non-development part and work only with first one. We only store custom them and plugin files 
inside the repository and everything else is managed by installation script.
      


## Steps to set up project locally
1. Navigate to the folder where you want to install the project
    ```bash
    $ cd Projects/
    ```
2. Clone the repository.
    ```bash
    $ git clone git@github.com:alexakopi/wp-template.git
    ```
   you will get `wp-content/` directory with default theme folder in it, `.gitignore`, `README.md` and `local-setup.sh.temp` files.
   Purpose of `.gitignore` and `README.md` are obvious, however we will discuss specifics related to `.gitignore` in a separate chapter.
   The file we are interested in right now is `local-setup.sh.temp`, it is template for shell script to download Wordpress core, 
   set essential configurations and install Wordpress.
3. After cloning the repo, next step we need to do is to create `local-setup.sh` from `local-setup.sh.temp` file, edit newly created file 
   and change configuration variables to match our environment.
4. After setting the variables make sure that your current user can execute the script file and just run it in terminal.
    ```bash
    $ chmod +x local-setup.sh
    $ ./local-setup.sh
    ```
   the output should be something like:
   ```bash
   Success: WordPress downloaded.
   Success: Generated 'wp-config.php' file.
   Success: Updated the variable 'table_prefix' in the 'wp-config.php' file with the value 'frtech_'.
   Success: WordPress installed successfully.
   Success: Installed 1 of 1 plugins.
   Success: Installed 1 of 1 plugins.
   Success: WordPress installation verifies against checksums.
   ```
After completing those steps we have running Wordpress website(The core version will correspond to version set in shell script file),
with default theme. You can now log in to dashboard using credentials set in `local-setup.sh` file and activate the theme, if you had list
of the plugins in shell script you can also see them inside dashboard and activate them as well.
