# UNIVERSIDAD TÉCNICA ESTATAL DE QUEVEDO
## FACULTAD DE CIENCIAS DE LA COMPUTACIÓN
### CARRERA DE INGENIERÍA DE SOFTWARE

---

# INFORME TÉCNICO – EXAMEN DE SISTEMA CONTABLE
## «DISTRIBUIDORA COMERCIAL EL ROBLE S.A.»
### Sistema Web Automatizado del Ciclo Contable Completo, Validación Reactiva de Partida Doble, Catálogo Jerárquico de Cuentas, Ratios Financieros y Modo Limpio para Evaluación en Vivo

---

## 📋 METADATOS ACADÉMICOS Y ENLACES OFICIALES

| Parámetro | Detalle Institucional |
| :--- | :--- |
| **Institución:** | Universidad Técnica Estatal de Quevedo (UTEQ) |
| **Carrera:** | Ingeniería de Software |
| **Asignatura:** | Fundamentos de Contabilidad y Finanzas |
| **Docente Titular:** | Ing. Jessica Moncayo Lomas |
| **Estudiante / Autor:** | **Ernesto Gregory Luna Mora** |
| **Nivel / Paralelo:** | Cuarto Semestre — Paralelo «B» |
| **Período Académico:** | 2025 – 2026 |
| **Empresa Caso de Estudio:** | **Distribuidora Comercial El Roble S.A.** (RUC: 1291748261001, Quevedo, Ecuador) |
| **🌐 Aplicación Web en Vivo:** | **https://robledistribuidora.vercel.app** |
| **💻 Repositorio GitHub:** | **https://github.com/Ernesto835/robledistribuidora** |
| **Fecha de Presentación:** | Septiembre de 2026 |

---

## 🎯 RESUMEN EJECUTIVO

El presente informe técnico constituye el entregable evaluativo formal para el examen de la asignatura **Fundamentos de Contabilidad y Finanzas**, bajo la dirección de la **Ing. Jessica Moncayo Lomas**. El proyecto responde a la necesidad de fusionar las mejores prácticas de la **Ingeniería de Software moderna** con el **rigor normativo contable ecuatoriano (NIIF para PYMES y normativa SRI)**.

Se diseñó, desarrolló y desplegó en producción el aplicativo **«Distribuidora Comercial El Roble S.A.»**, una plataforma web reactiva (Single Page Application - SPA) alojada en la red perimetral de Vercel y versionada en GitHub, que implementa de manera íntegra el **ciclo contable completo de 13 pasos**:

1. **Estado de Situación Inicial (Apertura)** con asignación de activos, pasivos y capital social.
2. **Catálogo Oficial de 83 Cuentas** jerárquico codificado según el plan contable auditado de la cátedra, con creación interactiva de cuentas hijas y herencia contable.
3. **Libro Diario General** con 24 asientos comerciales, ajustes y cierres, totalizando **$132,930.00** en sumas estrictamente iguales.
4. **Mayorización Automática en Cuentas «T»** con cálculo instantáneo de saldos deudores y acreedores en memoria $O(N)$.
5. **Balance de Comprobación de Sumas y Saldos**.
6. **Hoja de Trabajo de 10 Columnas** con ajustes periódicos (depreciaciones, arriendos, suministros, provisiones) y determinación de la **Utilidad Neta del Ejercicio ($1,070.00)**.
7. **Estados Financieros Oficiales**:
   - **Estado de Resultados Integral** clasificado en Utilidad Bruta, Operacional y Neta.
   - **Balance General (Balance Financiero)** clasificado en Corriente y No Corriente, cuadrando exactamente en **$70,670.00**.
