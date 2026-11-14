# Misión «Cero errores de captura»

## Metadatos

| Campo | Valor |
|---|---|
| **Duración** | 42 minutos |
| **Complejidad** | Media |
| **Nivel Bloom** | Crear |

## Descripción General

Recibir solicitudes administrativo-financieras con información faltante; crear en Forms un formulario de captura estandarizada con campos pertinentes y validaciones disponibles, registrar respuestas de prueba y revisar su salida en Excel. Comprobación individual: identificar datos incompletos y demostrar que los resultados sirven para un reporte posterior, incluso en Power BI.

Esta práctica cierra el ciclo del cierre operativo mensual iniciado en la Práctica 1, atacando el problema de origen: las solicitudes que llegan con datos incompletos y generan reprocesos. El formulario estandarizado que crearás se integrará con la biblioteca SharePoint `Documentos-CierreOperativo` y el equipo de Teams configurado en prácticas anteriores.

## Objetivos de Aprendizaje

- [ ] Diagnosticar los campos de información faltante o inconsistente en solicitudes administrativo-financieras del cierre mensual.
- [ ] Diseñar y crear un formulario en Microsoft Forms con tipos de pregunta pertinentes (texto, opción múltiple, fecha, número, escala) y validaciones nativas (obligatorio, límites numéricos, formato de texto).
- [ ] Registrar al menos cinco respuestas de prueba y exportar los resultados a Excel Online, identificando registros con datos incompletos o inconsistentes.
- [ ] Demostrar que el conjunto de datos exportado desde Forms puede conectarse a Power BI o, como alternativa, analizarse mediante tabla dinámica en Excel para generar un reporte básico.

## Prerrequisitos

**Conocimientos previos:**

- Haber completado las Prácticas 1, 2, 3 y 4 del curso.
- Haber revisado los contenidos del Módulo 5: lecciones 5.1 (Formularios, encuestas y evaluaciones) y 5.2 (Recopilación, revisión y uso de resultados).
- Comprensión básica de tipos de datos (texto, número, fecha) y su impacto en la calidad de la información.

**Acceso y recursos:**

| Recurso | Detalle |
|---|---|
| Cuenta Microsoft 365 | Licencia institucional activa con acceso a Forms, Excel Online, SharePoint Online y Teams |
| Microsoft Forms | Accesible en `https://forms.microsoft.com` con la cuenta institucional |
| Microsoft Excel Online | Integrado en Microsoft 365 (servicio Evergreen, abril 2025) |
| Excel de escritorio (opcional) | Versión 2504 (build 18730.20144), canal Current Channel |
| Power BI Desktop (demostración) | Versión 2.128.751.0 (marzo 2025) — en equipo del instructor o del participante. Descarga: `https://www.microsoft.com/es-es/download/details.aspx?id=58494` |
| Power BI Service (alternativa) | `https://app.powerbi.com` con cuenta institucional |
| Navegador web | Microsoft Edge 134.0.3124.72+ (recomendado) o Google Chrome 134.0.6998.89+ |
| Biblioteca SharePoint | `Documentos-CierreOperativo` en `https://[tenant].sharepoint.com/sites/CierreOperativo-Practica` |
| Equipo de Teams | `CierreOperativo-[Apellido]` con canal `Informe-Mensual` |

## Entorno de Laboratorio

**Artefactos existentes de prácticas anteriores (no recrear):**

| Artefacto | Ubicación |
|---|---|
| Directorio de trabajo OneDrive | `/CierreOperativo/Semana1/` |
| Sitio SharePoint | `https://[tenant].sharepoint.com/sites/CierreOperativo-Practica` |
| Biblioteca con metadatos | `Documentos-CierreOperativo` (columnas: Periodo, TipoDocumento, Estado, Responsable) |
| Equipo de Teams | `CierreOperativo-[Apellido]` con canales General, Informe-Mensual, Pendientes-y-Acuerdos |

**Solicitudes de ejemplo proporcionadas por el instructor:**

El instructor entrega (vía Teams o en pantalla) tres solicitudes con información faltante. A continuación se reproduce el contenido textual de cada una para que el participante las analice:

### Solicitud A — Correo de María López

```
De: María López
Asunto: Solicitud urgente

Hola, necesito que me aprueben un reembolso por los viáticos del viaje
a la sede norte. Fueron como 4500 o 5000 pesos, no recuerdo exacto.
Adjunto la factura después.

Gracias.
```

### Solicitud B — Mensaje de Teams de Carlos R.

```
Carlos R. escribió en el chat general:
"Necesito un anticipo para comprar materiales. Es para el proyecto
del segundo piso. Lo necesito ya."
```

### Solicitud C — Nota en papel digitalizada (PDF)

```
SOLICITUD DE COMPRA
Solicitante: J. Pérez
Área: (en blanco)
Concepto: Tóner y papelería
Monto: Varios
Fecha: marzo
Aprobado por: (sin firma)
```

