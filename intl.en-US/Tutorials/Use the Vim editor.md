# Use the Vim editor {#concept_188767 .concept}

Vim is a text editor that is developed as an improved version of the vi editor. It can display text with extra format details, such as font color and underline. Vim is an essential tool in Linux. For example, you can use this tool to edit configuration files of Web applications. This topic describes the modes and commonly used commands of Vim.

## Vim modes {#section_u9e_ujf_y2m .section}

|Mode|Function|Mode switch|
|----|--------|-----------|
|Normal mode \[DO NOT TRANSLATE\]

 |In this mode, you can copy, paste, and delete characters or lines.| -   The tool enters normal mode when you run the `vim <file name>` command to open a file.
-   To switch from other modes to this mode, press the `Esc` key.

 |
|Insert mode \[DO NOT TRANSLATE\]

 |In this mode, you can insert characters.|To switch from the normal mode to this mode, enter any of the following characters: `i, I, a, A, o, O`. **Note:** You will see `-- INSERT --` in the lower-left corner of the editor after you switch to this mode.

 |
|Replace mode \[DO NOT TRANSLATE\]

 |In this mode, you can replace characters.|To switch from the normal mode to this mode, enter `R`. **Note:** You will see `-- REPLACE --` in the lower-left corner of the editor after you switch to this mode.

 |
|Visual mode \[DO NOT TRANSLATE\]

 |In this mode, you can select a range of text. You must select a range of text before running commands such as copy, replace, and delete on the specified text.|To switch from the normal mode to this mode, enter `v`. **Note:** You will see `-- VISUAL --` in lower-left corner of the editor after you switch to this mode.

 |
|Command mode \[DO NOT TRANSLATE\]

 |In this mode, you can search and replace strings, display line numbers, save file changes, and exit the editor.|To switch from the normal mode to this mode, enter `:`.|

## Insert {#section_tr1_ny1_buk .section}

 **Commands** 

-   i: inserts a character to the left of the current character
-   I: inserts a character at the start of the current line
-   a: inserts a character to the right of the current character
-   A: inserts a character at the end of the current line
-   o: inserts a new line below the current line
-   O: inserts a new line above the current line

 **Examples** 

Assume that you want to edit an example.conf file that contains the following content:

