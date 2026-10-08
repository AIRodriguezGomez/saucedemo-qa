# Requerimientos funcionales

## Login

- RF-01: El sistema debe redirigir a la pantalla de productos cuando se inicia sesión con un usuario y una contraseña válidos.
- RF-02: El sistema debe mostrar el mensaje "Epic sadface: Username is required" si se intenta iniciar sesión con el campo Username vacío y el campo Password completo.
- RF-03: El sistema debe mostrar el mensaje "Epic sadface: Password is required" si se intenta iniciar sesión con el campo Password vacío y el campo Username completo.
- RF-04: El sistema debe mostrar el mensaje "Epic sadface: Username is required" si se intenta iniciar sesión con ambos campos vacíos.
- RF-05: El sistema debe mostrar el mensaje "Epic sadface: Username and password do not match any user in this service" si se intenta iniciar sesión con un usuario válido y una contraseña incorrecta.
- RF-06: El sistema debe mostrar el mensaje "Epic sadface: Username and password do not match any user in this service" si se intenta iniciar sesión con un usuario inexistente y una contraseña válida.
- RF-07: El sistema debe mostrar el mensaje "Epic sadface: Sorry, this user has been locked out." si se intenta iniciar sesión con el usuario `locked_out_user` y su contraseña correcta.


  ## Productos

- RF-08: El sistema debe mostrar 6 productos en la pantalla de productos.
- RF-09: El sistema debe mostrar, para cada producto, su imagen correspondiente, título, descripción y precio.
- RF-10: El sistema debe ordenar los productos alfabéticamente por título, de la A a la Z, al seleccionar la opción "Name (A to Z)" en la lista de ordenamiento.
- RF-11: El sistema debe ordenar los productos alfabéticamente por título, de la Z a la A, al seleccionar la opción "Name (Z to A)" en la lista de ordenamiento.
- RF-12: El sistema debe ordenar los productos por precio, de menor a mayor, al seleccionar la opción "Price (low to high)" en la lista de ordenamiento.
- RF-13: El sistema debe ordenar los productos por precio, de mayor a menor, al seleccionar la opción "Price (high to low)" en la lista de ordenamiento.
- RF-14: El sistema debe redirigir a la página de detalle del producto seleccionado al tocar su nombre o su imagen.
- RF-15: La página de detalle debe mostrar la misma imagen y el mismo precio que el producto en la lista de productos.
- RF-16: Al agregar un producto al carrito, el botón del producto debe cambiar de "Add to cart" a "Remove".
- RF-17: Al agregar un producto al carrito, el texto del botón del producto debe mostrarse en rojo.
- RF-18: Al quitar un producto del carrito desde esta pantalla, el botón del producto debe volver a "Add to cart".
- RF-19: Al quitar un producto del carrito desde esta pantalla, el texto del botón del producto debe volver a mostrarse en negro.
- RF-20: El ícono del carrito debe mostrar un número con la cantidad de productos agregados.
- RF-21: El ícono del carrito no debe mostrar ningún número cuando no hay productos en el carrito.
