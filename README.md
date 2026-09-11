# Ciclo Contable — Distribuidora El Roble S.A.

Proyecto de contabilidad: una aplicación web de una sola página que recorre el
ciclo contable completo de una empresa comercial (compra y venta de
mercadería) — libro diario, libro mayor (cuentas T), balance de
comprobación, ajustes, balance ajustado, hoja de trabajo y estados
financieros — y permite agregar tus propias cuentas y asientos, que se
recalculan y se guardan automáticamente en el navegador.

## Cómo levantar el proyecto

No requiere instalar nada (sin Node, sin npm, sin base de datos). Es un solo
archivo HTML con su CSS y JavaScript incluidos.

**Opción 1 — la más simple:** haz doble clic en `index.html`. Se abre
directamente en tu navegador (Chrome, Edge, Firefox).

**Opción 2 — con un servidor local** (recomendable si tu navegador bloquea
algo al abrir el archivo directamente, o si quieres mostrarlo como "corriendo
un servidor" en la presentación):

```bash
# con Python (si lo tienes instalado)
python -m http.server 8000
# luego abre http://localhost:8000 en el navegador

# o con Node (si lo tienes instalado)
npx serve .
```

## Estructura del proyecto

```
ProyectoContabilidad-ElRoble/
├── index.html   → toda la aplicación (HTML + CSS + JavaScript)
└── README.md    → este archivo
```

Todo el código vive en `index.html`: los estilos dentro de `<style>`, la
lógica dentro de `<script>`. No hay dependencias externas aparte de las
fuentes tipográficas (Google Fonts, requiere conexión a internet para verse
con la tipografía correcta; sin conexión funciona igual pero con la fuente
del sistema).

## Cómo funciona

- **Datos de ejemplo**: la app arranca con un caso práctico ya resuelto
  (Distribuidora El Roble S.A., enero 2026) para que puedas ver el ciclo
  completo funcionando desde el primer momento.
- **Mis Datos**: pestaña donde agregas tus propias cuentas contables y
  asientos (con validación de que el Debe cuadre con el Haber). El resto de
  la aplicación —diario, mayor, balances, ajustes, hoja de trabajo, estados
  financieros— se recalcula automáticamente a partir de esos datos.
- **Persistencia**: cada cambio se guarda en `localStorage` del navegador
  (una capa de almacenamiento propia del navegador, sin servidor ni base de
  datos). Esto significa que tus datos quedan guardados en **ese
  navegador y ese equipo** mientras no borres los datos del sitio; no se
  sincronizan entre dispositivos.
- **Respaldo**: desde "Mis Datos" puedes descargar tus datos como un archivo
  `.json`, volver a cargarlos después, restaurar el ejemplo original o
  borrar todo.
- **Sistema de Modales y Edición Completa**: reemplazo integral de las ventanas
  nativas del navegador (`alert` y `confirm`) por modales modernos y estilizados
  con desenfoque de fondo (`backdrop-filter`) y soporte de teclado (Escape/Enter).
  Permite editar asientos contables completos (fecha, fase, glosa y líneas con
  comprobación dinámica de partida doble) y cuentas del catálogo directamente
  mediante ventanas emergentes, confirmaciones detalladas para eliminar asientos o
  cuentas, y notificaciones flotantes (*toasts*) automáticas.
- **Gráficos**: pestaña con el resultado del periodo (ingresos, gastos y
  utilidad) y las cuentas de activo/gasto de mayor a menor, calculados a
  partir de tus propios datos.
- **Exportar a PDF**: el botón "Exportar a PDF" (arriba a la derecha) abre el
  diálogo de impresión del navegador — ahí eliges "Guardar como PDF" para
  obtener el proyecto completo en un archivo, listo para entregar o imprimir.
- **Módulo de Examen — Indicadores Financieros (Paso 12)**: sección previa al
  cierre del periodo que contiene el análisis financiero integral para la evaluación
  parcial (caso *Distribuidora Comercial El Roble S.A.*, 2024 vs. 2025).
  Calcula y explica los 8 indicadores requeridos (Razón Corriente, Prueba Ácida,
  Nivel de Endeudamiento, Deuda/Patrimonio, ROA, ROE, Margen Neto y Rotación de
  Inventarios con base del 50%), resuelve las preguntas de análisis cualitativo y cuantitativo,
  presenta los estados financieros comparativos con análisis horizontal y provee una
  calculadora de ratios en vivo que se conecta con los datos actuales de El Roble.
- **Asientos de Cierre (Paso 13)**: procedimiento de cierre definitivo del ejercicio
  donde se liquidan las cuentas nominales (ingresos y gastos) contra Resumen de Rentas
  y Gastos, trasladando el resultado final al patrimonio.
- **Animación de arranque**: al abrir la app se ve una breve secuencia estilo
  terminal antes de mostrar el contenido (se puede omitir con un clic o
  cualquier tecla, y se desactiva sola si el sistema tiene activado
  "reducir movimiento").

## Tecnologías

HTML5, CSS3 (variables CSS, grid/flexbox, modo oscuro automático) y
JavaScript vanilla (sin frameworks ni librerías). Tipografías: Fraunces, IBM
Plex Sans e IBM Plex Mono (Google Fonts).