**Verificación inicial del entorno (antes de comenzar):**

1. Abre `https://forms.microsoft.com` e inicia sesión con tu cuenta institucional.
2. Verifica que aparece tu nombre y la organización en la esquina superior derecha.
3. Confirma que puedes ver el botón **+ Nuevo formulario**.

## Instrucciones Paso a Paso

### Paso 1: Diagnosticar campos faltantes en las solicitudes

**Objetivo:** Identificar qué información falta o es inconsistente en cada solicitud de ejemplo para determinar los campos obligatorios del formulario.

**Instrucciones:**

1. Lee las tres solicitudes proporcionadas en la sección **Entorno de Laboratorio**.
2. Abre un documento nuevo en tu navegador (puede ser un archivo de texto en OneDrive o una nota rápida) y crea una tabla de diagnóstico con el siguiente formato:

```
Campo requerido          | Solicitud A | Solicitud B | Solicitud C
-------------------------|-------------|-------------|-------------
Nombre completo          |     ✓ (*)   |    ✗ (*)    |    ✗ (*)
Área / Centro de costo   |     ✗       |    ✗        |    ✗
Tipo de solicitud        |     ✓       |    ✓        |    ✓
Periodo de referencia    |     ✗       |    ✗        |    ✗ (*)
Monto exacto             |     ✗ (*)   |    ✗        |    ✗
Descripción del concepto |     ✓       |    ✓ (*)    |    ✓
Documento de soporte     |     ✗       |    ✗        |    ✗
```

> (*) Notas: Solicitud A tiene nombre pero no área; monto es aproximado. Solicitud B usa nombre parcial "Carlos R." sin apellido completo. Solicitud C usa inicial "J. Pérez" y "marzo" sin año ni día. El monto dice "Varios" (texto, no número).

3. Confirma que los **siete campos** listados son los mínimos necesarios para una captura estandarizada sin ambigüedades.

**Resultado esperado:** Una tabla que evidencia que ninguna de las tres solicitudes contiene los siete campos completos y correctos.

**Verificación:** Compara tu tabla con la referencia anterior. Debes haber identificado al menos 5 campos faltantes o inconsistentes por solicitud.

---

### Paso 2: Crear el formulario en Microsoft Forms

**Objetivo:** Iniciar un nuevo formulario con el título y la descripción estandarizados del curso.

**Instrucciones:**

1. Navega a `https://forms.microsoft.com`.
2. Haz clic en **+ Nuevo formulario** (no en "Nuevo cuestionario", ya que no se requiere calificación automática).
3. Haz clic en el título **"Formulario sin título"** y reemplázalo por:

```
Solicitud Administrativa - Cierre Mensual [Mes/Año]
```

> Sustituye `[Mes/Año]` por el mes y año indicados por el instructor (ejemplo: `Abril/2025`).

4. Haz clic en el campo de descripción debajo del título y escribe:

```
Formulario estandarizado para la captura de solicitudes administrativo-financieras
del cierre operativo mensual. Todos los campos marcados con asterisco (*) son
obligatorios. Complete cada campo con datos exactos para evitar reprocesos.
```

**Resultado esperado:** El formulario aparece con el título y la descripción configurados. No tiene preguntas aún.

**Verificación:** El título se muestra completo en la barra superior del formulario. La descripción es visible debajo del título en la vista previa.

---

### Paso 3: Agregar el campo «Nombre completo del solicitante»

**Objetivo:** Crear la primera pregunta de tipo texto con validación de campo obligatorio.

**Instrucciones:**

1. Haz clic en **+ Agregar nuevo** (o el botón **+**).
2. Selecciona el tipo **Texto**.
3. En el campo de la pregunta, escribe:

```
Nombre completo del solicitante
```

4. Activa el interruptor **Obligatorio** (parte inferior derecha de la pregunta).
5. Haz clic en el icono de tres puntos (**⋯**) de la pregunta y selecciona **Subtítulo**. En el campo de subtítulo escribe:

```
Escriba nombre(s) y apellido(s) completos. Ejemplo: María Elena López García.
```

**Resultado esperado:** Primera pregunta visible con asterisco rojo (*) indicando obligatoriedad y subtítulo de instrucción.

**Verificación:** En la vista previa (botón **Vista previa** en la barra superior), el campo aparece como obligatorio y muestra el subtítulo.

---

### Paso 4: Agregar el campo «Área o centro de costo»

**Objetivo:** Crear una pregunta de opción múltiple con lista predefinida para estandarizar las áreas.

**Instrucciones:**

1. Haz clic en **+ Agregar nuevo** → **Opción**.
2. En el campo de la pregunta, escribe:

```
Área o centro de costo
```

3. Configura las opciones con los siguientes valores (una por línea, haciendo clic en **+ Agregar opción** para cada nueva):