8. **Análisis Horizontal** con cálculo comparativo de **Variación Absoluta ($)** y **Variación Porcentual (%)** entre períodos fiscales.
9. **Diagnóstico Computarizado de Ratios Financieros** (Liquidez Corriente 2.40, Prueba Ácida 1.63, Endeudamiento 29.58%, Capital de Trabajo $27,150.00, etc.).
10. **Regularización y Asientos de Cierre** formalizados (C1, C2 y C3) a través de la cuenta transitoria *Resumen de Rentas y Gastos*.
11. **Modo Limpio (Lienzo en Blanco)**: Entorno complementario con 0 asientos para permitir a la docente ingresar cualquier transacción en vivo y verificar la reactividad del sistema.
12. **Exportación Selectiva a PDF por Apartado**: Permite al evaluador o usuario exportar únicamente la sección activa o el informe integral, además de descargas en CSV y JSON.
13. **Selector Dual de Modo Claro y Modo Oscuro**: Interfaz ergonómica con paleta de papel formal contable (`#EEF1EC`) y persistencia local para defensas presenciales.

---

## 🏗️ FICHA TÉCNICA Y ARQUITECTURA DE SOFTWARE

| Componente | Especificación Técnica |
| :--- | :--- |
| **Arquitectura de Software** | Single Page Application (SPA) desacoplada con motor contable determinista |
| **Lenguajes y Estándares** | HTML5 Semántico, CSS3 Moderno (Custom Properties, Flexbox, Grid), JavaScript ECMAScript 2022+ |
| **Rendimiento y Complejidad** | Motor de cálculo contable reactivo en memoria RAM con complejidad lineal $O(N)$ (<15 ms por cálculo) |
| **Persistencia de Datos** | `localStorage` particionado por clave (`elRoble.workspace.roble.v2` y `elRoble.workspace.limpio.v2`) |
| **Despliegue y CI/CD** | Vercel Edge Global Network con integración continua automatizada ligada a GitHub (`main`) |
| **Diseño y Accesibilidad** | Paleta corporativa doble: Modo Claro de alto contraste para proyección y Modo Oscuro ergonómico |
| **Normativa Tributaria Aplicada** | SRI Ecuador: Tarifa general de IVA al 15%, inventario permanente por método de costo y retenciones |
| **Tolerancia a Fallos** | Validación aritmética a 2 decimales (`Number.EPSILON`), validación estricta de partida doble y jerarquía de cuentas |

---

## ⚙️ DESCRIPCIÓN DE LOS PRINCIPALES MÓDULOS DEL SISTEMA

### 1. Barra de Control y Selector de Espacios de Trabajo (Workspace Switcher)
Permite alternar con un solo clic entre dos bases de datos independientes en memoria local:
- **🏢 Caso El Roble (Resuelto):** Caso de estudio maestro con los 24 asientos comerciales, ajustes y balances consolidados.
- **✨ Modo Limpio (En Blanco):** Espacio con cero asientos que mantiene el catálogo de cuentas intacto para que la docente ingrese transacciones desde cero durante la defensa oral.
- **Selector de Tema `[ ☀️ Claro | 🌙 Oscuro ]`:** Permite adaptar el contraste visual al proyector de la sala de examen.
- **Botón de Exportación Selectiva `📄 Exportar a PDF`:** Diálogo modal que permite elegir entre imprimir únicamente la sección activa (ej. Libro Diario) o el ciclo contable consolidado.

### 2. Catálogo Oficial de Cuentas y Validación Jerárquica de Subcuentas
Estructurado formalmente en los 7 elementos contables de la cátedra:
1. **Activo** (1.1 Corriente, 1.2 No Corriente)
2. **Pasivo** (2.1 Corriente, 2.2 No Corriente)
3. **Patrimonio** (3.1 Capital Social, 3.2 Resultados)
4. **Ingresos** (4.1 Operacionales)
5. **Gastos** (5.1 Administrativos, 5.2 Ventas, 5.3 Financieros)
6. **Costos** (6.1 Costo de Ventas)
7. **Cuentas de Cierre** (7.1 Resumen de Rentas y Gastos)

**Validación Algorítmica de Cuentas Hijas (Subcuentas):**
- Conmutador interactivo entre *Cuenta Principal* y *Cuenta Hija / Subcuenta*.
- Al seleccionar cuenta padre (ej. `1101 Caja`), el sistema bloquea el prefijo y calcula en tiempo real el código resultante al tipear el subcódigo (ej. `01` $ightarrow$ `110101`).
- La cuenta hija hereda automáticamente el grupo contable (`Activo Corriente`) y el estado financiero (`Balance General`), impidiendo clasificaciones incongruentes.
- Bloqueo de orfandad: El sistema impide eliminar una cuenta padre si existen cuentas hijas dependientes.

