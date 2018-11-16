# SMARTY
* SMARTY is a PHP template engine used in Shopware
* allows to organize HTML in related blocks
* when extending a *.tpl file you have to put HTML code inside existing SMARTY blocks.
* SMARTY v.3 docs: https://www.smarty.net/docs/en/
# SMARTY variables
* how to open front-end popup with all SMARTY variables:
    * use **{debug}** in any SMARTY block in *.tpl file (where you want to check existing variables)
    * refresh front-ent page
    * open blocked popup (from browser address URL bar)
    * refresh page again - the SMARTY variables popup should be visible
* how to debug SMARTY SMARTY variable object <br>
<pre>
{block name="frontend_index_logo"}
    {foreach $sCategories as $sCategory}
        < ul>
          < li>Category id: {$sCategory['id']}</ li>        //from debugging popup
          ...
          ...
          ...  
</pre>

# SMARTY resources
* official page: https://smarty.net <br>
don't use **append** or **prepand** commands in Shopware development. <br>
Use Instead **{$smarty.block.parent}** command
# How to debug template hints in Shopware
* use FroshProfiler plugin: https://github.com/FriendsOfShopware/FroshProfiler
