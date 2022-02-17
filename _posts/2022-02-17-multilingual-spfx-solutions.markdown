---
layout: post
title: "Multilingual SPFx solutions!"
date: 2022-02-17 12:02:06 +0530
categories: SPFx
---

One of the common asks across SharePoint, Viva Connections SPFx solutions is supporting multiple language of the content that appears inside SPFx user interfaces. The localization and translations, can be customized using SPFx solution from
`/src/../../loc` directory.

```bash
├── loc
│   ├── en-us.js
│   ├── *lang-country*.js
│   ├── mystring.d.ts
```

This uses a "key-value" approach to localization.

- First, notice `mystring.d.ts` is where the scafolded default "key" is stored. This
  is a typescript definition files and it informs TypeScript part of the codes about these localized string "key". So you declare
  your key and type inside an interface like below snippet:
  {% highlight javascript %}
  PropertyPaneDescription: string;
  BasicGroupName: string;
  DescriptionFieldLabel: string;
  {% endhighlight %}

- Next, there is also a scafolded default `en-us.js`. This is the default locale.This stores the values for `en` or English language used in `us` or United States as country. Similarly, for example, in german language for Germany you can translate the values and define it in a file called `de-de.js` in the same directory using the same "key" declared previously in the following way:
  {% highlight javascript %}
  "PropertyPaneDescription": "Beschreibung",
  "BasicGroupName": "Gruppenname",
  "DescriptionFieldLabel": "Beschreibungsfeld",
  {% endhighlight %}

- Now, at this point, we have all the required `loc` files and "key-value" ready to be used. To use it, the module defined in
  `mystring.d.ts` need to be imported `import * as strings`. If you notice some of the scalfolded files already have
  similar reference. Then just use it as typical variable in specific part of your solution following way:
  {% highlight javascript %}
  strings.PropertyPaneDescription
  {% endhighlight %}

- Finally, to test specific locale, run the gulp serve with `locale` parameter in the following way:(change the locale code according to your need)
  {% highlight javascript %}gulp serve --locale=de-de{% endhighlight %}

Check out the [spfx documentations][spfx-docs] for more info on how to get the most out of SPFx. Find all community samples here
at [PnP site][pnp-samples].

[spfx-docs]: https://docs.microsoft.com/en-us/sharepoint/dev/spfx/set-up-your-developer-tenant
[pnp-samples]: https://pnp.github.io/#samples

