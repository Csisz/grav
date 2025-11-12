---
title: Családfák, leírások, anyakönyvek
menu: Családfák, leírások, anyakönyvek
process:
  twig: true
---

Itt rendszerezzük a családfákat (PDF/kép), szöveges leírásokat és az anyakönyvi hivatkozásokat.

{% set listPage = page.find(page.route ~ '/csaladfak') %}
{% set children = listPage ? listPage.children.order('folder','asc') : [] %}

{% if children|length %}
### Családfák
<ul>
{% for p in children %}
  <li style="margin-bottom:.4rem">
    <a href="{{ p.url }}">{{ p.title }}</a>
    {% if p.header.pdf %}
      &nbsp;<a class="btn" href="{{ listPage.media[p.header.pdf].url ?? p.media[p.header.pdf].url ?? p.header.pdf }}"
               target="_blank" rel="noopener">PDF</a>
    {% endif %}
  </li>
{% endfor %}
</ul>
{% else %}
Még nincs családfa feltöltve.
{% endif %}

---

### Összes PDF ebben a szekcióban

{# ide az 01-csaladfak/files alatti PDF-ek kerülnek automatikusan #}
{% set pdfs = page.media.files
  |filter(f => f.extension == 'pdf')
  |sort((a,b)=>a.basename < b.basename ? -1 : 1)
%}
{% if pdfs|length %}
{% for f in pdfs %}
- [{{ f.basename }}]({{ f.url }}) ({{ (f.size/1024/1024)|number_format(2) }} MB){target=_blank rel="noopener"}
{% endfor %}
{% else %}
Nincs feltöltött dokumentum.
{% endif %}
