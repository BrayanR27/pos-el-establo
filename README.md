# POS El Establo

Aplicación táctil de punto de venta para **El Establo Gourmet** (Bogotá, Calle 66 #69I-01), hecha como propuesta para reemplazar/complementar el InterPOS que usan hoy.

## Versión estática para Vercel

El archivo **`index.html`** es la versión estática del POS, lista para desplegar en Vercel: es una sola página que funciona sola, sin servidor ni base de datos. Para publicarla, en Vercel se importa este repositorio y se despliega sin comando de compilación.

Ojo: en esta versión los datos (ventas, mesas, inventario, cierres) se guardan en el navegador del equipo que la usa (localStorage), así que cada equipo lleva sus propios datos. La versión con base de datos sigue viviendo en el entorno de Muse (artefacto `pos-el-establo`).

## Qué hace

- **Vender (Caja):** venta rápida por categorías, cobro en efectivo (con cálculo de vueltas), tarjeta o Nequi. Al cobrar, el stock se descuenta solo.
- **Mesas:** Piso 1 con 7 mesas y Caja. Al tocar una mesa se toma su pedido; cada mesa ocupada muestra en vivo cuánto tiempo lleva desde que pidieron y se marca **Retardado** en rojo si lleva más de 20 minutos sin cobrarse. Al cobrar, la mesa queda libre y la venta pasa a Ventas de hoy.
- **Domicilios y Para recoger:** pedidos con nombre, teléfono y dirección (domicilio). El domicilio suma automático el cobro de $2.000 de la carta. También muestran su tiempo en vivo en la lista de pedidos activos.
- **Inventario:** cuánto queda de cada producto e insumo, alerta de lo que está por acabarse, entradas, mermas, conteos y registro de movimientos.
- **Ventas de hoy:** total vendido, número de ventas, lo más vendido y detalle por venta.
- **Imprimir recibo:** después de cada venta, recibo en formato térmico de 80 mm (productos, total, método de pago, recibido y vueltas). También se puede reimprimir desde Ventas de hoy.
- **Abrir caja:** botón independiente que abre la caja sin imprimir nada, y apertura automática al cobrar en efectivo. Funciona con el impulso ESC/POS que la impresora de recibos le manda al cajón (Web Serial en Chrome): la primera vez, en el computador del local, se enlaza la impresora; la caja debe estar conectada a la impresora por el cable del cajón y la impresora configurada para abrirla.
- **Cierre de turno:** recibo grande tipo informe Z imprimible con ventas totales por Nequi, efectivo y tarjeta, por tipo de pedido, retornos, total neto y efectivo esperado en caja. Una venta cobrada ya no se puede editar ni borrar: solo se le puede hacer un Retorno (total o parcial), que se resta en el cierre.

## La carta

El catálogo completo está en [`data/catalogo.json`](data/catalogo.json): **57 productos vendibles** con los precios reales de la carta (arepas rellenas, perros calientes, patacones, hamburguesas, varios, bebidas, 12 combos con francesas y gaseosa 250 ml, platos especiales y adicionales, incluido el domicilio de $2.000), más 5 insumos que solo se controlan en inventario.

El stock que trae el archivo es el de la demostración y se puede editar desde el POS.

## Sobre este repositorio

La aplicación en vivo corre en el entorno de Muse (artefacto `pos-el-establo`) y es una app con base de datos, así que **este repositorio no contiene el código fuente ejecutable de esa versión**: el código de esa plataforma no se puede exportar a archivos. Lo que se guarda aquí es la versión estática desplegable (`index.html`), la documentación de cómo funciona y el catálogo real con sus precios.

Última actualización: 21 de noviembre de 2026.
