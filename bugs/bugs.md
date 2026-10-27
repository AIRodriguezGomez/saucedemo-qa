# Reporte de bugs: SauceDemo

Defectos encontrados al ejecutar los [casos de prueba](../casos-de-prueba/casos-de-prueba.md) del proyecto. Cada bug se reporta una sola vez, aunque afecte a varios casos o usuarios, y el detalle por usuario está en la tabla de "Usuarios y ejecuciones afectados" de cada sección.

- **Aplicación:** SauceDemo (https://www.saucedemo.com)
- **Tester:** Andrea Isabella Rodriguez Gomez
- **Navegador:** Chrome
- **Fecha de ejecución:** 26/10/2026
- **Total de bugs:** 11 (todos abiertos)
- **Contraseña de todos los usuarios:** `secret_sauce`

**Criterio de severidad:** alta cuando impide completar un flujo o rompe una función principal, media cuando la función se puede usar pero con un resultado incorrecto, y baja para detalles menores.

## Resumen

| ID | Título | Severidad | Usuarios | Casos |
|---|---|---|---|---|
| BUG-01 | Un producto muestra una imagen que no le corresponde | Media | problem_user, visual_user | CP-43, CP-44 |
| BUG-02 | El sistema permite avanzar al checkout con el carrito vacío | Media | standard_user | CP-22 |
| BUG-03 | El ordenamiento no funciona con problem_user | Alta | problem_user | CP-10, CP-11, CP-12 |
| BUG-04 | El ordenamiento muestra un error con error_user | Alta | error_user | CP-10, CP-11, CP-12 |
| BUG-05 | No se puede escribir en el campo Last Name del checkout | Alta | problem_user, error_user | CP-23 |
| BUG-06 | Se avanza al resumen de compra sin Last Name y sin mensaje de error | Media | error_user | CP-26 |
| BUG-07 | El botón "Remove" no funciona desde la pantalla de productos | Media | error_user | CP-16 |
| BUG-08 | El precio del producto es inconsistente entre pantallas | Alta | visual_user | CP-30 |
| BUG-09 | Demora al ordenar los productos | Media | performance_glitch_user | CP-41 |
| BUG-10 | Demora al volver a productos con "Back Home" | Media | performance_glitch_user | CP-42 |
| BUG-11 | Al tocar un producto se abre el detalle de otro producto | Alta | problem_user | CP-13, CP-44 |

---

## BUG-01: Un producto muestra una imagen que no le corresponde

- **Severidad:** Media
- **Estado:** Abierto
- **Requerimiento incumplido:** RF-09 (CP-43) y RF-15 (CP-44)

**Precondiciones:** haber iniciado sesión y estar en la pantalla de productos.

**Pasos para reproducir** (con `visual_user`):

1. Iniciar sesión con `visual_user`.
2. Mirar la imagen de cada producto del listado.

**Resultado esperado:** cada producto muestra la imagen que le corresponde.

**Resultado obtenido:** el producto "Sauce Labs Backpack" muestra la imagen de un perro con una pelota en la boca en lugar de la imagen del producto.

**Usuarios y ejecuciones afectados:**

| Usuario | Caso | Ejecución | Alcance | Evidencia |
|---|---|---|---|---|
| problem_user | CP-43 | EJ-12 | Los 6 productos | evidencia_EJ-12_BUG-01 |
| visual_user | CP-43 | EJ-13 | Solo "Sauce Labs Backpack" | evidencia_EJ-13_BUG-01 |
| problem_user | CP-44 | EJ-30 | "Sauce Labs Backpack". Además el detalle abre otro producto (ver BUG-11) | evidencia_EJ-30_BUG-01 |
| visual_user | CP-44 | EJ-31 | Solo "Sauce Labs Backpack". El detalle muestra la imagen correcta, distinta de la del listado | evidencia_EJ-31_BUG-01 |

---

## BUG-02: El sistema permite avanzar al checkout con el carrito vacío

- **Severidad:** Media
- **Estado:** Abierto
- **Usuario:** standard_user
- **Requerimiento incumplido:** RF-28
- **Detectado en:** CP-22 (EJ-42)
- **Evidencia:** evidencia_EJ-42_BUG-02

**Precondiciones:** haber iniciado sesión y no tener productos agregados en el carrito.

**Pasos para reproducir:**

1. Tocar el ícono del carrito.
2. Tocar el botón "Checkout".

**Resultado esperado:** el sistema no permite avanzar a la pantalla "Checkout: Your Information".

**Resultado obtenido:** el sistema permite avanzar a la pantalla "Checkout: Your Information".

---

## BUG-03: El ordenamiento no funciona con problem_user

- **Severidad:** Alta
- **Estado:** Abierto
- **Requerimiento incumplido:** RF-11, RF-12 y RF-13

**Precondiciones:** haber iniciado sesión con `problem_user` y estar en la pantalla de productos.

**Pasos para reproducir:**

1. Abrir la lista de ordenamiento.
2. Seleccionar "Name (Z to A)".
3. Observar el orden de los productos.

**Resultado esperado:** los productos se muestran ordenados alfabéticamente por título, de la Z a la A.

**Resultado obtenido:** los productos quedan en el mismo orden. No se reordenan.

**Usuarios y ejecuciones afectados:**

| Usuario | Caso | Requerimiento | Ejecución | Opción | Evidencia |
|---|---|---|---|---|---|
| problem_user | CP-10 | RF-11 | EJ-18 | Name (Z to A) | evidencia_EJ-18_BUG-03 |
| problem_user | CP-11 | RF-12 | EJ-21 | Price (low to high) | evidencia_EJ-21_BUG-03 |
| problem_user | CP-12 | RF-13 | EJ-24 | Price (high to low) | evidencia_EJ-24_BUG-03 |

**Observación:** la opción "Name (A to Z)" (CP-09, EJ-15) no se considera falla, porque la lista ya aparece ordenada de A a Z al entrar y la opción no tiene nada que cambiar.

---

## BUG-04: El ordenamiento muestra un error con error_user

- **Severidad:** Alta
- **Estado:** Abierto
- **Requerimiento incumplido:** RF-11, RF-12 y RF-13

**Precondiciones:** haber iniciado sesión con `error_user` y estar en la pantalla de productos.

**Pasos para reproducir:**

1. Abrir la lista de ordenamiento.
2. Seleccionar "Name (Z to A)".
3. Observar la lista y los mensajes en pantalla.

**Resultado esperado:** los productos se muestran ordenados alfabéticamente por título, de la Z a la A.

**Resultado obtenido:** la lista queda en el mismo orden y se muestra el mensaje "Sorting is broken! This error has been reported to Backtrace."

**Usuarios y ejecuciones afectados:**

| Usuario | Caso | Requerimiento | Ejecución | Opción | Evidencia |
|---|---|---|---|---|---|
| error_user | CP-10 | RF-11 | EJ-19 | Name (Z to A) | evidencia_EJ-19_BUG-04 |
| error_user | CP-11 | RF-12 | EJ-22 | Price (low to high) | evidencia_EJ-22_BUG-04 |
| error_user | CP-12 | RF-13 | EJ-25 | Price (high to low) | evidencia_EJ-25_BUG-04 |

**Observación:** con "Name (A to Z)" (CP-09, EJ-16) no se muestra ningún mensaje y no se considera falla, porque la lista ya aparece ordenada de A a Z.

---

## BUG-05: No se puede escribir en el campo Last Name del checkout

- **Severidad:** Alta
- **Estado:** Abierto
- **Requerimiento incumplido:** RF-29
- **Detectado en:** CP-23

**Precondiciones:** haber iniciado sesión, tener un producto en el carrito y estar en la pantalla "Checkout: Your Information".

**Pasos para reproducir** (con `problem_user`):

1. Agregar "Sauce Labs Backpack" al carrito y entrar al carrito.
2. Tocar "Checkout".
3. Escribir `Ana` en First Name.
4. Intentar escribir `Pérez` en Last Name.
5. Escribir `1000` en Zip/Postal Code.

**Resultado esperado:** los tres campos permiten ingresar los datos proporcionados.

**Resultado obtenido:** First Name y Zip/Postal Code permiten escribir. Last Name no permite escribir. Con `problem_user`, al no poder completar el campo, no se puede avanzar al resumen de la compra.

**Usuarios y ejecuciones afectados:**

| Usuario | Caso | Ejecución | Evidencia |
|---|---|---|---|
| problem_user | CP-23 | EJ-44 | evidencia_EJ-44_BUG-05 |
| error_user | CP-23 | EJ-45 | evidencia_EJ-45_BUG-05 |

---

## BUG-06: Se avanza al resumen de compra sin Last Name y sin mensaje de error

- **Severidad:** Media
- **Estado:** Abierto
- **Usuario:** error_user
- **Requerimiento incumplido:** RF-32 y RF-34
- **Detectado en:** CP-26 (EJ-49)
- **Evidencia:** evidencia_EJ-49_BUG-06

**Precondiciones:** haber iniciado sesión con `error_user`, tener un producto en el carrito y estar en la pantalla "Checkout: Your Information".

**Pasos para reproducir:**

1. Escribir `Ana` en First Name.
2. Dejar Last Name vacío.
3. Escribir `1000` en Zip/Postal Code.
4. Tocar "Continue".

**Resultado esperado:** se muestra el mensaje "Error: Last Name is required" y el sistema permanece en la pantalla de datos del comprador.

**Resultado obtenido:** no se muestra el mensaje de error y el sistema permite avanzar a la pantalla "Checkout: Overview".

---

## BUG-07: El botón "Remove" no funciona desde la pantalla de productos

- **Severidad:** Media
- **Estado:** Abierto
- **Usuario:** error_user
- **Requerimiento incumplido:** RF-18, RF-19 y RF-21
- **Detectado en:** CP-16 (EJ-35)
- **Evidencia:** evidencia_EJ-35_BUG-07

**Precondiciones:** haber iniciado sesión con `error_user` y tener únicamente "Sauce Labs Backpack" agregado al carrito.

**Pasos para reproducir:**

1. Estar en la pantalla de productos.
2. Tocar el botón "Remove" de "Sauce Labs Backpack".

**Resultado esperado:** el botón vuelve a "Add to cart", su texto vuelve a mostrarse en negro y el ícono del carrito no muestra ningún número.

**Resultado obtenido:** el botón sigue en "Remove", el texto no vuelve a negro y el ícono del carrito sigue mostrando el número.

**Observación:** según las notas de exploración, desde la pantalla del carrito sí permite quitar el producto.

---

## BUG-08: El precio del producto es inconsistente entre pantallas

- **Severidad:** Alta
- **Estado:** Abierto
- **Usuario:** visual_user
- **Requerimiento incumplido:** RF-37
- **Detectado en:** CP-30 (EJ-54)
- **Evidencia:** evidencia_EJ-54_BUG-08_lista y evidencia_EJ-54_BUG-08_resumen

**Precondiciones:** haber iniciado sesión con `visual_user` y estar en la pantalla de productos.

**Pasos para reproducir:**

1. Registrar el precio de "Sauce Labs Backpack" en la pantalla de productos.
2. Agregar el producto al carrito, entrar al carrito y tocar "Checkout".
3. Completar First Name con `Ana`, Last Name con `Pérez` y Zip/Postal Code con `1000`, y tocar "Continue".
4. Comparar el precio del producto en el resumen con el registrado en el paso 1.

**Resultado esperado:** el precio del producto en el resumen coincide con el registrado en la pantalla de productos.

**Resultado obtenido:** el precio es 3,93 en el listado y 29,99 en el resumen de la compra. Además, el precio del producto cambia al refrescar la página o al moverse entre pantallas.

---

## BUG-09: Demora al ordenar los productos

- **Severidad:** Media
- **Estado:** Abierto
- **Usuario:** performance_glitch_user
- **Requerimiento incumplido:** RNF-01
- **Detectado en:** CP-41 (EJ-66)
- **Evidencia:** evidencia_EJ-66_BUG-09

**Precondiciones:** haber iniciado sesión con `performance_glitch_user` y estar en la pantalla de productos.

**Pasos para reproducir:**

1. Abrir la lista de ordenamiento.
2. Seleccionar "Price (low to high)" y activar el cronómetro.
3. Detener el cronómetro cuando la lista aparece reordenada.

**Resultado esperado:** la lista se muestra reordenada en menos de 2 segundos.

**Resultado obtenido:** la lista se reordena en 4 segundos. Con `standard_user` el mismo paso tarda 0,4 segundos (EJ-65).

**Observación:** el tiempo se midió con cronómetro manual y solo con la opción "Price (low to high)".

---

## BUG-10: Demora al volver a productos con "Back Home"

- **Severidad:** Media
- **Estado:** Abierto
- **Usuario:** performance_glitch_user
- **Requerimiento incumplido:** RNF-02
- **Detectado en:** CP-42 (EJ-68)
- **Evidencia:** evidencia_EJ-68_BUG-10

**Precondiciones:** haber iniciado sesión con `performance_glitch_user` y estar en la pantalla de confirmación de compra.

**Pasos para reproducir:**

1. Completar una compra: agregar un producto, tocar "Checkout", completar los datos del comprador, tocar "Continue" y "Finish".
2. En la pantalla de confirmación, tocar "Back Home" y activar el cronómetro.
3. Detener el cronómetro cuando se muestra la pantalla de productos.

**Resultado esperado:** la pantalla de productos se muestra en menos de 2 segundos.

**Resultado obtenido:** la pantalla de productos se muestra en 5 segundos. Con `standard_user` el mismo paso tarda 0,4 segundos (EJ-67).

---

## BUG-11: Al tocar un producto se abre el detalle de otro producto

- **Severidad:** Alta
- **Estado:** Abierto
- **Usuario:** problem_user
- **Requerimiento incumplido:** RF-14

**Precondiciones:** haber iniciado sesión con `problem_user` y estar en la pantalla de productos.

**Pasos para reproducir:**

1. Tocar el nombre "Sauce Labs Backpack".
2. Observar el producto que se muestra en la página de detalle.

**Resultado esperado:** el sistema redirige a la página de detalle del producto seleccionado ("Sauce Labs Backpack").

**Resultado obtenido:** el sistema abre la página de detalle de otro producto ("Sauce Labs Fleece Jacket").

**Usuarios y ejecuciones afectados:**

| Usuario | Caso | Ejecución | Evidencia |
|---|---|---|---|
| problem_user | CP-13 | EJ-27 | evidencia_EJ-27_BUG-11 |
| problem_user | CP-44 | EJ-30 | evidencia_EJ-30_BUG-11 |