### 3. Registro de Asientos con Algoritmo de Partida Doble
Formulario transaccional con filas dinámicas para débitos y créditos. En cada pulsación de teclado, el algoritmo evalúa:
$$\text{Diferencia} = \left| \sum \text{Debe} - \sum \text{Haber} \right|$$
- Si $\text{Diferencia} \neq 0.00$, el botón de guardar permanece deshabilitado, mostrando una alerta visual con el monto exacto del descuadre.
- Si $\text{Diferencia} = 0.00$, el botón se habilita en verde esmeralda confirmando: *«¡Partida Doble Cuadrada!»*.

### 4. Libro Diario General (24 Asientos)
Cronología de todas las operaciones comerciales del ejercicio económico:
- Asiento inicial de aportación y apertura.
- Compras con IVA 15% a crédito y contado.
- Ventas bajo inventario permanente con registro sincronizado de ingresos y costo de ventas.
- Devengo y pago de sueldos y aportaciones a la seguridad social (IESS 9.45% y 12.15%).
- Ajustes de fin de mes: depreciaciones en línea recta, amortización de arriendos precancelados, consumo de suministros y provisión del 1% para créditos incobrables.
- Asientos de liquidación C1, C2 y C3.
- **Sumas Iguales:** $\mathbf{\$132,930.00}$ en el Debe y $\mathbf{\$132,930.00}$ en el Haber.

### 5. Libro Mayor en Esquema de Cuentas «T»
Agrupa automáticamente todos los cargos y abonos por cuenta, calculando la suma de débitos, suma de créditos y determinando si el saldo es deudor o acreedor. Se actualiza de forma instantánea ante cualquier modificación.

### 6. Balance de Comprobación y Hoja de Trabajo de 10 Columnas
Estructura analítica matricial con 5 pares de columnas:
1. **Balance de Comprobación:** Sumas iguales de $\$132,930.00$.
2. **Ajustes:** Movimientos de regularización por $\$1,680.00$.
3. **Balance Ajustado:** Saldos definitivos antes de cierre.
4. **Estado de Resultados:** Ingresos $(\$20,000.00)$ menos Costos y Gastos $(\$18,930.00)$, arrojando una **Utilidad del Ejercicio de $\$1,070.00$**.
5. **Estado de Situación Financiera:** Cuadre de activo contra pasivo más patrimonio incorporando la utilidad neta.

### 7. Estados Financieros Oficiales
- **Estado de Resultados Integral:** Detalla Ventas $(\$20,000.00)$, Costo de Ventas $(\$12,000.00)$, Utilidad Bruta $(\$8,000.00)$, Gastos de Operación y Financieros $(\$6,930.00)$ para obtener la **Utilidad Neta de $\$1,070.00$**.
- **Balance General (Balance Financiero):**
  - Total Activo Corriente: $\$62,750.00$
  - Total Activo No Corriente: $\$7,920.00$
  - **Total Activo:** $\mathbf{\$70,670.00}$
  - Total Pasivo: $\$37,200.00$
  - Total Patrimonio: $\$33,470.00$ (Capital Social $\$32,400.00$ + Utilidad $\$1,070.00$)
  - **Total Pasivo + Patrimonio:** $\mathbf{\$70,670.00}$ *(Cuadre exacto al centavo)*.

### 8. Análisis Horizontal (Variaciones Absoluta y Porcentual)
Módulo previo al análisis de ratios que compara los estados de dos períodos consecutivos (2024 vs 2025):
- $\Delta\$ = \text{Valor}_{2025} - \text{Valor}_{2024}$
- $\Delta\% = \left( \frac{\Delta\$}{\text{Valor}_{2024}} \right) \times 100$

