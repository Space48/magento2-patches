# Magento Patches

A collection of Core Magento fixes currently waiting to be merged into Magento.

Sometimes you encounter a core magento bug which has been fixed in the main repo but is not yet distributed, this can be
frustrating and you might want the fix yesterday, magento2-patches collects these patches and utilises `vaimo/composer-patches`
to apply them to your code base.

## Installation

`composer require space48/magento2-patches`


## Add a patch

Go to the PR in the magento2 repo which you want to apply, add .patch to the end of the url and github will produce a
patch file for you, put this file in `patches/Magento_ModuleName/magento2-issue-ISSUENUMBER.patch` and then add an entry
to the `composer.json` file of this repository:

```json
"extra": {
    "patches": {
        "magento/module-name": {
            "Excellent description of the issue which people will see on composer install": {
                "source" : "patches/Magento_ModuleName/magento2-issue-ISSUENUMBER.patch",
                "version" : [
                    "MAGENTO-VERSION_NUMBER e.g. 100.2.*"
                ]
            }
        },
```

Then on composer install you will see the patch applied:

```
Processing patches configuration
  - Applying patches for magento/module-braintree (1)
    ~ space48/magento2-patches: patches/Magento_ModuleName/magento2-issue-ISSUENUMBER.patch [NEW]
      Excellent description of the issue which people will see on composer install

Writing patch info to install file
```
