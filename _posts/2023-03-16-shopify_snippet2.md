---
title: Shopify Snippet - Filtering method from collection loop
date: 2023-03-16
author: Brandon Baek
categories: [Blogging]
tags: [Shopify, Snippet]
---
Iterate through 'all' collection products and only pick first 3 that has .png image file.

```
{% assign count = 0 %}
{% for product in collections['all'].products %}
  {% if count == 3 %}
    {% break %}
  {% endif %}
  {% if product.featured_image.src contains ".png" %}
    <p>{{ product.title }}</p>
    <!-- Do whatever you want with the product information here -->
    {% assign count = count | plus: 1 %}
  {% endif %}
{% endfor %}
```


