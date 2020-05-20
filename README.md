# URI Pago Móvil

La siguiente propuesta especifica un URI unificado para el instrumento
financiero Pago Móvil, con el objetivo de hacer la experiencia del usuario
más transparente y permitir mayor velocidad en el procesamiento de pagos.

## Especificación

    pmovil:<código del banco>/<número telefónico>/<número de identificador>?monto=<monto a pagar>&moneda=<moneda a utilizar>&concepto=<concepto del pago>

Ejemplos:

  * `pmovil:0136/04241234567/V12345678?monto=1000&moneda=VES&concepto=Cafe`
  * `pmovil:0105/584121234567/J000000009?monto=5&moneda=USD&concepto=Corte+de+pelo`

## Explicación de la estructura

El URI cuenta con las siguientes partes:

  * **Esquema**: `pmovil`
  * **Ruta**: consta de tres partes separadas por un slash `/`,
    * ***Código bancario***: El código de 4 dígitos del banco recipiente.
    * ***Número telefónico***: Número telefónico del recipiente.
    * ***Identificador***: El identificador con el prefijo adecuado del tipo de
    persona: `V`, `E`, `P`, `J`, `G` o `R`.
  * **Query**: Campos adicionales opcionales que permiten prellenar campos del
  pago, separados por un ampersand `&`, utilizando el esquema
  `<nombre del campo>=<valor>`. Los campos disponibles son:
    * `monto`: el monto a pagar.
    * `moneda`: código ISO de la moneda a usar en el pago. Puede
    ser extendido con los códigos de monedas digitales. Se desarrollará una
    subespecificación para este tipo de códigos.
    * `concepto`: concepto del pago.

El URI debe estar correctamente codificado de acuerdo a la especificación de la
W3C https://www.w3.org/Addressing/URL/uri-spec.html

## Utilización en medios de pago
(Sección no autoritativa, sólo utilizar como sugerencia)

Para presentar un pago al usuario es recomendable que el mismo sea presentado
en versión simple legible, luego como un código QR y debajo un enlace al URI
en cuestión.

Ejemplo:

    // incluir imagen de ejemplo

Estos elementos de la interfaz del usuario permiten lo siguiente:

  * El texto legible simple permite a usuarios de dispositivos tradicionales
  utilizar la información para hacer un pago móvil tradicional.
  * El código QR permite a los usuarios de dispositivos inteligentes escanear
  el código desde su aplicación de pagos preferida para realizar el pago
  rápidamente.
  * El botón o enlace del URI permite que las páginas Web agreguen un botón que
  llame por un ***Uri scheme handler*** a la aplicación preferida de pago móvil
  del usuario, permitiendo un flujo de operación rápido y eficiente.

## Licencia

Licencia MIT.

Ver LICENSE para detalles.