```
Dirección General
Administración y Finanzas
Recursos Humanos
Tecnología de la Información
Operaciones
Jurídico
Otro (especifique en Descripción del concepto)
```

4. Activa el interruptor **Obligatorio**.
5. Asegúrate de que **NO** esté habilitada la opción "Respuestas múltiples" (debe ser selección única).

**Resultado esperado:** Pregunta de opción única con 7 opciones predefinidas y marcada como obligatoria.

**Verificación:** En vista previa, solo se puede seleccionar una opción a la vez. Intentar enviar sin seleccionar muestra mensaje de error.

---

### Paso 5: Agregar el campo «Tipo de solicitud»

**Objetivo:** Crear una pregunta de opción que clasifique el tipo de trámite.

**Instrucciones:**

1. Haz clic en **+ Agregar nuevo** → **Opción**.
2. Pregunta:

```
Tipo de solicitud
```

3. Opciones:

```
Reembolso
Anticipo
Compra
Otro
```

4. Activa **Obligatorio**.

**Resultado esperado:** Pregunta de opción única con 4 categorías de solicitud, obligatoria.

**Verificación:** Vista previa muestra las 4 opciones como botones de radio (selección única).

---

### Paso 6: Agregar el campo «Periodo de referencia»

**Objetivo:** Capturar la fecha del periodo al que corresponde la solicitud usando el tipo de pregunta Fecha.

**Instrucciones:**

1. Haz clic en **+ Agregar nuevo** → **Fecha**.
2. Pregunta:

```
Periodo de referencia (fecha del gasto o necesidad)
```

3. Activa **Obligatorio**.
4. Agrega un subtítulo (vía menú **⋯** → **Subtítulo**):

```
Seleccione la fecha exacta del gasto o la fecha de inicio del periodo. No use fechas aproximadas.
```

**Resultado esperado:** Pregunta de tipo fecha con selector de calendario, obligatoria, con subtítulo instructivo.

**Verificación:** En vista previa, al hacer clic aparece un selector de calendario que solo permite fechas válidas.

---

### Paso 7: Agregar el campo «Monto solicitado» con validación numérica

**Objetivo:** Capturar el monto como número con validación de rango para impedir valores no numéricos o negativos.

**Instrucciones:**

1. Haz clic en **+ Agregar nuevo** → **Texto**.
2. Pregunta:

```
Monto solicitado (en pesos, sin símbolos)
```

3. Activa **Obligatorio**.
4. Haz clic en el icono de tres puntos (**⋯**) → **Restricciones**.
5. En el menú desplegable de restricciones, selecciona **Número**.
6. Configura la restricción:
   - Condición: **Mayor que**
   - Valor: **0**

```
Restricción configurada:
  Tipo:      Número
  Condición: Mayor que
  Valor:     0
  Mensaje de error personalizado: "Ingrese un monto numérico mayor que cero."
```

7. Si la interfaz lo permite, escribe el mensaje de error personalizado en el campo correspondiente.

**Resultado esperado:** Pregunta de texto con restricción numérica que rechaza valores ≤ 0 y entradas no numéricas.

**Verificación:** En vista previa, ingresa el texto `Varios` y verifica que Forms muestra un error de validación. Ingresa `-500` y verifica que también se rechaza. Ingresa `4500` y verifica que se acepta.

---

### Paso 8: Agregar el campo «Descripción del concepto»

**Objetivo:** Capturar una descripción detallada del gasto o necesidad en texto largo obligatorio.

**Instrucciones:**

1. Haz clic en **+ Agregar nuevo** → **Texto**.
2. Pregunta:

```
Descripción del concepto
```

3. Activa el interruptor **Respuesta larga** (aparece dentro de la configuración de la pregunta de texto).
4. Activa **Obligatorio**.
5. Agrega subtítulo:

```
Describa con detalle el motivo de la solicitud, incluyendo destino, proyecto o actividad relacionada.
```

**Resultado esperado:** Pregunta de texto largo, obligatoria, con subtítulo orientador.

**Verificación:** En vista previa, el campo de respuesta muestra un área de texto expandida (multilínea).

---

### Paso 9: Agregar el campo «Documento de soporte» (carga de archivo)

**Objetivo:** Permitir que el solicitante adjunte un comprobante o factura digitalizada.

**Instrucciones:**

1. Haz clic en **+ Agregar nuevo** → **Carga de archivos**.

> **Nota importante:** Si aparece un mensaje indicando que se creará una carpeta en OneDrive del propietario del formulario para almacenar los archivos, haz clic en **Aceptar** para continuar.

> **Si la opción de carga de archivos no está disponible** (el administrador del tenant puede haberla deshabilitado), omite este paso y agrega en su lugar una pregunta de tipo **Texto** con la instrucción: `"Pegue aquí el enlace al documento de soporte almacenado en OneDrive o SharePoint"`. Marca esta alternativa como obligatoria.

