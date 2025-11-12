---
title: A Nemeskosztolányi családfa
menu: A Nemeskosztolányi családfa
pdf: "5_1CsaladfaNK.pdf"   # ide írd be később a hozzátartozó PDF nevét, pl.: 11_gerogius.pdf
process:
  twig: true
---

**A Nemeskosztolányi családfa**

Itt lehet rövid bevezető vagy magyarázat.  
Ha a fenti `pdf` mező ki van töltve, a Családfák főoldalán megjelenik egy PDF gomb ehhez a tételhez.

{% if page.header.pdf %}
> [Megnyitás PDF-ben]({{ page.parent.parent.media[page.header.pdf].url ?? page.media[page.header.pdf].url ?? page.header.pdf }}){target=_blank rel="noopener"}
{% endif %}
