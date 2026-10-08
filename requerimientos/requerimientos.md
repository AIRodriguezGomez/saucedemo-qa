# Requerimientos funcionales

## Login

- RF-01: El sistema debe redirigir a la pantalla de productos cuando se inicia sesión con un usuario y una contraseña válidos.
- RF-02: El sistema debe mostrar el mensaje "Epic sadface: Username is required" si se intenta iniciar sesión con el campo Username vacío y el campo Password completo.
- RF-03: El sistema debe mostrar el mensaje "Epic sadface: Password is required" si se intenta iniciar sesión con el campo Password vacío y el campo Username completo.
- RF-04: El sistema debe mostrar el mensaje "Epic sadface: Username is required" si se intenta iniciar sesión con ambos campos vacíos.
- RF-05: El sistema debe mostrar el mensaje "Epic sadface: Username and password do not match any user in this service" si se intenta iniciar sesión con un usuario válido y una contraseña incorrecta.
- RF-06: El sistema debe mostrar el mensaje "Epic sadface: Username and password do not match any user in this service" si se intenta iniciar sesión con un usuario inexistente y una contraseña válida.
- RF-07: El sistema debe mostrar el mensaje "Epic sadface: Sorry, this user has been locked out." si se intenta iniciar sesión con el usuario `locked_out_user` y su contraseña correcta.
