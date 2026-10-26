# Casos de prueba: SauceDemo

Casos de prueba derivados de los [requerimientos](../requerimientos/requerimientos.md) del proyecto. Cada caso indica en la columna **Cubre** el requerimiento que verifica, y el **resultado esperado** sale del requerimiento, no del comportamiento observado en la aplicación.

- **Total de casos:** 42
- **Tipo:** 30 positivos y 12 negativos
- **Prioridad:** 5 alta, 29 media y 8 baja
- **Cobertura:** los 50 requerimientos (RF-01 a RF-48 y RNF-01 y RNF-02) tienen al menos un caso (ver [trazabilidad](#trazabilidad-requerimiento-caso))
- **Usuario de prueba:** salvo que el caso indique otro, se ejecuta con `standard_user`. El resultado con cada usuario se registra en la ejecución.

**Criterio de prioridad:** alta para el recorrido de compra (login válido, agregar al carrito, checkout y finalizar), media para validaciones, mensajes, ordenamientos y rendimiento del ordenamiento, y baja para detalles secundarios, como los botones de navegación y el rendimiento de "Back Home".

---

## 1. Login

| ID | Cubre | Título | Precondición | Pasos | Datos de prueba | Resultado esperado | Tipo | Prioridad |
|---|---|---|---|---|---|---|---|---|
| CP-01 | RF-01 | Iniciar sesión con credenciales válidas | Estar en la pantalla de login (https://www.saucedemo.com/) | 1. Escribir el usuario en Username<br>2. Escribir la contraseña en Password<br>3. Tocar "Login" | Username: standard_user<br>Password: secret_sauce | El sistema redirige a la pantalla de productos | Positivo | Alta |
| CP-02 | RF-02 | Intentar iniciar sesión con Username vacío | Estar en la pantalla de login (https://www.saucedemo.com/) | 1. Dejar Username vacío<br>2. Escribir la contraseña en Password<br>3. Tocar "Login" | Username: vacío<br>Password: secret_sauce | Se muestra el mensaje "Epic sadface: Username is required" | Negativo | Media |
| CP-03 | RF-03 | Intentar iniciar sesión con Password vacío | Estar en la pantalla de login (https://www.saucedemo.com/) | 1. Escribir el usuario en Username<br>2. Dejar Password vacío<br>3. Tocar "Login" | Username: standard_user<br>Password: vacío | Se muestra el mensaje "Epic sadface: Password is required" | Negativo | Media |
| CP-04 | RF-04 | Intentar iniciar sesión con los campos Username y Password vacíos | Estar en la pantalla de login (https://www.saucedemo.com/) | 1. Dejar Username vacío<br>2. Dejar Password vacío<br>3. Tocar "Login" | Username: vacío<br>Password: vacío | Se muestra el mensaje "Epic sadface: Username is required" | Negativo | Media |
| CP-05 | RF-05 | Intentar iniciar sesión con usuario válido y contraseña incorrecta | Estar en la pantalla de login (https://www.saucedemo.com/) | 1. Escribir el usuario en Username<br>2. Escribir la contraseña en Password<br>3. Tocar "Login" | Username: standard_user<br>Password: 123 | Se muestra el mensaje "Epic sadface: Username and password do not match any user in this service" | Negativo | Media |
| CP-06 | RF-06 | Intentar iniciar sesión con usuario inexistente y contraseña válida | Estar en la pantalla de login (https://www.saucedemo.com/) | 1. Escribir el usuario en Username<br>2. Escribir la contraseña en Password<br>3. Tocar "Login" | Username: usuario_falso<br>Password: secret_sauce | Se muestra el mensaje "Epic sadface: Username and password do not match any user in this service" | Negativo | Media |
| CP-07 | RF-07 | Intentar iniciar sesión con usuario bloqueado y contraseña correcta | Estar en la pantalla de login (https://www.saucedemo.com/) | 1. Escribir el usuario en Username<br>2. Escribir la contraseña en Password<br>3. Tocar "Login" | Username: locked_out_user<br>Password: secret_sauce | Se muestra el mensaje "Epic sadface: Sorry, this user has been locked out." | Negativo | Media |

## 2. Productos

| ID | Cubre | Título | Precondición | Pasos | Datos de prueba | Resultado esperado | Tipo | Prioridad |
|---|---|---|---|---|---|---|---|---|
| CP-08 | RF-08, RF-09 | Verificar la cantidad y los datos de los productos del listado | Haber iniciado sesión y estar en la pantalla de productos | 1. Contar los productos del listado<br>2. Revisar los datos que muestra cada producto | N/A | RF-08: Se muestran 6 productos en el listado<br>RF-09: Cada producto muestra la imagen que corresponde a ese producto, su título, su descripción y su precio | Positivo | Media |
| CP-09 | RF-10 | Ordenar los productos de la A a la Z | Haber iniciado sesión y estar en la pantalla de productos | 1. Abrir la lista de ordenamiento<br>2. Seleccionar "Name (A to Z)" | Opción: Name (A to Z) | Se muestran los productos ordenados alfabéticamente por título, de la A a la Z | Positivo | Media |
| CP-10 | RF-11 | Ordenar los productos de la Z a la A | Haber iniciado sesión y estar en la pantalla de productos | 1. Abrir la lista de ordenamiento<br>2. Seleccionar "Name (Z to A)" | Opción: Name (Z to A) | Se muestran los productos ordenados alfabéticamente por título, de la Z a la A | Positivo | Media |
| CP-11 | RF-12 | Ordenar los productos por precio, de menor a mayor | Haber iniciado sesión y estar en la pantalla de productos | 1. Abrir la lista de ordenamiento<br>2. Seleccionar "Price (low to high)" | Opción: Price (low to high) | Se muestran los productos ordenados por precio, de menor a mayor | Positivo | Media |
| CP-12 | RF-13 | Ordenar los productos por precio, de mayor a menor | Haber iniciado sesión y estar en la pantalla de productos | 1. Abrir la lista de ordenamiento<br>2. Seleccionar "Price (high to low)" | Opción: Price (high to low) | Se muestran los productos ordenados por precio, de mayor a menor | Positivo | Media |
| CP-13 | RF-14, RF-15 | Ver detalle del producto al tocar su nombre | Haber iniciado sesión y estar en la pantalla de productos | 1. Registrar la imagen y el precio del producto indicado<br>2. Tocar el nombre del producto indicado. | Producto: Sauce Labs Backpack | RF-14: El sistema redirige a la página de detalle del producto seleccionado.<br>RF-15: La página de detalle muestra la misma imagen y el mismo precio registrados en el listado. | Positivo | Media |
| CP-14 | RF-14 | Ver detalle del producto al tocar su imagen | Haber iniciado sesión y estar en la pantalla de productos | 1. Tocar la imagen del producto indicado. | Producto: Sauce Labs Backpack | El sistema redirige a la página de detalle del producto seleccionado | Positivo | Media |
| CP-15 | RF-16, RF-17, RF-20 | Agregar un producto al carrito desde la pantalla de productos | Haber iniciado sesión, estar en la pantalla de productos y tener el carrito vacío. | 1. Tocar el botón "Add to cart" del producto indicado. | Producto: Sauce Labs Backpack | RF-16: El botón cambia de "Add to cart" a "Remove".<br>RF-17: El texto del botón se muestra en color rojo.<br>RF-20: El ícono del carrito muestra el número 1. | Positivo | Alta |
| CP-16 | RF-18, RF-19, RF-21 | Quitar un producto del carrito desde la pantalla de productos | Haber iniciado sesión, estar en la pantalla de productos y tener únicamente el producto indicado agregado al carrito. | 1. Tocar el botón "Remove" del producto indicado. | Producto: Sauce Labs Backpack | RF-18: El botón cambia de "Remove" a "Add to cart".<br>RF-19: El texto del botón se muestra en color negro.<br>RF-21: El ícono del carrito no muestra ningún número. | Positivo | Media |

## 3. Carrito

| ID | Cubre | Título | Precondición | Pasos | Datos de prueba | Resultado esperado | Tipo | Prioridad |
|---|---|---|---|---|---|---|---|---|
| CP-17 | RF-22 | Ver el contenido del carrito con un producto agregado | Haber iniciado sesión, estar en la pantalla de productos y tener únicamente el producto indicado agregado al carrito. | 1. Tocar el ícono del carrito<br>2. Revisar los datos del producto en el carrito | Producto: Sauce Labs Backpack | Se visualiza el producto con su correspondiente nombre, precio y cantidad | Positivo | Media |
| CP-18 | RF-23, RF-24 | Quitar un producto desde el carrito | Haber iniciado sesión, estar en la pantalla de carrito y tener agregados los dos productos indicados | 1. Tocar el botón "Remove" del primer producto indicado<br>2. Observar la lista del carrito y el ícono del carrito | Producto1: Sauce Labs Backpack<br>Producto2: Sauce Labs Bolt T-Shirt | RF-23: El producto eliminado deja de mostrarse en la lista del carrito<br>RF-24: El número del ícono del carrito baja de 2 a 1 | Positivo | Media |
| CP-19 | RF-25 | Ingresar al carrito sin productos agregados | Haber iniciado sesión, estar en la pantalla de productos y no tener productos agregados en el carrito. | 1. Tocar el ícono del carrito | N/A | Se muestra la pantalla del carrito, sin productos | Positivo | Baja |
| CP-20 | RF-26 | Volver a la pantalla de productos desde el carrito | Haber iniciado sesión y estar en la pantalla de carrito | 1. Tocar el botón "Continue Shopping" | N/A | El sistema redirige a la pantalla de productos | Positivo | Baja |
| CP-21 | RF-27 | Ingresar a la página de checkout | Haber iniciado sesión, estar en la pantalla de carrito y tener únicamente el producto indicado agregado al carrito | 1. Tocar el botón "Checkout" | Producto: Sauce Labs Backpack | El sistema redirige a la página "Checkout: Your Information" | Positivo | Alta |
| CP-22 | RF-28 | Intentar avanzar a la página de checkout sin productos agregados en el carrito | Haber iniciado sesión, estar en la pantalla de carrito y no tener productos agregados en el carrito. | 1. Tocar el botón "Checkout" | N/A | El sistema no permite avanzar a la pantalla "Checkout: Your Information" | Negativo | Media |

## 4. Checkout: datos del comprador

| ID | Cubre | Título | Precondición | Pasos | Datos de prueba | Resultado esperado | Tipo | Prioridad |
|---|---|---|---|---|---|---|---|---|
| CP-23 | RF-29 | Ingresar datos en los campos del comprador | Haber iniciado sesión, tener un producto en el carrito y estar en la pantalla "Checkout: Your Information". | 1. Ingresar un nombre en First Name.<br>2. Ingresar un apellido en Last Name.<br>3. Ingresar un código postal en Zip/Postal Code. | First Name: Ana<br>Last Name: Pérez<br>Zip/Postal Code: 1000 | Los tres campos permiten ingresar los datos proporcionados. | Positivo | Media |
| CP-24 | RF-30 | Continuar al resumen de la compra con los campos completos | Haber iniciado sesión, tener un producto en el carrito y estar en la pantalla "Checkout: Your Information". | 1. Completar los tres campos obligatorios.<br>2. Tocar el botón "Continue". | First Name: Ana<br>Last Name: Pérez<br>Zip/Postal Code: 1000 | El sistema redirige a la pantalla de resumen de la compra. | Positivo | Alta |
| CP-25 | RF-31, RF-34 | Intentar continuar con First Name vacío | Haber iniciado sesión, tener un producto en el carrito y estar en la pantalla "Checkout: Your Information". | 1. Dejar vacío First Name.<br>2. Completar Last Name y Zip/Postal Code.<br>3. Tocar "Continue". | First Name: vacío<br>Last Name: Pérez<br>Zip/Postal Code: 1000 | RF-31: El sistema muestra el mensaje "Error: First Name is required".<br>RF-34: El sistema permanece en la pantalla de datos del comprador. | Negativo | Media |
| CP-26 | RF-32, RF-34 | Intentar continuar con Last Name vacío | Haber iniciado sesión, tener un producto en el carrito y estar en la pantalla "Checkout: Your Information". | 1. Completar First Name.<br>2. Dejar vacío Last Name.<br>3. Completar Zip/Postal Code.<br>4. Tocar "Continue". | First Name: Ana<br>Last Name: vacío<br>Zip/Postal Code: 1000 | RF-32: El sistema muestra el mensaje "Error: Last Name is required".<br>RF-34: El sistema permanece en la pantalla de datos del comprador. | Negativo | Media |
| CP-27 | RF-33, RF-34 | Intentar continuar con Postal Code vacío | Haber iniciado sesión, tener un producto en el carrito y estar en la pantalla "Checkout: Your Information". | 1. Completar First Name y Last Name.<br>2. Dejar vacío Zip/Postal Code.<br>3. Tocar "Continue". | First Name: Ana<br>Last Name: Pérez<br>Zip/Postal Code: vacío | RF-33: El sistema muestra el mensaje "Error: Postal Code is required".<br>RF-34: El sistema permanece en la pantalla de datos del comprador. | Negativo | Media |
| CP-28 | RF-35 | Cancelar el checkout desde los datos del comprador | Haber iniciado sesión y estar en la pantalla "Checkout: Your Information". | 1. Tocar el botón "Cancel". | N/A | El sistema redirige a la pantalla del carrito. | Positivo | Baja |

## 5. Checkout: resumen de la compra

| ID | Cubre | Título | Precondición | Pasos | Datos de prueba | Resultado esperado | Tipo | Prioridad |
|---|---|---|---|---|---|---|---|---|
| CP-29 | RF-36 | Visualizar los productos y los importes del resumen de compra | Haber iniciado sesión, tener un producto en el carrito y haber completado los datos del comprador para llegar al resumen de la compra. | 1. Revisar los datos de los productos y los importes del resumen. | Producto: Sauce Labs Backpack | El sistema muestra, para cada producto, su nombre y precio, y muestra los importes Item total, Tax y Total. | Positivo | Media |
| CP-30 | RF-37 | Verificar que el precio del producto coincida con el de la pantalla de productos | Haber iniciado sesión y estar en la pantalla de productos. | 1. Registrar el precio del producto indicado.<br>2. Agregar ese producto al carrito.<br>3. Entrar al carrito y tocar "Checkout".<br>4. Completar los datos del comprador y tocar "Continue".<br>5. Comparar el precio del producto en el resumen con el registrado en la pantalla de productos. | Producto: Sauce Labs Backpack.<br>Datos del comprador: First Name: Ana<br>Last Name: Pérez<br>Zip/Postal Code: 1000 | El precio del producto en el resumen coincide con el precio registrado en la pantalla de productos. | Positivo | Media |
| CP-31 | RF-38 | Cancelar desde el resumen de la compra | Haber iniciado sesión, tener un producto en el carrito y estar en la pantalla de resumen de la compra. | 1. Tocar el botón "Cancel". | N/A | El sistema redirige a la pantalla de productos. | Positivo | Baja |
| CP-32 | RF-39, RF-40 | Finalizar la compra desde el resumen | Haber iniciado sesión, tener un producto en el carrito, haber completado los datos del comprador y estar en la pantalla de resumen de la compra. | 1. Tocar el botón "Finish". | Producto: Sauce Labs Backpack | RF-39: El sistema redirige a la pantalla de confirmación de compra.<br>RF-40: El sistema muestra el mensaje "Thank you for your order! Your order has been dispatched, and will arrive just as fast as the pony can get there!". | Positivo | Alta |

## 6. Confirmación de compra

| ID | Cubre | Título | Precondición | Pasos | Datos de prueba | Resultado esperado | Tipo | Prioridad |
|---|---|---|---|---|---|---|---|---|
| CP-33 | RF-41 | Volver a la pantalla de productos desde la confirmación de compra | Haber iniciado sesión y estar en la pantalla de confirmación de compra | 1. Tocar "Back Home" | N/A | El sistema redirige a la pantalla de productos | Positivo | Baja |
| CP-34 | RF-42 | Verificar que el carrito quede vacío después de finalizar la compra | Haber iniciado sesión, tener un producto en el carrito y llegar a la pantalla de resumen de la compra. | 1. Tocar "Finish".<br>2. Observar el ícono del carrito | Producto: Sauce Labs Backpack<br>First Name: Ana<br>Last Name: Pérez<br>Zip/Postal Code: 1000 | El carrito queda vacío después de finalizar la compra. | Positivo | Media |

## 7. Menú lateral

| ID | Cubre | Título | Precondición | Pasos | Datos de prueba | Resultado esperado | Tipo | Prioridad |
|---|---|---|---|---|---|---|---|---|
| CP-35 | RF-43 | Visualizar las opciones del menú lateral | Haber iniciado sesión y estar en la pantalla de productos. | 1. Abrir el menú lateral.<br>2. Revisar las opciones disponibles. | N/A | El menú muestra las opciones "All Items", "About", "Logout" y "Reset App State". | Positivo | Baja |
| CP-36 | RF-44 | Acceder a Sauce Labs desde la opción About | Haber iniciado sesión y estar en la pantalla de productos | 1. Abrir el menú lateral<br>2. Seleccionar "About" | N/A | El sistema redirige a la página de Sauce Labs. | Positivo | Baja |
| CP-37 | RF-45 | Cerrar la sesión desde el menú lateral | Haber iniciado sesión y estar en la pantalla de productos | 1. Abrir el menú lateral<br>2. Seleccionar "Logout" | Username: standard_user | El sistema cierra la sesión del usuario. | Positivo | Media |
| CP-38 | RF-46 | Reiniciar el estado de la aplicación desde el menú lateral | Haber iniciado sesión, estar en la pantalla de productos y tener un producto agregado al carrito. | 1. Abrir el menú lateral.<br>2. Seleccionar "Reset App State".<br>3. Tocar el ícono del carrito. | Producto: Sauce Labs Backpack | El sistema reinicia el estado de la aplicación y el carrito queda vacío. | Positivo | Media |

## 8. Sesión

| ID | Cubre | Título | Precondición | Pasos | Datos de prueba | Resultado esperado | Tipo | Prioridad |
|---|---|---|---|---|---|---|---|---|
| CP-39 | RF-47 | Intentar volver a productos con el botón atrás después de cerrar sesión | Haber iniciado sesión y estar en la pantalla de productos | 1. Abrir el menú lateral.<br>2. Seleccionar "Logout".<br>3. Utilizar el botón atrás del navegador | Username: standard_user | El sistema no permite volver a la pantalla de productos y muestra el mensaje "Epic sadface: You can only access '/inventory.html' when you are logged in.". | Negativo | Media |
| CP-40 | RF-48 | Intentar acceder a productos sin iniciar sesión | No haber iniciado sesión. | 1. Ingresar directamente a la URL de la pantalla de productos. | URL: https://www.saucedemo.com/inventory.html | El sistema no permite acceder a la pantalla de productos y muestra el mensaje "Epic sadface: You can only access '/inventory.html' when you are logged in.". | Negativo | Media |

## 9. Rendimiento

| ID | Cubre | Título | Precondición | Pasos | Datos de prueba | Resultado esperado | Tipo | Prioridad |
|---|---|---|---|---|---|---|---|---|
| CP-41 | RNF-01 | Ordenar los productos y medir el tiempo de respuesta | Haber iniciado sesión y estar en la pantalla de productos | 1. Abrir la lista de ordenamiento<br>2. Seleccionar "Price (low to high)" y activar el cronómetro<br>3. Detener el cronómetro cuando la lista aparece reordenada | Opción: Price (low to high) | La lista se muestra reordenada en menos de 2 segundos | Positivo | Media |
| CP-42 | RNF-02 | Volver a productos desde la confirmación de compra y medir el tiempo de respuesta | Haber iniciado sesión y estar en la pantalla de confirmación de compra | 1. Tocar "Back Home" y activar el cronómetro<br>2. Detener el cronómetro cuando se muestra la pantalla de productos | N/A | La pantalla de productos se muestra en menos de 2 segundos | Positivo | Baja |
---

## Trazabilidad: requerimiento a caso

| Requerimiento | Casos que lo cubren |
|---|---|
| RF-01 | CP-01 |
| RF-02 | CP-02 |
| RF-03 | CP-03 |
| RF-04 | CP-04 |
| RF-05 | CP-05 |
| RF-06 | CP-06 |
| RF-07 | CP-07 |
| RF-08 | CP-08 |
| RF-09 | CP-08 |
| RF-10 | CP-09 |
| RF-11 | CP-10 |
| RF-12 | CP-11 |
| RF-13 | CP-12 |
| RF-14 | CP-13, CP-14 |
| RF-15 | CP-13 |
| RF-16 | CP-15 |
| RF-17 | CP-15 |
| RF-18 | CP-16 |
| RF-19 | CP-16 |
| RF-20 | CP-15 |
| RF-21 | CP-16 |
| RF-22 | CP-17 |
| RF-23 | CP-18 |
| RF-24 | CP-18 |
| RF-25 | CP-19 |
| RF-26 | CP-20 |
| RF-27 | CP-21 |
| RF-28 | CP-22 |
| RF-29 | CP-23 |
| RF-30 | CP-24 |
| RF-31 | CP-25 |
| RF-32 | CP-26 |
| RF-33 | CP-27 |
| RF-34 | CP-25, CP-26, CP-27 |
| RF-35 | CP-28 |
| RF-36 | CP-29 |
| RF-37 | CP-30 |
| RF-38 | CP-31 |
| RF-39 | CP-32 |
| RF-40 | CP-32 |
| RF-41 | CP-33 |
| RF-42 | CP-34 |
| RF-43 | CP-35 |
| RF-44 | CP-36 |
| RF-45 | CP-37 |
| RF-46 | CP-38 |
| RF-47 | CP-39 |
| RF-48 | CP-40 |
| RNF-01 | CP-41 |
| RNF-02 | CP-42 |
