---
title: Snippets for Shopify Dawn Theme
author: Brandon Baek
date: 2022-09-10
categories: [Tutorial, Shopify]
tags: [Shopify, Dawn Theme, liquid]
---

# Product Card Title Beautify
{%raw%}{{ card_product.title }}{%endraw%} This will suffice to print out product title in liquid-html. The shopify store I am currently working on has a title format which includes "-" between two different fields. For example
Zebra blen 3c Multicolor Ballpoint Pen 0.5mm
Zebra - blen 3c - Multicolor Ballpoint Pen 0.5mm

Printint this hypen formatted title in a product card layout is a bit ugly depending on linebreaking point.

```liquid
{% raw %}
{% case card_product.type %}
    {% when 'Writing Material' %}
        {% assign splitTitle = card_product.title | split: " - " %}
        {{ splitTitle[0]}}<br />
        {{ splitTitle[1]}}<br />
        {{ splitTitle[2] | truncate: 35 }}
        {{ splitTitle[3] | truncate: 35 }}
{% endcase %}
{% endraw %}
```

This snippets checks if the product type is Writing Material, then splits by " - ". It ignores normal use of hypen, like 'multi-pen' because there's no space before & after a hypen.

![test image](/assets/img/nonformattedTitle.jpg){: w="500" h="500"}
![test image](/assets/img/splitTitle.jpg){: w="500" h="500"}
