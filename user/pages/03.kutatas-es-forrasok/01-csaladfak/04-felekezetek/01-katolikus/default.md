---
title: Katolikus anyagok
menu: Katolikus
process: { twig: true }
---

{% set pdfs = page.parent.parent.media.files
  |filter(f => f.extension == 'pdf' and ('katolikus' in f.basename|lower))
  |sort((a,b)=>a.basename < b.basename ? -1 : 1) %}

{% if pdfs|length %}
{% for f in pdfs %}
- [{{ f.basename }}]({{ f.url }}) ({{ (f.size/1024/1024)|number_format(2) }} MB){target=_blank rel="noopener"}
{% endfor %}
{% else %}
Nem található „katolikus” jellegű dokumentum.
{% endif %}
