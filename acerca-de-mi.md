---
layout: default
title: Acerca de mi
description: 
---


<div class="image-cropper">
    <img  class = "rounded">
</div>

Mi nombre es Marco Rios, soy estudiante de ingeniería electrónica, y  me gusta programar. En este pequeño espacio compartiré proyectos que me hayan parecido relevantes e interesantes, para distintas aplicaciones y en distintos lenguajes de programación. 

<body>
    <h3>Contáctese conmigo</h3>
    <form id="fcf-form-id" class="fcf-form-class" method="post" action="email.php">
            <label for="Name" class="fcf-label">Su nombre</label>
            <div class="fcf-input-group">
                <input type="text" id="Name" name="Name" class="fcf-form-control" required>
            </div>
        <div class="fcf-form-group">
            <label for="Email" class="fcf-label">Su e-mail</label>
            <div class="fcf-input-group">
                <input type="email" id="Email" name="Email" class="fcf-form-control" required>
            </div>
        <div class="fcf-form-group">
            <label for="Message" class="fcf-label">Su mensaje</label>
            <div class="fcf-input-group">
                <textarea id="Message" name="Message" class="fcf-form-control" rows="6" maxlength="3000" required></textarea>
            </div>
        </div>
        <div class="fcf-form-group">
            <button type="submit" id="fcf-button" class="fcf-btn fcf-btn-primary fcf-btn-lg fcf-btn-block">Enviar</button>
        </div>
