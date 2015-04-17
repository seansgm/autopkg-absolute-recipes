#AutoPkg Recipes for Absolute Manage

Absolute Manage have provided a guide to [install](http://forums.absolute.com/kb.php?a=1062&hilit=autopkg)

For information on AutoPkg please read the [wiki](https://github.com/autopkg/autopkg/wiki/Getting-Started)

To add the packages into Absolute you will require [AbsoluteManageExport](https://github.com/tburgin/AbsoluteManageExport)

All these recipes require a parent.  Look at the ParentRecipe key in the file.  For example, Firefox.Absolute.recipe

        <key>ParentRecipe</key>
        <string>com.github.autopkg.pkg.Firefox_EN</string>
        
Alternatively, you can get parent info running:

        autopkg info Firefox.Absolute
        
which in turn will show all parents

    Recipe file path:    /Volumes/DATA/autopkg/Recipes/Absolute/Firefox.Absolute.recipe
    Parent recipe(s):    /Volumes/DATA/autopkg/RecipeRepos/com.github.autopkg.recipes/Mozilla/Firefox.pkg.recipe
                         /Volumes/DATA/autopkg/RecipeRepos/com.github.autopkg.recipes/Mozilla/Firefox.download.recipe

##Overrides

Information on recipe overrides can be found [here](https://github.com/autopkg/autopkg/wiki/Recipe-Overrides)

Consider using overrides for some keys, e.g.

* sd\_name\_prefix
* payload\_name\_prefix
* add\_s\_to\_availability\_date

###Example

Firefox override

        <key>Identifier</key>
        <string>local.Override.Absolute.Firefox</string>
        <key>Input</key>
        <dict>
                <key>LOCALE</key>
                <string>en_GB</string>
                <key>NAME</key>
                <string>Firefox</string>
                <key>RELEASE</key>
                <string>latest</string>
                <key>sd_name_prefix</key>
                <string>ABSOLUTE-</string>
                <key>payload_name_prefix</key>
                <string>ABSOLUTE-</string>
                <key>add_s_to_availability_date</key>
                <integer>86400</integer>
        </dict>
        <key>ParentRecipe</key>
        <string>local.amsdpackages.FirefoxESR</string>

autopkg info will also show any overrides if there are any

        autopkg info Firefox.Absolute.Override


    Input values: 
        LOCALE = "en_GB";
        NAME = Firefox;
        RELEASE = latest;
        "add_s_to_availability_date" = 86400;
        "payload_name_prefix" = "ABSOLUTE-";
        "sd_name_prefix" = "ABSOLUTE-";