2. Pregunta:

```
Documento de soporte (factura, recibo o cotización)
```

3. Configura:
   - Límite de archivos: **1**
   - Tamaño máximo por archivo: **10 MB**
   - Tipos de archivo permitidos (si la interfaz lo permite): PDF, JPG, PNG, XLSX

4. Este campo **no** se marca como obligatorio (puede haber solicitudes de anticipo sin soporte previo).

**Resultado esperado:** Pregunta de carga de archivo configurada con límites, no obligatoria.

**Verificación:** En vista previa, aparece un botón para cargar archivo con las restricciones indicadas.

---

### Paso 10: Configurar opciones generales del formulario

**Objetivo:** Restringir el formulario a usuarios de la organización y habilitar el registro del nombre del respondedor.

**Instrucciones:**

1. Haz clic en el icono de tres puntos (**⋯**) en la esquina superior derecha del formulario (o en **Configuración** / **Settings**).
2. Configura las siguientes opciones:

```
Configuración del formulario:
  ☑ Aceptar respuestas
  ☑ Solo pueden responder personas de mi organización
  ☑ Registrar nombre
  ☐ Un registro por persona (dejar desactivado para permitir pruebas múltiples)
  ☑ Notificación de cada respuesta por correo electrónico
  Fecha de inicio: (dejar vacío para pruebas)
  Fecha de fin:    (dejar vacío para pruebas)
```

3. Guarda la configuración (se guarda automáticamente al cerrar el panel).

**Resultado esperado:** El formulario solo acepta respuestas de usuarios autenticados de la organización y registra automáticamente su nombre.

**Verificación:** En la vista previa, verifica que aparece tu nombre de usuario en la parte superior del formulario como respondedor identificado.

---

### Paso 11: Revisar el formulario completo en vista previa

**Objetivo:** Validar que todas las preguntas, tipos y validaciones están correctamente configurados antes de registrar respuestas.

**Instrucciones:**

1. Haz clic en **Vista previa** (botón en la barra superior del editor de Forms).
2. Recorre todas las preguntas y verifica:

```
Lista de verificación del formulario:
  [1] Nombre completo del solicitante  → Texto, obligatorio, con subtítulo    ✓
  [2] Área o centro de costo           → Opción (7 opciones), obligatorio     ✓
  [3] Tipo de solicitud                → Opción (4 opciones), obligatorio     ✓
  [4] Periodo de referencia            → Fecha, obligatorio, con subtítulo    ✓
  [5] Monto solicitado                 → Texto con restricción numérica >0    ✓
  [6] Descripción del concepto         → Texto largo, obligatorio             ✓
  [7] Documento de soporte             → Carga de archivo, no obligatorio     ✓
  Total de preguntas: 7
```

3. Intenta enviar el formulario **sin completar ningún campo** para verificar que los campos obligatorios muestran error.
4. Regresa al editor haciendo clic en **Atrás**.

**Resultado esperado:** Los 6 campos obligatorios muestran mensajes de error al intentar enviar vacíos. El campo de monto rechaza texto no numérico.

**Verificación:** Confirma que el formulario tiene exactamente 7 preguntas y que las validaciones funcionan según lo configurado.

---

### Paso 12: Registrar cinco respuestas de prueba

**Objetivo:** Poblar el conjunto de datos con respuestas controladas: tres completas, una bloqueada por validación y una con datos inconsistentes.

**Instrucciones:**

1. Desde la vista previa (o copiando el enlace del formulario y abriéndolo en una pestaña nueva), registra las siguientes respuestas una por una:

**Respuesta 1 — Completa y correcta:**

```
Nombre:       María Elena López García
Área:         Administración y Finanzas
Tipo:         Reembolso
Periodo:      15/03/2025
Monto:        4500
Descripción:  Reembolso de viáticos por visita a sede norte, transporte y alimentación.
Soporte:      (adjuntar cualquier archivo PDF de prueba o dejar vacío)
```

**Respuesta 2 — Completa y correcta:**

```
Nombre:       Carlos Alberto Ramírez Soto
Área:         Operaciones
Tipo:         Anticipo
Periodo:      01/04/2025
Monto:        12000
Descripción:  Anticipo para compra de materiales de construcción, proyecto segundo piso.
Soporte:      (dejar vacío — es anticipo sin factura previa)
```

**Respuesta 3 — Completa y correcta:**

```
Nombre:       Javier Pérez Mendoza
Área:         Tecnología de la Información
Tipo:         Compra
Periodo:      20/03/2025
Monto:        3200
Descripción:  Compra de tóner HP 58A y resma de papel bond tamaño carta.
Soporte:      (adjuntar cualquier archivo de prueba o dejar vacío)
```

2. **Respuesta 4 — Prueba de validación (bloqueada):**