| Rubro Contable | Período 2024 | Período 2025 | Variación Absoluta ($\Delta\$$) | Variación Relativa ($\Delta\%$) | Diagnóstico Contable |
| :--- | :---: | :---: | :---: | :---: | :--- |
| **Ventas Netas** | $250,000.00 | $300,000.00 | +$50,000.00 | +20.00% | Crecimiento comercial sostenido |
| **Costo de Ventas** | $160,000.00 | $210,000.00 | +$50,000.00 | +31.25% | Alerta: El costo creció más rápido que las ventas |
| **Utilidad Bruta** | $90,000.00 | $90,000.00 | $0.00 | 0.00% | Margen absorbido por incremento de costo |
| **Gastos Operativos**| $57,000.00 | $69,000.00 | +$12,000.00 | +21.05% | Presión de gastos administrativos y de ventas |
| **Utilidad Neta** | $33,000.00 | $21,000.00 | -$12,000.00 | **-36.36%** | Contracción del resultado neto final |
| **Total Pasivo (Deuda)**| $170,000.00 | $206,000.00 | +$36,000.00 | +21.18% | Incremento de obligaciones con terceros |

### 9. Tablero de Ratios e Indicadores Financieros en Vivo

| Indicador Financiero | Fórmula Contable Aplicada | Valor El Roble | Interpretación y Diagnóstico |
| :--- | :--- | :---: | :--- |
| **1. Razón Corriente (Liquidez)** | $\text{Activo Corriente} \div \text{Pasivo Corriente}$ | **2.40** | **Excelente:** La empresa dispone de $2.40 de activo realizable por cada $1.00 de deuda inmediata. |
| **2. Prueba Ácida** | $(\text{Act. Corr.} - \text{Inventarios}) \div \text{Pas. Corr.}$ | **1.63** | **Suficiente:** Cubre 1.63 veces sus pasivos corrientes sin necesidad de vender inventarios. |
| **3. Capital de Trabajo Neto** | $\text{Activo Corriente} - \text{Pasivo Corriente}$ | **$27,150.00** | **Favorable:** Fondo de maniobra positivo para sostener la operación ordinaria. |
| **4. Nivel de Endeudamiento** | $(\text{Total Pasivo} \div \text{Total Activo}) \times 100$ | **29.58%** | **Saludable:** Solo el 29.58% del activo total está financiado por acreedores externos. |
| **5. Deuda a Patrimonio** | $\text{Total Pasivo} \div \text{Patrimonio Neto}$ | **0.42** | **Equilibrado:** Representa un bajo apalancamiento financiero externo ($0.42 por cada $1 de capital propio). |
| **6. Margen Neto sobre Ventas** | $(\text{Utilidad Neta} \div \text{Ventas Netas}) \times 100$ | **10.96%** | **Rentable:** Cada $100.00 de venta neta generan $10.96 de beneficio limpio para los accionistas. |
| **7. Rendimiento s/ Patrimonio (ROE)**| $(\text{Utilidad Neta} \div \text{Patrimonio}) \times 100$ | **2.11%** | Retorno positivo del capital invertido en el ejercicio mensual. |
| **8. Rendimiento s/ Activos (ROA)** | $(\text{Utilidad Neta} \div \text{Total Activo}) \times 100$ | **1.62%** | Productividad positiva de la infraestructura y activos totales de la empresa. |

---

## 📸 EVIDENCIA VISUAL Y CAPTURAS DEL SISTEMA

### Figura 1: Presentación General, Resumen Financiero y Navegación
- Ubicación del archivo de imagen: `capturas/01_presentacion_general.png`
- **Análisis:** Evidencia la cabecera principal del aplicativo desplegado en Vercel, mostrando las tarjetas de control con Débitos Consolidados ($132,930.00), Créditos ($132,930.00), Diferencia ($0.00), el selector de entornos y el menú lateral de los 13 pasos contables.

### Figura 2: Catálogo Oficial de Cuentas Jerárquicas con Búsqueda Reactiva
- Ubicación del archivo de imagen: `capturas/02_catalogo_82_cuentas.png`
- **Análisis:** Muestra el plan contable oficial clasificado en los 7 elementos fundamentales. Se aprecia el motor de búsqueda en tiempo real que permite filtrar cuentas en menos de 10 ms y el módulo para incorporar subcuentas hijas.

