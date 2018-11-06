# Shopware file system
* engine/ <br>
contains all core Shopware files <br><br>
/engine/shopware/Config/Default.php contains all Shopware settings which can be ovveriden in /config.php file
* custom/ <br>
contains all plugins (new feature from Shopware 5.2)
* media/ <br>
contains all uploaded media files
* theme/ <br>
contains all themes files for the shop
* var/ and web/ <br>
conatins cached files and logs
### Filesystem for theme folder (theme/)
* Backend/
* Frontend/
    * Bare/ <br>
    hint: contains all HTML files
        * documents/ <br>
        HTML files for reports
        * frontend/ <br>
        contains HTML files for shop
            * index/ <br>
            contains all static HTML (header, footer, etc)
            * home/ <br>
            contains HTML for homepage
        * theme.php <br>
        contains all theme backend settings and lets add custom backend theme configuration (explained later)
    * Responsive/ <br>
    contains all js, less files  
    
# Theme manager and creation of new theme
### Theme configuration
Configuration > Theme manager > Configure theme (button)
### Creation of new theme via theme manager
Configuration > Theme manager > Create theme (button) <br>
* set required options
* filesystem for new theme: *themes/*
* Shopware creates empty theme directory tree
* theme.php - themes settings

# Theme inheritance
New theme inherites from Bare (HTML) and Responsive (js, CSS) themes
### how to inherit a theme template (HTML) file
- copy a *.tpl file from Bare theme which you want to override 
- use smarty {extends} command in template to inherit from another file
- add **parent:** prefix to smarty command before file path to access code of the inherited file <br>
**{extends file = "parent:frontend/index/index.tpl"}** - this smarty command will pull entire code from file path block

### Smarty - block system
- Smarty defines sections for the HTML code (modularization)
- Smarty is identified by an unique name attribute
- Smarty integrates with the inheritance system
- Smarty can be manipulated by other themes or plugins <br><br>
<pre>
    {block name = 'frontend/index/logo'}
</pre>
        <div class="logo">
            <h1>{$sShopname}</h1> //smarty variable
        </div>
<pre>
    {/block}
</pre>
* note: not so easy to reorder existing SMARTY blocks!
* source: https://www.smarty.net/

### Replace or extend content of a SMARTY block
- by default the block will replace the content of its inherited version
- use **{$smarty.block.parent}** command to access original content of the inherited block <br>
<pre>
    {block name = 'frontend_index_logo'}
        {$smarty.block.parent} //this command will call inherited block content
</pre>
            //below is a custom html which will display under inherited block content
            <div class="logo--badge">
                <span>Free shipping</span>
            </div>
<pre>
    {/block}
</pre>
            