```
Nombre:       (dejar vacío)
Área:         (no seleccionar)
Tipo:         Reembolso
Periodo:      (no seleccionar)
Monto:        Varios
Descripción:  (dejar vacío)
```

   Intenta enviar. **El formulario debe impedir el envío** mostrando errores en los campos obligatorios y en la validación numérica del monto. **No completes los campos; solo verifica que las validaciones funcionan.** Cierra la vista previa sin enviar.

3. **Respuesta 5 — Datos inconsistentes (se envía completa):**

```
Nombre:       Ana M.
Área:         Otro (especifique en Descripción del concepto)
Tipo:         Otro
Periodo:      01/01/2020
Monto:        1
Descripción:  Prueba con datos inconsistentes para verificación en análisis posterior.
Soporte:      (dejar vacío)
```

> Esta respuesta se envía exitosamente porque cumple las validaciones mínimas, pero contiene datos sospechosos: nombre incompleto, área genérica, fecha antigua y monto de $1. Servirá para identificar inconsistencias en el análisis.

**Resultado esperado:** 4 respuestas registradas exitosamente (Respuestas 1, 2, 3 y 5). La Respuesta 4 fue bloqueada por las validaciones. El contador de respuestas en la pestaña **Respuestas** del formulario muestra **4**.

**Verificación:** Regresa al editor del formulario. Haz clic en la pestaña **Respuestas**. Confirma que el contador indica **4 respuestas**.

---

### Paso 13: Revisar el resumen de respuestas en Forms

**Objetivo:** Interpretar el resumen visual automático que genera Forms para cada pregunta.

**Instrucciones:**

1. En la pestaña **Respuestas** del formulario, observa los gráficos de resumen automático:
   - **Área o centro de costo:** gráfico circular mostrando la distribución por área.
   - **Tipo de solicitud:** gráfico circular con la distribución por tipo.
   - **Monto solicitado:** lista de valores numéricos ingresados.

2. Identifica visualmente la Respuesta 5 (Ana M.) como dato atípico: área "Otro", tipo "Otro", monto $1, fecha 2020.

3. Haz clic en **Ver resultados** (debajo del contador de respuestas) para navegar respuesta por respuesta y confirmar los datos individuales.

**Resultado esperado:** El resumen muestra 4 respuestas con distribuciones coherentes. La respuesta de "Ana M." es visualmente identificable como atípica en los gráficos.

**Verificación:** Puedes navegar entre las 4 respuestas individuales usando las flechas de navegación en la vista de resultados.

---

### Paso 14: Exportar resultados a Excel Online

**Objetivo:** Generar el libro de Excel con los datos del formulario para análisis detallado.

**Instrucciones:**

1. En la pestaña **Respuestas**, haz clic en **Abrir en Excel** (botón verde con ícono de Excel).
2. Se descargará un archivo `.xlsx` o se abrirá directamente en Excel Online (dependiendo de la configuración del navegador).
3. Si se descargó, ábrelo en Excel Online subiendo el archivo a OneDrive:
   - Navega a `https://onedrive.com` → carpeta `/CierreOperativo/Semana1/`.
   - Sube el archivo y ábrelo desde allí.
4. Observa la estructura de la tabla generada:

```
Columnas esperadas en el Excel exportado:
  A: Id
  B: Hora de inicio
  C: Hora de finalización
  D: Correo electrónico
  E: Nombre
  F: Nombre completo del solicitante
  G: Área o centro de costo
  H: Tipo de solicitud
  I: Periodo de referencia (fecha del gasto o necesidad)
  J: Monto solicitado (en pesos, sin símbolos)
  K: Descripción del concepto
  L: Documento de soporte (factura, recibo o cotización)
```

5. Verifica que hay **4 filas de datos** (una por cada respuesta enviada exitosamente).

**Resultado esperado:** Un libro de Excel con una tabla estructurada de 4 registros y aproximadamente 12 columnas (el número exacto puede variar si se incluyeron o no columnas de metadatos del sistema).

**Verificación:** Confirma que la fila correspondiente a "Ana M." muestra los datos inconsistentes: fecha `01/01/2020`, monto `1`, área `Otro`.

---

### Paso 15: Identificar datos incompletos en Excel y documentar hallazgos

**Objetivo:** Analizar la tabla exportada para detectar registros con datos inconsistentes o sospechosos.

**Instrucciones:**

1. En el archivo Excel abierto, inserta una nueva hoja (pestaña **+** en la parte inferior) y nómbrala:

```
Hallazgos
```

2. En la hoja `Hallazgos`, documenta tu análisis en el siguiente formato:

