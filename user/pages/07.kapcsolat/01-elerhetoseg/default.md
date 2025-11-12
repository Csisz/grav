---
title: Elérhetőség
menu: Elérhetőség
visible: true
form:
  name: contact
  fields:
    - name: name
      label: Név
      type: text
      validate: { required: true }
    - name: email
      label: E-mail
      type: email
      validate: { required: true, rule: email }
    - name: message
      label: Üzenet
      type: textarea
      validate: { required: true }
  buttons:
    - type: submit
      value: Küldés
  process:
    - email:
        from: "{{ form.value.email }}"
        to: you@example.com
        subject: "Üzenet a családi honlapról"
    - message: "Köszönjük az üzenetet!"
---
## Elérhetőség

Az alábbi űrlapon keresztül üzenet küldhető a szerkesztőknek.
