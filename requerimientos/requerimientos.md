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

## Carrito

- RF-22: Al entrar al carrito con productos agregados, el sistema debe mostrar para cada producto su nombre, precio y cantidad.
- RF-23: Al quitar un producto desde el carrito, el producto debe dejar de mostrarse en la lista del carrito.
- RF-24: Al quitar un producto desde el carrito, el número del ícono del carrito debe disminuir en uno.
- RF-25: El sistema debe mostrar la pantalla del carrito, sin productos, al ingresar al carrito sin haber agregado productos.
- RF-26: El sistema debe redirigir a la pantalla de productos al tocar el botón "Continue Shopping".
- RF-27: El sistema debe redirigir a la pantalla de datos del comprador ("Checkout: Your Information") al tocar el botón "Checkout" con productos en el carrito.
- RF-28: El sistema no debe permitir avanzar al checkout si el carrito no tiene productos.

## Checkout: datos del comprador

- RF-29: Los campos First Name, Last Name y Zip/Postal Code deben permitir ingresar datos.
- RF-30: El sistema debe redirigir a la pantalla de resumen de la compra al completar los tres campos y tocar el botón "Continue".
- RF-31: El sistema debe mostrar el mensaje "Error: First Name is required" si el campo First Name está vacío al tocar "Continue".
- RF-32: El sistema debe mostrar el mensaje "Error: Last Name is required" si el campo Last Name está vacío al tocar "Continue".
- RF-33: El sistema debe mostrar el mensaje "Error: Postal Code is required" si el campo Postal Code está vacío al tocar "Continue".
- RF-34: El sistema debe permanecer en la pantalla de datos del comprador si alguno de los tres campos está vacío al tocar el botón "Continue".
- RF-35: El sistema debe redirigir a la pantalla del carrito al tocar el botón "Cancel".

## Checkout: resumen de la compra

- RF-36: El sistema debe mostrar, para cada producto, su nombre y precio, y los importes Item total, Tax y Total.
- RF-37: El precio de cada producto en el resumen debe coincidir con el de la pantalla de productos.
- RF-38: El sistema debe redirigir a la pantalla de productos al tocar el botón "Cancel".
- RF-39: El sistema debe redirigir a la pantalla de confirmación de compra al tocar el botón "Finish".

## Confirmación de compra

- RF-40: El sistema debe mostrar el mensaje "Thank you for your order! Your order has been dispatched, and will arrive just as fast as the pony can get there!" al finalizar la compra.
- RF-41: El sistema debe redirigir a la pantalla de productos al tocar el botón "Back Home".
- RF-42: El carrito debe quedar vacío después de finalizar una compra.

## Menú lateral

- RF-43: El sistema debe mostrar las opciones All Items, About, Logout y Reset App State al abrir el menú.
- RF-44: El sistema debe redirigir a la página de Sauce Labs al seleccionar "About".
- RF-45: El sistema debe cerrar la sesión del usuario al seleccionar "Logout".
- RF-46: El sistema debe reiniciar el estado de la aplicación al seleccionar "Reset App State".

## Rendimiento (requerimientos no funcionales)

- RNF-01: El sistema debe mostrar la lista de productos reordenada en menos de 2 segundos desde que se selecciona una opción de ordenamiento.
- RNF-02: El sistema debe mostrar la pantalla de productos en menos de 2 segundos al tocar el botón "Back Home".
## Sesión

- RF-47: El sistema no debe permitir volver a la pantalla de productos con el botón "atrás" del navegador después de cerrar sesión, y debe mostrar el mensaje "Epic sadface: You can only access '/inventory.html' when you are logged in."
- RF-48: El sistema no debe permitir acceder a la página de productos sin haber iniciado sesión, y debe mostrar el mensaje "Epic sadface: You can only access '/inventory.html' when you are logged in."