```
Celda A1: ANÁLISIS DE CALIDAD DE DATOS - Formulario de Solicitudes
Celda A3: Registro | Campo           | Problema detectado                    | Severidad
Celda A4: 4       | Nombre           | Nombre incompleto: "Ana M."           | Alta
Celda A5: 4       | Área             | Área genérica: "Otro"                 | Media
Celda A6: 4       | Periodo          | Fecha fuera de rango: 01/01/2020      | Alta
Celda A7: 4       | Monto            | Monto sospechosamente bajo: $1        | Alta
Celda A8: 4       | Tipo             | Tipo genérico: "Otro"                 | Media
Celda A10: Total de registros: 4
Celda A11: Registros con problemas: 1 (25%)
Celda A12: Registros limpios: 3 (75%)
```

3. Guarda el archivo.

**Resultado esperado:** Una hoja de hallazgos que documenta 5 problemas en 1 registro, con un resumen cuantitativo de la calidad de los datos.

**Verificación:** La hoja `Hallazgos` contiene al menos 5 problemas identificados y el porcentaje de registros con problemas (25%).

---

### Paso 16: Crear una tabla dinámica básica en Excel

**Objetivo:** Demostrar que los datos exportados permiten generar reportes analíticos.

**Instrucciones:**

1. Regresa a la hoja principal con los datos del formulario.
2. Selecciona todo el rango de datos (incluyendo encabezados) con `Ctrl+A` o selección manual.
3. Ve a **Insertar** → **Tabla dinámica**.
4. Acepta la ubicación predeterminada (nueva hoja o misma hoja).
5. Configura la tabla dinámica:

```
Configuración de la tabla dinámica:
  Filas:    Tipo de solicitud
  Valores:  Monto solicitado (en pesos, sin símbolos) → Suma
```

6. La tabla dinámica resultante debe mostrar:

```
Tipo de solicitud | Suma de Monto
------------------|---------------
Anticipo          |    12000
Compra            |     3200
Otro              |        1
Reembolso         |     4500
Total general     |    19701
```

**Resultado esperado:** Tabla dinámica funcional que agrupa los montos por tipo de solicitud.

**Verificación:** Los totales coinciden con los montos ingresados en las respuestas de prueba. El valor `1` del tipo "Otro" confirma visualmente el dato atípico.

---

### Paso 17: Conectar a Power BI (demostración)

**Objetivo:** Demostrar que el archivo Excel exportado puede servir como fuente de datos para un reporte en Power BI.

**Instrucciones:**

> **Opción A — Power BI Desktop** (si está disponible en el equipo del participante o del instructor):

1. Abre Power BI Desktop (versión 2.128.751.0).
2. Haz clic en **Obtener datos** → **Excel**.
3. Navega al archivo Excel exportado desde Forms (ubicado en `/CierreOperativo/Semana1/` en OneDrive o en la carpeta de descargas).
4. Selecciona la tabla de datos y haz clic en **Cargar**.
5. En el panel de visualizaciones, selecciona **Gráfico de barras agrupadas**.
6. Arrastra `Tipo de solicitud` al eje Y y `Monto solicitado` al eje X.

```
Visualización esperada en Power BI:
  Gráfico de barras horizontales:
    Anticipo    ████████████ 12,000
    Reembolso   ████████     4,500
    Compra      ██████       3,200
    Otro        █            1
```

> **Opción B — Power BI Service** (alternativa en la nube):

1. Navega a `https://app.powerbi.com` e inicia sesión.
2. Haz clic en **+ Nuevo** → **Cargar un archivo** → selecciona el Excel desde OneDrive.
3. Crea un informe nuevo y agrega una visualización de barras con los mismos campos.

> **Opción C — Solo tabla dinámica** (si Power BI no está disponible):

Si ni Power BI Desktop ni Power BI Service están disponibles, la tabla dinámica creada en el Paso 16 constituye la alternativa mínima aceptable. Documenta en la hoja `Hallazgos`:

```
Celda A14: Nota: Demostración de reporte realizada con tabla dinámica en Excel
           (Power BI no disponible en este equipo).
```

**Resultado esperado:** Un gráfico de barras (en Power BI) o una tabla dinámica (en Excel) que muestra la distribución de montos por tipo de solicitud.

**Verificación:** La visualización muestra correctamente las 4 categorías de tipo de solicitud con sus montos correspondientes.

---

### Paso 18: Guardar el Excel en la biblioteca SharePoint

**Objetivo:** Almacenar el archivo de resultados en la biblioteca `Documentos-CierreOperativo` con los metadatos correspondientes, integrando el artefacto con el repositorio del curso.

**Instrucciones:**

1. Descarga o guarda una copia del archivo Excel con el nombre:

```
Resultados_Solicitudes_CierreMensual_Abr2025.xlsx
```

> Ajusta el mes/año según lo indicado por el instructor.

2. Navega a `https://[tenant].sharepoint.com/sites/CierreOperativo-Practica`.
3. Abre la biblioteca **Documentos-CierreOperativo**.
4. Sube el archivo Excel.
5. Edita los metadatos del archivo recién subido:

