---
layout: post
title: "Multilingual SPFx solutions!"
date: 2022-02-17 12:02:06 +0530
categories: SPFx
---

One of the common asks across SPFx solutions in SharePoint and Viva Connections is supporting multiple languages of the content that appears inside SPFx user interfaces. The localization and translations can be customized using SPFx solution from
`/src/../../loc` directory.

```bash
├── loc
│   ├── en-us.js
│   ├── *lang-country*.js
│   ├── mystring.d.ts
```

This uses a "key-value" approach to localization.

- First, notice `mystring.d.ts` is where the scaffolded default “key” is stored. This is a typescript definition file and it informs the TypeScript part of the code about these
 localized string “keys”. So you declare your key and type inside an interface like the snippet below:   
 
```
  PropertyPaneDescription: string;
  BasicGroupName: string;
  DescriptionFieldLabel: string;
```

- Next, there is also a scaffolded default `en-us.js`. This is the default locale.This stores the values for `en` or English language used in the `us` or United States as a country. Similarly, for example, in German language for Germany you can translate the values and define it in a file called `de-de.js` in the same directory using the same “key” declared previously in the following way:
```
  "PropertyPaneDescription": "Beschreibung",
  "BasicGroupName": "Gruppenname",
  "DescriptionFieldLabel": "Beschreibungsfeld",
 ```

- Now, at this point, we have all the required `loc` files and the "key-values" ready to be used. To use it, the module defined in
  `mystring.d.ts` need to be imported `import * as strings`. If you notice, some of the scaffolded files already have similar references. Then just use it as a typical variable in a specific part of your solution in the following way:
```
  strings.PropertyPaneDescription
```

- Finally, to test specific locale, run the gulp serve with `locale` parameter in the following way(change the locale code according to your need):
 ```
 gulp serve --locale=de-de
 ```

Check out the [spfx documentations][spfx-docs] for more info on how to get the most out of SPFx. Find all community samples here
at [PnP site][pnp-samples].

[spfx-docs]: https://docs.microsoft.com/en-us/sharepoint/dev/spfx/set-up-your-developer-tenant
[pnp-samples]: https://pnp.github.io/#samples