``` {#codeblock_x1k_glz_ckt}
# To be able to use the functionality of a module which was built as a DSO you
# have to place corresponding `LoadModule' lines at this location so the
# directives contained in it are actually available _before_ they are used.
# Statically compiled modules (those listed by `httpd -l') do not need
# to be loaded here.
#
# Example:
# LoadModule foo_module modules/mod_foo.so
#
Include conf.modules.d/*.conf			
```

Example 1: Insert `Location` as the first line of the example.conf file. To do this, follow these steps:

1.  Run the `vim example.conf` command to open the file in normal mode.
2.  Enter `i` to switch to the insert mode.
3.  Enter `Location`.
4.  Press the Enter key to switch to a new line.
5.  Press the `Esc` key to exit the insert mode.
6.  Enter the `:wq` command to save the changes to the file and then exit the editor.

    After you make this insertion, the example.conf file contains the following content:

    ``` {#codeblock_bro_cl9_h9w}
    Location
    # To be able to use the functionality of a module which was built as a DSO you
    # have to place corresponding `LoadModule' lines at this location so the
    # directives contained in it are actually available _before_ they are used.
    # Statically compiled modules (those listed by `httpd -l') do not need
    # to be loaded here.
    #
    # Example:
    # LoadModule foo_module modules/mod_foo.so
    #
    Include conf.modules.d/*.conf			
    ```


Example 2: Insert \# at the start of line ten in the `example. conf` file. To do this, follow these steps:

1.  Run the `vim example.conf` command to open the file in normal mode.
2.  Enter `:10` to move the cursor to line ten.
3.  Enter `I` to switch to the insert mode.
4.  Enter `#`.
5.  Press the `Esc` key to exit the insert mode.
6.  Enter the `:wq` command to save the changes to the file and then exit the editor.

    After you make this insertion, the example.conf file contains the following content:

    ``` {#codeblock_i6k_pyq_yjx}
    # To be able to use the functionality of a module which was built as a DSO you
    # have to place corresponding `LoadModule' lines at this location so the
    # directives contained in it are actually available _before_ they are used.
    # Statically compiled modules (those listed by `httpd -l') do not need
    # to be loaded here.
    #
    # Example:
    # LoadModule foo_module modules/mod_foo.so
    #
    #Include conf.modules.d/*.conf		
    ```


Example 3: Insert LoadModule rewrite\_module modules/mod\_rewrite.so in the line below the `Include conf.modules.d/*.conf` line of the `example.conf` file. To do this, follow these steps:

1.  Run the `vim example.conf` command to open the file in normal mode.
2.  Run the `/Include conf.modules.d/*.conf` command to find the target line.
3.  Enter `o` to switch to the insert mode.
4.  Enter `LoadModule rewrite_module modules/mod_rewrite.so`.
5.  Press the `Esc` key to exit the insert mode.
6.  Enter the `:wq` command to save the changes to the file and then exit the editor.

    After you make the insertion, the example.conf file contains the following content:

    ``` {#codeblock_pog_fe4_zys}
    # To be able to use the functionality of a module which was built as a DSO you
    # have to place corresponding `LoadModule' lines at this location so the
    # directives contained in it are actually available _before_ they are used.
    # Statically compiled modules (those listed by `httpd -l') do not need
    # to be loaded here.
    #
    # Example:
    # LoadModule foo_module modules/mod_foo.so
    #
    Include conf.modules.d/*.conf
    LoadModule rewrite_module modules/mod_rewrite.so							
    ```


## Replace {#section_tq7_lnt_5in .section}

 **Commands** 

R: replaces the highlighted characters, until you press the `Esc` key to exit the replace mode.

 **Example** 

Assume that you want to edit an example.conf file that contains the following content:

``` {#codeblock_4ll_e6h_c6q}
# AllowOverride controls what directives may be placed in .htaccess files.
# It can be "All", "None", or any combination of the keywords:
# Options FileInfo AuthConfig Limit
#
AllowOverride None				
```

For example, to replace `AllowOverride None` with `AllowOverride All` in the example.conf file, follow these steps:

1.  Run the `vim example.conf` command to open the file in normal mode.
2.  Run the `/AllowOverride None` command to find the target.
3.  Move the cursor to the first letter of `None`.
4.  Enter `R` to switch to the replace mode.
5.  Enter `All` and a space.

    **Note:** The word `None` has four characters, but the word `All` has three characters. To replace all the four characters of None, you must type an extra white space following the three characters of All.

6.  Press the `Esc` key to exit the replace mode.
7.  Enter the `:wq` command to save the changes to the file and then exit the editor.

    After you make the replacement, the example.conf file contains the following content:

    ``` {#codeblock_dd0_djk_dzz}
    # AllowOverride controls what directives may be placed in .htaccess files.
    # It can be "All", "None", or any combination of the keywords:
    # Options FileInfo AuthConfig Limit
    #
    AllowOverride All							
    ```


## Delete {#section_lh9_ubw_4fb .section}

 **Commands** 

-   x: deletes the highlighted character.
-   nx \(n represents a number\): deletes the highlighted character and the n-1 characters after it.
-   dd: deletes the line in which the cursor is located.
-   ndd \(n represents a number\): deletes the line in which the cursor is located and the n-1 lines below it.

 **Examples** 

Assume that you want to edit an example.conf file that contains the following contents:

``` {#codeblock_vi3_na4_4m3}
# Listen: Allows you to bind Apache to specific IP addresses and/or
# ports, instead of the default. See also the <VirtualHost>
# directive.
#
# Change this to Listen on specific IP addresses as shown below to
# prevent Apache from glomming onto all bound IP addresses.
#
#Listen 12.34.56.78:80
Listen 80				
```

Example 1: Delete `#` at the start of the `#Listen 12.34.56.78:80` line of the example.conf file. To do this, follow these steps:

1.  Run the `vim example.conf` command to open the file in normal mode.
2.  Run the `/#Listen 12.34.56.78:80` command to find the target so that the cursor is on the `#` character.
3.  Enter the `x` command to delete `#`.
4.  Enter the `:wq` command to save the changes to the file and then exit the editor.

    After you make the deletion, the example.conf file contains the following content:

    ``` {#codeblock_mc4_0cw_gk2}
    # Listen: Allows you to bind Apache to specific IP addresses and/or
    # ports, instead of the default. See also the <VirtualHost>
    # directive.
    #
    # Change this to Listen on specific IP addresses as shown below to
    # prevent Apache from glomming onto all bound IP addresses.
    #
    Listen 12.34.56.78:80  
    Listen 80						
    ```


Example 2: Delete the `#Listen 12.34.56.78:80` line and the line below in the example.conf file. To do this, follow these steps:

1.  Run the `vim example.conf` command to open the file in normal mode.
2.  Run the `/#Listen 12.34.56.78:80` command to find the target.
3.  Enter the `2dd` command to delete the following contents.

    ``` {#codeblock_jon_hsp_13h}
    #Listen 12.34.56.78:80
    Listen 80
    ```

4.  Enter the `:wq` command to save the changes to the file and then exit the editor.

    After you make the deletion, the example.conf file contains the following content:

    ``` {#codeblock_r91_1ko_l9l}
    # Listen: Allows you to bind Apache to specific IP addresses and/or
    # ports, instead of the default. See also the <VirtualHost>
    # directive.
    #
    # Change this to Listen on specific IP addresses as shown below to
    # prevent Apache from glomming onto all bound IP addresses.
    #						
    ```


