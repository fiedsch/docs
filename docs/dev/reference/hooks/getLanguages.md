---
title: "getLanguages"
description: "getLanguages hook"
tags: ["hook-system"]
aliases:
    - /reference/hooks/getLanguages/
    - /reference/hooks/getlanguages/
---


The `getLanguages` hook allows to modify the system's list of languages.

{{% notice note %}}
Using the `getLanguages` hook has been deprecated and will no longer work in Contao 5.0. Decorate the `Contao\CoreBundle\Intl\Locales` 
service instead.
{{% /notice %}}


## Parameters

1. *array* `$compiledLanguages`

    The array containing the languages as filled by `\Contao\System::getLanguages()` according 
    to the system configuration. This parameter has to be passed by reference if you 
    want your changes to become effective.

2. *array* `$languages`

    The list of languages from the system config file `languages.php` with english
    language names.

3. *array* `$langsNative`
 
    The list of languages with native language names (also read from from the system 
    config file `languages.php`).
    
4. *bool* `$installedOnly`
 
    Indicates whether only languages installed in the back end should be considered
    in the result. 


## Example

```php
// src/EventListener/GetLanguagesListener.php
namespace App\EventListener;

use Contao\CoreBundle\DependencyInjection\Attribute\AsHook;

#[AsHook('getLanguages')]
class GetLanguagesListener
{
    public function __invoke(array &$compiledLanguages, array $languages, array $langsNative, bool $installedOnly): void
    {
        // Make your changes to $compiledLanguages
    }
}
```


## References

* [\Contao\System#L574-L581](https://github.com/contao/contao/blob/4.7.6/core-bundle/src/Resources/contao/library/Contao/System.php#L574-L581)
* [languages.php](https://github.com/contao/contao/blob/4.7.6/core-bundle/src/Resources/contao/config/languages.php)
