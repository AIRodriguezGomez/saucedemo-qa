# Notas de exploración: SauceDemo

Documento de trabajo del proyecto de QA, elaborado antes de escribir los requerimientos. Recoge lo observado al usar la aplicación, pantalla por pantalla.

- **Aplicación:** SauceDemo (https://www.saucedemo.com)
- **Tester:** Andrea Isabella Rodriguez Gomez
- **Fecha de exploración:** 06/10/2026
- **Navegador:** Chrome
- **Usuario de referencia:** `standard_user` / `secret_sauce`

Salvo que se indique otro usuario, todas las pruebas de las secciones 1 a 8 se hicieron con `standard_user`. Los resultados con los demás usuarios están en la sección 9.

---

## 1. Login

**Elementos de la pantalla:** campo Username, campo Password, botón Login, listado de usuarios de prueba, contraseña de prueba y título "Swag Labs".

| N° | Acción | Resultado obtenido | Mensaje textual |
|---|---|---|---|
| 1 | Usuario y contraseña válidos (`standard_user` / `secret_sauce`) | Login exitoso | N/A |
| 2 | Usuario vacío, contraseña completa | Login fallido | Epic sadface: Username is required |
| 3 | Usuario completo, contraseña vacía | Login fallido | Epic sadface: Password is required |
| 4 | Ambos campos vacíos | Login fallido | Epic sadface: Username is required |
| 5 | `standard_user` con contraseña incorrecta (`123`) | Login fallido | Epic sadface: Username and password do not match any user in this service |
| 6 | `locked_out_user` con contraseña válida | Login fallido | Epic sadface: Sorry, this user has been locked out. |

---

## 2. Productos

**Elementos de la pantalla:** menú hamburguesa (All Items, About, Logout, Reset App State), botón del carrito, lista desplegable de orden, botones "Add to cart" y enlaces a Twitter, Facebook e Instagram.

| N° | Acción | Resultado obtenido | Mensaje textual |
|---|---|---|---|
| 1 | Ver cuántos productos hay y qué datos muestra cada uno | 6 productos en total. Cada uno muestra precio, título, imagen y una breve descripción | N/A |
| 2 | Ordenar de A a Z | Ordenamiento exitoso | N/A |
| 3 | Ordenar de Z a A | Ordenamiento exitoso | N/A |
| 4 | Ordenar por precio, de menor a mayor | Ordenamiento exitoso | N/A |
| 5 | Ordenar por precio, de mayor a menor | Ordenamiento exitoso | N/A |
| 6 | Tocar el nombre o la foto de un producto | Redirige a la página de detalle del producto seleccionado | N/A |
| 7 | Agregar un producto al carrito | El botón "Add to cart" cambia a "Remove" y su texto pasa de negro a rojo. En el ícono del carrito aparece un número con la cantidad de productos agregados | N/A |
| 8 | Quitar el producto desde esta misma pantalla | El botón "Remove" vuelve a "Add to cart" y su texto pasa de rojo a negro | N/A |

---

## 3. Carrito

**Elementos de la pantalla:** textos "Your Cart", "QTY" y "Description", botón del carrito, botón "Checkout" y botón "Continue Shopping".

| N° | Acción | Resultado obtenido | Mensaje textual |
|---|---|---|---|
| 1 | Entrar al carrito con productos agregados | Muestra nombre, precio y cantidad de cada producto | N/A |
| 2 | Quitar un producto desde el carrito | El ícono del carrito muestra un número en un círculo rojo con la cantidad de productos. Al quitar el único producto, el ícono queda sin número | N/A |
| 3 | Entrar al carrito vacío | Permite acceder al carrito sin productos | N/A |
| 4 | Botón Continue Shopping | Redirige a la pantalla principal de productos para seguir comprando | N/A |
| 5 | Botón Checkout con el carrito vacío | Permite avanzar con la compra | N/A |

**Observaciones:**

- No permite modificar la cantidad de cada producto.
- Permite avanzar con la compra sin tener productos en el carrito.

---

## 4. Checkout: datos del comprador

**Elementos de la pantalla:** título "Checkout: Your Information", campos First Name, Last Name y Zip/Postal Code, botones Cancel y Continue, ícono del carrito y menú hamburguesa.

| N° | Acción | Resultado obtenido | Mensaje textual |
|---|---|---|---|
| 1 | Completar todos los campos y continuar | Permite pasar a la pantalla de resumen de la compra | N/A |
| 2 | Dejar vacío First Name | No permite continuar | Error: First Name is required |
| 3 | Dejar vacío Last Name | No permite continuar | Error: Last Name is required |
| 4 | Dejar vacío Postal Code | No permite continuar | Error: Postal Code is required |
| 5 | Botón Cancel | Vuelve a la pantalla del carrito | N/A |

---

## 5. Checkout: resumen de la compra

**Elementos de la pantalla:** Payment Information, Shipping Information, Price Total, Item total, Tax, Total, botón Cancel y botón Finish.

| N° | Acción | Resultado obtenido | Mensaje textual |
|---|---|---|---|
| 1 | Revisar productos, precios, impuesto y total | Muestra los productos con su precio y los importes Item total, Tax y Total | N/A |
| 2 | Comparar los precios con los de la pantalla de productos | Los precios coinciden | N/A |
| 3 | Botón Cancel | Vuelve a la pantalla de productos | N/A |
| 4 | Botón Finish | Finaliza la compra | Thank you for your order! Your order has been dispatched, and will arrive just as fast as the pony can get there! |

**Observaciones:**

- Permite finalizar una compra sin productos agregados.

---

## 6. Confirmación de compra

**Elementos de la pantalla:** título "Checkout: Complete!" y botón Back Home.

| N° | Acción | Resultado obtenido | Mensaje textual |
|---|---|---|---|
| 1 | Ver el mensaje que aparece al finalizar | Muestra la pantalla de confirmación con el mensaje de agradecimiento | Thank you for your order! Your order has been dispatched, and will arrive just as fast as the pony can get there! |
| 2 | Botón Back Home | Vuelve a productos y el carrito queda vacío | N/A |

---

## 7. Menú lateral

**Opciones del menú:** All Items, About, Logout y Reset App State.

| N° | Acción | Resultado obtenido | Mensaje textual |
|---|---|---|---|
| 1 | Abrir el menú y listar las opciones | All Items, About, Logout, Reset App State | N/A |
| 2 | All Items | No realiza ninguna acción visible | N/A |
| 3 | About | Redirige a la página de Sauce Labs | N/A |
| 4 | Logout | Cierra la sesión | N/A |
| 5 | Reset App State | Reinicia el estado de la aplicación (por ejemplo, vacía el carrito) | N/A |

---

## 8. Sesión

| N° | Acción | Resultado obtenido | Mensaje textual |
|---|---|---|---|
| 1 | Cerrar sesión y volver atrás con el botón del navegador | No permite volver a la pantalla anterior | Epic sadface: You can only access '/inventory.html' when you are logged in. |
| 2 | Abrir la página de productos sin haber iniciado sesión | No permite ingresar sin haber iniciado sesión | Epic sadface: You can only access '/inventory.html' when you are logged in. |

---

## 9. Otros usuarios de prueba

### `locked_out_user`

- **Login:** no permite iniciar sesión. Mensaje: "Epic sadface: Sorry, this user has been locked out."

### `problem_user`

- **Login:** permite iniciar sesión.
- **Productos:**
  - En la lista de productos muestra la imagen de un perro con una pelota en la boca en lugar de la imagen descriptiva del producto, con un precio distinto del real. Sin requerimientos definidos, falta determinar si es un error o un comportamiento intencional.
  - Al tocar un producto, la página de detalle muestra la foto que corresponde y el precio cambia respecto del de la lista.
  - Ordenar de A a Z: no ordena los productos.
  - Ordenar de Z a A: no ordena los productos.
  - Ordenar por precio de menor a mayor: no ordena.
  - Ordenar por precio de mayor a menor: no ordena.
  - El precio de la pantalla de productos no coincide con el precio al agregar el producto al carrito. En el carrito sí se muestra la imagen que corresponde al producto.
- **Checkout:** en la pantalla "Your Information" no permite escribir en el campo Last Name. Al no poder completarlo, no se puede avanzar a la pantalla de resumen. Mensaje: "Error: Last Name is required".

### `performance_glitch_user`

- **Login:** permite iniciar sesión.
- **Productos:** presenta demora (efecto tardío) al ordenar los productos (A-Z, Z-A, menor a mayor y mayor a menor) y al tocar "Back Home" después de concretar una compra. Toda la página tarda en cargar.

### `error_user`

- **Login:** permite iniciar sesión.
- **Productos:** al ordenar con Z-A, menor a mayor y mayor a menor, muestra el mensaje "Sorting is broken! This error has been reported to Backtrace."
- **Carrito:** solo deja agregar 3 productos. Con esos 3 agregados desde la pantalla de productos, el botón "Remove" no los quita. Desde la pantalla del carrito sí permite quitarlos.
- **Checkout:** permite escribir números en First Name. No permite escribir en Last Name (ni números ni letras), pero sí permite avanzar a la pantalla de resumen sin ese dato y no muestra ningún mensaje de error.

### `visual_user`

- **Login:** permite iniciar sesión.
- **Productos:**
  - De los 6 productos, 5 muestran su imagen correspondiente y 1 muestra la imagen del perro con la pelota.
  - Los precios de la lista no coinciden con los de la página de detalle del producto (por ejemplo, 5 dólares en la lista y 20 dólares en el detalle).
- **Carrito:** los precios del carrito no coinciden con los de la pantalla de productos. Al completar la compra vuelve a mostrarse el precio de la pantalla de productos.
  - El botón Checkout aparece en la esquina superior derecha y el ícono del carrito aparece en medio de una línea de separación.
