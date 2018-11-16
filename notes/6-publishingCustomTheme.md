* New theme should be deployed as a plugin

# Plugin structure

SwagTutorialTheme<br>
 ├── Themes<br>
 │    ├──Frontend<br>
 │    │   ├──TutorialTheme<br>
 │    │   │    ├── preview.png<br>
 │    │   │    ├── Theme.php<br>
 │    │   │    └── frontend<br>
 └── Bootstrap.php
 
# Required changes in Bootstrap.php file
<pre>
< ?php
class Shopware_Plugins_Frontend_SwagTutorialTheme_Bootstrap extends Shopware_Components_Plugin_Bootstrap
{
    /**Returns a marketing friendly name of the plugin.*/
    public function getLabel()
    {
        return 'Your custom theme as a plugin';
    }

    /**Returns the version of the plugin.*/
    public function getVersion()
    {
        return '1.0.0';
    }
}
</pre>

# QAing new theme plugin
* load plugin via plugin manager and active it (Configuration > Plugin manager)
* go to theme manager (Configuration > Theme manager), refresh view, check if new theme is available

# Resources
Shopware docs: https://developers.shopware.com/designers-guide/preparing-themes-for-the-community-store/#search-results