```
Periodo:        01/04/2025  (o el mes indicado por el instructor)
TipoDocumento:  Control
Estado:         En revisión
Responsable:    [Tu nombre]
```

**Resultado esperado:** El archivo aparece en la biblioteca SharePoint con los metadatos correctamente asignados.

**Verificación:** Aplica la vista **Por estado** creada en la Práctica 4. El archivo NO debe aparecer en esta vista (porque su estado es "En revisión", no "Vigente"). Cambia a la vista "Todos los documentos" para confirmar que el archivo está presente.

---

### Paso 19: Compartir el reporte en el canal de Teams

**Objetivo:** Publicar el resultado del análisis en el canal `Informe-Mensual` del equipo de Teams, cerrando el ciclo de integración entre herramientas.

**Instrucciones:**

1. Abre Microsoft Teams (escritorio o `https://teams.microsoft.com`).
2. Navega al equipo **CierreOperativo-[Apellido]** → canal **Informe-Mensual**.
3. Inicia una nueva publicación con el siguiente contenido:

```
Asunto: Resultados del formulario de solicitudes - Cierre Mensual [Mes/Año]

Cuerpo:
Se completó la captura estandarizada de solicitudes administrativo-financieras.

📊 Resumen:
- Total de registros: 4
- Registros limpios: 3 (75%)
- Registros con inconsistencias: 1 (25%)
- Monto total solicitado: $19,701

📎 El archivo de resultados está disponible en la biblioteca
   Documentos-CierreOperativo de SharePoint.

🔗 Enlace al formulario: [pegar enlace de compartir del formulario]
```

4. Para obtener el enlace del formulario: regresa a Forms, haz clic en **Recopilar respuestas** (botón **Enviar** en la barra superior) y copia el enlace corto.
5. Publica el mensaje en el canal.

**Resultado esperado:** Mensaje publicado en el canal `Informe-Mensual` con el resumen y el enlace al formulario.

**Verificación:** El mensaje es visible para todos los miembros del equipo. El enlace al formulario es funcional (al hacer clic, abre el formulario).

## Validación y Pruebas

Completa la siguiente lista de verificación para confirmar que todos los objetivos de la práctica se cumplieron:

| # | Criterio de validación | Evidencia requerida | ¿Cumple? |
|---|---|---|---|
| 1 | Se diagnosticaron los campos faltantes en las 3 solicitudes de ejemplo | Tabla de diagnóstico del Paso 1 con al menos 5 campos faltantes por solicitud | ☐ |
| 2 | El formulario tiene 7 preguntas con los tipos correctos | Vista previa del formulario muestra: 2 texto, 2 opción, 1 fecha, 1 texto con restricción numérica, 1 carga de archivo | ☐ |
| 3 | Las validaciones funcionan correctamente | La Respuesta 4 fue bloqueada: campos obligatorios vacíos y monto no numérico rechazado | ☐ |
| 4 | Se registraron al menos 4 respuestas exitosas | Pestaña Respuestas de Forms muestra contador ≥ 4 | ☐ |
| 5 | El Excel exportado tiene la estructura correcta | Archivo con 4+ filas de datos y columnas correspondientes a cada pregunta del formulario | ☐ |
| 6 | Se identificaron datos inconsistentes en Excel | Hoja `Hallazgos` documenta al menos 5 problemas en el registro de "Ana M." | ☐ |
| 7 | Se generó un reporte analítico | Tabla dinámica en Excel o gráfico de barras en Power BI mostrando montos por tipo de solicitud | ☐ |
| 8 | El archivo se almacenó en SharePoint con metadatos | Archivo visible en biblioteca `Documentos-CierreOperativo` con Periodo, TipoDocumento, Estado y Responsable | ☐ |
| 9 | Se publicó el resumen en Teams | Mensaje en canal `Informe-Mensual` con resumen cuantitativo y enlace al formulario | ☐ |

**Caso adverso (validación de limitaciones):**

10. Abre el formulario en vista previa e intenta ingresar en el campo **Monto solicitado** el siguiente texto diseñado para probar los límites de la validación:

```
99999999999999999999
```

Verifica el comportamiento: Forms acepta números muy grandes porque la validación solo exige "mayor que 0". Documenta en la hoja `Hallazgos` esta limitación:

```
Celda A16: LIMITACIÓN IDENTIFICADA: El formulario no tiene validación de monto
           máximo. Un usuario podría ingresar montos irrealmente altos sin que
           Forms lo impida. Recomendación: agregar validación "Menor o igual que"
           con un tope razonable (ej. 1,000,000) o implementar revisión manual
           posterior en el flujo de aprobación.
```

> Esta verificación demuestra que las validaciones de Forms son útiles pero no suficientes por sí solas; el análisis posterior en Excel o Power BI sigue siendo necesario para detectar anomalías que las reglas básicas no cubren.

## Solución de Problemas

**Problema 1: La opción "Carga de archivos" no aparece al agregar una nueva pregunta**

