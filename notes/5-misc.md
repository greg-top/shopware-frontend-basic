# How to display a price with currency in *.tpl file
<pre>
    < p> price {$product.price|currecy} //SMARTY variable with modifier < /p> 
</pre>

<p>Managing currency settings in Backend:</p>
Backend > Configuration > basic settings (search for currencies)

# How to create custom listing layout for a specific category
* go to Configuration > basic settings (search for categories/lists)
* in field **Available listing layout** add custom layout <br>
custom-food-listing.tpl:Custom food category listing layout;
* in file structure navigate to [custom_theme]/frontend/listing and create a file custom-food-listing.tpl
* create custom listing in template file, example:
<pre>
{extends file="parent:frontend/listing/index.tpl"}

{block name="frontend_index_content"}
    < div class="custom-listing">
        {$smarty.block.parent}
    < /div>
{/block}

{block name="frontend_listing_list_inline"}
    {$productBoxLayout = "custom"} {** shopware function which will create box--custom class **}
    < div class="custom-listing--listing">
        {foreach $sArticles as $sArticle}
            {include file="frontend/listing/product-box/box-custom.tpl"}
        {/foreach}
    < /div>
{/block}

{block name='frontend_index_content_left'}{/block}

{block name="frontend_listing_index_topseller"}{/block}
</pre> 
* clean cache (Configuration > cache performance, clean all caches from **cache tab** excepts **compile themes**)
* select custom listing layout for specific category:
    * go to Items > categories
    * choose category
    * set individual layout (if custom layout is not visible check 2nd point)
* tip: all included SMARTY blocks in *.tpl file can be override (also SMARTY blocks from included child templates) 
 
# Shopware SMARTY functions
* some of SMARTY functions can create a CSS classes in template files, example
<pre>
{$productBoxLayout="custom-food"} //willcreate a CSS class .box--custom-food for product tile container on listening page
</pre>