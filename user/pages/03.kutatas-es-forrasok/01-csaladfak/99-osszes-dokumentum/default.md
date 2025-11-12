---
title: Összes dokumentum
menu: Összes
process: { twig: true }
---

{% set pdfs = page.parent.media.files
  |filter(f => f.extension == 'pdf')
  |sort((a,b)=>a.basename < b.basename ? -1 : 1) %}

{% if pdfs|length %}
{% for f in pdfs %}
- [{{ f.basename }}]({{ f.url }}) ({{ (f.size/1024/1024)|number_format(2) }} MB){target=_blank rel="noopener"}
{% endfor %}
{% else %}
Nincs feltöltött dokumentum.
{% endif %}