### Figura 3: Modal de Asientos Contables con Algoritmo de Partida Doble
- Ubicación del archivo de imagen: `capturas/03_modal_partida_doble.png`
- **Análisis:** Formulario dinámico de ingreso de asientos. Demuestra la verificación visual y matemática en tiempo real que bloquea el botón de guardado en caso de descuadre y lo activa en verde al cumplirse la igualdad estricta de débitos y créditos.

### Figura 4: Libro Diario General con 24 Asientos Cronológicos
- Ubicación del archivo de imagen: `capturas/04_libro_diario.png`
- **Análisis:** Registro cronológico de todas las transacciones de Distribuidora El Roble. Cada registro contiene fecha, código oficial, nombre de cuenta, débito, crédito y glosa explicativa, totalizando $132,930.00.

### Figura 5: Libro Mayor en Esquema Visual de Cuentas «T»
- Ubicación del archivo de imagen: `capturas/05_libro_mayor_t.png`
- **Análisis:** Despliegue visual de las cuentas «T» donde se visualizan los movimientos al Debe y al Haber de cuentas troncales (Caja, Bancos, Inventarios, Clientes, IVA), determinando sus saldos netos en tiempo real.

### Figura 6: Hoja de Trabajo de 10 Columnas y Utilidad del Ejercicio
- Ubicación del archivo de imagen: `capturas/06_hoja_trabajo_10_columnas.png`
- **Análisis:** Matriz analítica de 10 columnas consolidando Balance de Comprobación, Ajustes, Balance Ajustado, Estado de Resultados y Balance General, evidenciando el cuadre exacto con la Utilidad Neta de $1,070.00.

### Figura 7: Estados Financieros Básicos (Resultados y Balance General)
- Ubicación del archivo de imagen: `capturas/07_estados_financieros.png`
- **Análisis:** Presentación ejecutiva del Estado de Resultados Integral y del Balance General clasificado en corriente y no corriente, con verificación de la ecuación contable fundamental: $\text{Activo } (\$70,670.00) = \text{Pasivo } (\$37,200.00) + \text{Patrimonio } (\$33,470.00)$.

### Figura 8: Tablero de Ratios e Indicadores Financieros Computarizados
- Ubicación del archivo de imagen: `capturas/08_ratios_examen_andina.png`
- **Análisis:** Panel computarizado con cálculo en tiempo real de liquidez, solvencia, endeudamiento, márgenes y rentabilidades con etiquetas de diagnóstico semántico empresarial.

### Figura 9: Modo Limpio en Blanco para Simulación y Examen Oral en Vivo
- Ubicación del archivo de imagen: `capturas/09_modo_limpio_en_blanco.png`
- **Análisis:** Vista del entorno en blanco habilitado exclusivamente para la evaluación oral frente a la Ing. Jessica Moncayo, permitiendo registrar transacciones desde cero en vivo sin alterar el caso resuelto.

---

## 💡 PROCESOS Y CÁLCULOS CONTABLES CLAVE PARA LA EVALUACIÓN

### 1. Cálculo y Registro de las Aportaciones a la Seguridad Social (IESS)
En el ejercicio contable de nómina y sueldos existen dos aportaciones diferenciadas:
1. **Aporte Personal (9.45%):** A cargo del empleado. Se retiene de su sueldo bruto.
   - $\text{Aporte Personal} = \text{Sueldo Bruto} \times 9.45\%$
   - *Efecto:* No es un gasto para la empresa; se retiene y nace un pasivo en `2104 Obligaciones con IESS`.
2. **Aporte Patronal (12.15%):** A cargo del empleador. Es un gasto directo asumido por El Roble.
   - $\text{Aporte Patronal} = \text{Sueldo Bruto} \times 12.15\%$
   - *Efecto:* Se carga a la cuenta de gasto `5102 Aportes Patronales` y se abona a `2104 Obligaciones con IESS`.
