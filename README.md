# Conversor de Monedas — README

## Descripción
Proyecto pequeño en Python que convierte un monto ingresado por el usuario desde una moneda de origen (JPY, USD, GBP, EUR, BRL, COP) hacia cuatro monedas de destino fijas: **JPY**, **USD**, **GBP** y **COP**. El objetivo es demostrar una lógica robusta de conversión usando un diccionario de tasas y una moneda base para minimizar errores en conversiones indirectas.

## Objetivo y planteamiento
- **Objetivo principal**: permitir que un usuario ingrese un monto y una moneda de origen para obtener los valores equivalentes en JPY, USD, GBP y COP.
- **Planteamiento**: normalizar todas las conversiones a una moneda base (USD). El flujo es:
  1. Convertir el monto de la moneda de origen a USD usando factores predefinidos.
  2. Convertir desde USD a cada moneda destino usando los factores inversos apropiados.
- Ventaja: con una base común no es necesario mantener tasas directas para cada par de monedas, lo que reduce complejidad y riesgo de inconsistencias.

## Tasas de referencia
El programa utiliza un diccionario con factores que indican cuántos USD vale 1 unidad de cada moneda (o la inversa cuando se proporciona la relación en sentido contrario). Estas tasas se derivaron de las relaciones proporcionadas en el enunciado y se usan internamente como fuente única para las conversiones.

Ejemplo de relaciones relevantes usadas para construir los factores:
- 1 JPY = 0.01020 USD
- 1 EUR = 1.34265 USD
- 1 GBP = 1.56726 USD
- 1 COP = 0.00052 USD
- 1 BRL = 1 / 63.24728 USD

Estas entradas se almacenan en el diccionario interno para normalizar a USD y luego calcular los destinos.

## Uso
1. Clonar o descargar el script (por ejemplo, `conversor_monedas.py`).
2. Ejecutar en consola:
   - python conversor_monedas.py
3. El script solicita:
   - Monto a convertir (acepta decimales).
   - Código de moneda de origen (uno de: JPY, USD, GBP, EUR, BRL, COP).
4. Resultado: imprime el monto inicial y los cuatro montos convertidos en JPY, USD, GBP y COP, formateados con dos decimales.

Ejemplo interactivo:
- Entrada:
  - Monto: 1000
  - Moneda de origen: EUR
- Salida esperada (ejemplo ilustrativo):
  - Monto inicial: 1,000.00 EUR
  - JPY: 130,442.25 JPY
  - USD: 1,342.65 USD
  - GBP: 856.52 GBP
  - COP: 583,620.62 COP

## Estructura del código
- Diccionario de tasas: almacena la relación respecto a USD para cada moneda soportada.
- Función principal de conversión: recibir monto y moneda de origen, normalizar a USD y convertir a cada moneda destino.
- Módulo de interacción: entrada por consola, validación básica de monto y moneda, presentación de resultados.
- Formato de salida: función auxiliar para formatear montos con separador de miles y dos decimales.

## Manejo de errores y extensiones sugeridas
- Manejo básico incluido:
  - Validación de que el monto sea numérico.
  - Verificación de que la moneda de origen esté entre las soportadas.
- Extensiones posibles:
  - Ajustar formato por moneda (por ejemplo, sin decimales para JPY).
  - Soporte de tasas en tiempo real mediante una API externa.
  - Exportar resultados a CSV o Excel.
  - Interfaz gráfica o REST API para uso remoto.
  - Añadir más monedas destino o permitir elegir destinos dinámicamente.

Licencia y contribuciones
- Proyecto pensado como ejercicio educativo. Se puede adaptar libremente; para colaboración en repositorio, añadir archivo LICENSE y directrices CONTRIBUTING según convenga.