- **Síntoma:** Al hacer clic en **+ Agregar nuevo**, no se muestra el tipo de pregunta "Carga de archivos" entre las opciones disponibles.
- **Causa:** El administrador del tenant de Microsoft 365 ha deshabilitado la carga de archivos en Forms por políticas de seguridad o almacenamiento. Esta configuración se gestiona desde el Centro de administración de Microsoft 365 → Configuración → Servicios → Microsoft Forms.
- **Solución:** Sustituir la pregunta de carga de archivo por una pregunta de tipo **Texto** con la instrucción: `"Pegue aquí el enlace al documento de soporte almacenado en OneDrive o SharePoint"`. Marcarla como no obligatoria. Esta alternativa mantiene la trazabilidad del soporte documental sin requerir la carga directa. Si es necesario habilitar la función, escalar al administrador de TI con al menos 3 días hábiles de antelación.

**Problema 2: Al hacer clic en "Abrir en Excel", el archivo se descarga pero no contiene datos o muestra solo encabezados**

- **Síntoma:** El archivo `.xlsx` descargado desde la pestaña Respuestas de Forms se abre en Excel pero solo muestra la fila de encabezados sin filas de datos, a pesar de que el contador de respuestas en Forms indica 4 o más respuestas.
- **Causa:** Las respuestas fueron registradas en modo **Vista previa** del editor (no como envíos reales). Las respuestas de vista previa se muestran en el resumen visual de Forms pero pueden no exportarse al archivo Excel en todos los casos, dependiendo de la versión del servicio.
- **Solución:** Copiar el enlace de compartir del formulario (botón **Enviar** → copiar enlace), abrirlo en una pestaña nueva del navegador (o en una ventana de incógnito con sesión institucional activa) y registrar las respuestas desde allí como un respondedor real. Verificar después que el contador de respuestas se actualiza y repetir la exportación a Excel. Las respuestas enviadas desde el enlace compartido siempre se incluyen en la exportación.

## Limpieza

Al finalizar la práctica, realiza las siguientes acciones de orden:

1. **No elimines el formulario** — será referenciado en la comprobación final del curso.
2. **Desactiva las notificaciones por correo** si no deseas seguir recibiendo avisos: ve a Configuración del formulario → desmarca "Notificación de cada respuesta por correo electrónico".
3. **Cierra las pestañas** de Forms, Excel Online y Power BI que hayas abierto durante la práctica.
4. **Verifica** que el archivo `Resultados_Solicitudes_CierreMensual_Abr2025.xlsx` permanece en la biblioteca SharePoint `Documentos-CierreOperativo` con sus metadatos correctos.

> **No desactives** la opción "Aceptar respuestas" del formulario todavía; el instructor puede solicitar respuestas adicionales en sesiones posteriores.

## Resumen

En esta práctica completaste el ciclo integral del cierre operativo mensual:

- **Diagnosticaste** el problema de origen: solicitudes con datos faltantes, ambiguos o en formato libre que generan reprocesos.
- **Diseñaste** un formulario estandarizado en Microsoft Forms con 7 campos tipificados (texto, opción, fecha, número, archivo) y validaciones nativas que previenen errores de captura en el punto de entrada.
- **Verificaste** que las validaciones bloquean datos inválidos (campos vacíos, montos no numéricos) pero también identificaste sus limitaciones (no detectan montos irrealmente altos ni nombres incompletos que cumplan el mínimo técnico).
- **Exportaste** los resultados a Excel y realizaste análisis de calidad de datos, documentando hallazgos de inconsistencia.
- **Demostraste** la conexión con Power BI (o tabla dinámica como alternativa) para generar reportes analíticos a partir de los datos capturados.
- **Integraste** el artefacto con la biblioteca SharePoint (Práctica 4) y el equipo de Teams (Práctica 3), cerrando el flujo de trabajo colaborativo del curso.

**Temas cubiertos del Módulo 5:**

| Tema | Cobertura en esta práctica |
|---|---|
| 5.1 Formularios, encuestas y evaluaciones | Pasos 2–11: creación del formulario, tipos de pregunta, validaciones, configuración |
| 5.2 Recopilación, revisión y uso de resultados | Pasos 12–19: registro de respuestas, resumen en Forms, exportación a Excel, análisis, Power BI, integración |

**Recursos adicionales:**

- Documentación oficial de Microsoft Forms: `https://support.microsoft.com/es-es/forms`
- Tipos de preguntas en Microsoft Forms: `https://support.microsoft.com/es-es/office/elegir-un-tipo-de-pregunta-en-microsoft-forms-1a6a5f8d-7c4b-4e2a-9c5e-0e7c2d4b3f1a`
- Obtener datos en Power BI Desktop desde Excel: `https://learn.microsoft.com/es-es/power-bi/connect-data/desktop-connect-excel`
