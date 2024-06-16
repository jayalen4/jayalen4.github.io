---
layout: default
title: Contacto
description: This is just another page
---

## Contacto

<form
  action="https://formspree.io/f/xgeggdpn"
  method="POST"
>
  <label>
    <input type="name" name="name" placeholder="Nombre *" required style="padding:6px; margin-bottom: 10px; border-radius: 3px; border: 1px solid #bbb;">
  </label><br>
  <label>
    <input type="email" name="email" placeholder="Email *" required style="padding:6px; margin-bottom: 10px; border-radius: 3px; border: 1px solid #bbb;">
  </label><br>
  <label>
    <input type="text" inputmode="numeric" pattern="[0-9]+" minlength="7" name="phone" placeholder="Teléfono *" required style="padding:6px; margin-bottom: 10px; border-radius: 3px; border: 1px solid #bbb;">
  </label><br>
  <label>
    <textarea name="message" placeholder="Su consulta *" required style="padding:6px" style="padding:6px; width:96%; margin-bottom: 10px; border-radius: 3px; border: 1px solid #bbb;" rows="5"></textarea>
  </label><br>
  <!-- your other form fields go here -->
  <button type="submit">¡Enviar!</button>
</form>