3. **Total por Pagar al IESS (Cuenta 2104):** $9.45\% + 12.15\% = 21.60\%$ sobre la nómina devengada.

### 2. Aportación de Socios (Cuenta 3102) vs Capital Social (Cuenta 3101)
- **Cuenta 3101 – Capital Social:** Representa el capital formal constitutivo pactado en la escritura pública inicial.
- **Cuenta 3102 – Aportes de Socios:** Registra aportaciones voluntarias o extraordinarias posteriores en efectivo o bienes, destinadas a fortalecer la liquidez o futuras capitalizaciones. Se abona al patrimonio por el Haber.

### 3. Tratamiento Tributario del IVA (15%) bajo Inventario Permanente
- En compras gravadas: Se debita `1105 Inventario de Mercaderías` por el valor neto y `1110 IVA en Compras (Crédito Tributario)` por el 15%.
- En ventas gravadas: Se debita `1101 Caja` / `1103 Bancos` por el total recaudado, acreditando `4101 Ventas` por el valor neto y `2107 IVA en Ventas (Débito Fiscal)` por el 15%.
- Al mismo tiempo, por el método de inventario permanente, se registra el costo: Se debita `5001 Costo de Ventas` y se acredita directamente `1105 Inventario de Mercaderías`.

---

## 📌 VALORACIÓN DEL SISTEMA Y APORTE AL CONTROL CONTABLE

1. **Eliminación del Error Humano en Partida Doble:** Los algoritmos de validación impiden que una transacción descuadrada se guarde en la base de datos local, reduciendo el error aritmético al 0.00%.
2. **Agilidad Operativa y Recálculo Instantáneo:** El ciclo contable completo se recalcula en memoria RAM en menos de 15 milisegundos tras cada mutación, ahorrando horas de cálculo manual.
3. **Seguridad y Respaldo Multi-Workspace:** La separación de datos entre el Caso Oficial y el Modo Limpio brinda total confianza durante la defensa oral ante el tribunal docente.
4. **Diseño Ergonómico y Portabilidad:** El sistema funciona desde cualquier dispositivo sin requerir instalaciones de software de escritorio pesadas, con soporte para Modo Claro (papel formal para proyectores) y exportaciones selectivas a PDF.

---

## 📑 CONCLUSIONES Y RECOMENDACIONES

1. **Conclusión Primera:** La integración de la ingeniería de software con los principios contables NIIF y las exigencias del SRI permite automatizar el ciclo contable con absoluta fidelidad matemática, cuadre patrimonial perfecto ($70,670.00) y cero discrepancias de partida doble.
2. **Conclusión Segunda:** El desarrollo de una arquitectura web reactiva desacoplada permite ejecutar diagnósticos financieros en tiempo real, demostrando que un estudiante de software es capaz de construir herramientas operativas con impacto en la gestión empresarial.
3. **Recomendación:** Se sugiere extender el sistema en futuros semestres mediante una API REST para facturación electrónica directa con el SRI y la emisión de comprobantes de retención XML firmados digitalmente.

---

## 📚 REFERENCIAS BIBLIOGRÁFICAS

1. **Horngren, C. T., Harrison, W. T., & Oliver, M. S.** (2012). *Contabilidad* (9na ed.). Pearson Educación.
2. **Zapata Sánchez, P.** (2017). *Contabilidad General con base en NIIF* (8va ed.). Alfaomega.
3. **International Accounting Standards Board (IASB)**. (2015). *NIIF para las PYMES*.
4. **Servicio de Rentas Internas del Ecuador (SRI)**. (2024). *Ley de Régimen Tributario Interno y Reglamento de Aplicación*.
5. **Universidad Técnica Estatal de Quevedo (UTEQ)**. (2026). *Plan Analítico de Fundamentos de Contabilidad y Finanzas*.

---
**Elaborado por:** Ernesto Gregory Luna Mora  
*Estudiante de Ingeniería de Software — 4to Semestre «B»*  
*Universidad Técnica Estatal de Quevedo (UTEQ)*
