<img src="assets/LogoNetec.png" alt="logo" width="300"/>

# Setup Guide General

## Productividad Digital con Microsoft 365

| Control documental | Información |
|---|---|
| Clave del curso | PROD_DIG_M365 (Priv) |
| Versión del documento | 1.0 |
| Estado | BORRADOR: revisión documental completa; pendiente de validación en el tenant del cliente |
| Instructor responsable | Por asignar por Netec |
| Fecha de elaboración | 2026-11-13 |
| Fecha de última validación | 2026-11-13 (revisión de enlaces, recursos y coherencia con el temario) |
| Repositorio de laboratorios | https://github.com/Netec-Mx/PROD-DIG-M365-Priv |
| Rama y revisión analizada | `changes_course` (basada en `main`, commit `43eff30`) |
| Alcance revisado | 8 capítulos, 8 prácticas, 9 archivos de recursos, 9 diagramas, README principal y Setup Guide |
| Modalidad del entorno | Web (Microsoft 365 institucional del cliente) |

[Inicio](README.md)

# Objetivo

Preparar, para cada participante, una cuenta institucional de Microsoft 365 con acceso a OneDrive, Word, Excel y PowerPoint para la web, Teams, SharePoint, Forms, Planner, Power Automate (conectores estándar) y Copilot Chat básico. El instructor prepara además un sitio de práctica compartido, `CierreOperativo-Practica`, con los archivos de entrada de las misiones 4, 6 y 8. El entorno se considera listo cuando se aprueban las validaciones de la sección [Validación del Entorno](#validacion-entorno) con la cuenta de un participante.

# Requisitos de Hardware

| Recurso | Mínimo requerido | Recomendado | Observaciones |
|---|---|---|---|
| Procesador y arquitectura | 64 bits, 2 núcleos | 4 núcleos | Todas las aplicaciones se usan en el navegador |
| Memoria RAM | 8 GB | 16 GB | Teams, el navegador y Excel abiertos a la vez |
| Espacio libre | 2 GB | 5 GB | Descarga de recursos y, si se usa, Power BI Desktop |
| Pantalla | 1366 × 768 | 1920 × 1080 o dos monitores | Curso virtual: una pantalla para la sesión y otra para la práctica |
| Conectividad | 10 Mbps | 25 Mbps | Videoconferencia y aplicaciones en la nube al mismo tiempo |
| Audio | Audífonos con micrófono | — | Curso virtual sincrónico |

# Sistemas Operativos Compatibles

| Sistema operativo | Edición y versión | Arquitectura | Condición de soporte o validación |
|---|---|---|---|
| Windows | 10 u 11 | x64 | Plataforma base; compatible según fabricante; pendiente de validar en el tenant del cliente |
| macOS | 13 o posterior | Apple silicon o Intel | Compatible según fabricante para las aplicaciones web; Power BI Desktop no está disponible |

La plataforma base es Windows con Microsoft Edge. En macOS se completan todas las prácticas en el navegador; la demostración opcional de Power BI (Práctica 5) se hace con el servicio web de Power BI o en el equipo del instructor.

# Software Requerido

| Componente | Edición y versión requerida | Arquitectura | Obligatorio u opcional | Fuente oficial |
|---|---|---|---|---|
| Microsoft Edge o Google Chrome | Versión estable vigente | x64 | Obligatorio | [microsoft.com/edge](https://www.microsoft.com/es-es/edge/download) |
| OneDrive, Word, Excel y PowerPoint para la web | Servicio administrado (Microsoft 365) | N/A | Obligatorio (prácticas 1, 2, 3, 5 y 8) | [m365.cloud.microsoft](https://m365.cloud.microsoft) |
| Microsoft Teams | Servicio administrado (escritorio o web) | x64 | Obligatorio (prácticas 3, 5, 6 y 8) | [teams.microsoft.com](https://teams.microsoft.com) |
| SharePoint Online | Servicio administrado | N/A | Obligatorio (prácticas 4, 5, 6, 7 y 8) | [m365.cloud.microsoft](https://m365.cloud.microsoft) |
| Microsoft Forms | Servicio administrado | N/A | Obligatorio (Práctica 5) | [forms.office.com](https://forms.office.com) |
| Microsoft Planner | Servicio administrado | N/A | Obligatorio (prácticas 6 y 7) | [planner.cloud.microsoft](https://planner.cloud.microsoft) |
| Power Automate | Servicio administrado; solo conectores estándar | N/A | Obligatorio (Práctica 7) | [make.powerautomate.com](https://make.powerautomate.com) |
| Microsoft 365 Copilot Chat (Copilot Chat básico) | Servicio administrado con protección de datos empresariales; no requiere licencia de Microsoft 365 Copilot | N/A | Obligatorio (prácticas 1, 2, 3 y 8) | [m365.cloud.microsoft/chat](https://m365.cloud.microsoft/chat) |
| Power BI Desktop o servicio Power BI | Versión vigente | x64 | Opcional (demostración de la Práctica 5) | [Descarga de Power BI Desktop](https://www.microsoft.com/es-es/download/details.aspx?id=58494) |

Los servicios de Microsoft 365 no tienen una versión fijable. Registrar en el [Registro de validación](#registro-validacion) la fecha de la prueba, la edición visible y cualquier restricción del tenant.

# Herramientas y Dependencias

## Paquetes, frameworks y componentes adicionales

| Dependencia | Versión o restricción | Componente que la necesita | Método de instalación o habilitación |
|---|---|---|---|
| Conectores estándar: Microsoft Planner, SharePoint y Office 365 Outlook | Incluidos en Microsoft 365 | Práctica 7 | Disponibles en Power Automate; deben estar permitidos por la directiva de datos (DLP) del tenant |
| Desencadenador *Cuando se completa una tarea* (Planner) | Requiere un plan asociado a un grupo de Microsoft 365 | Práctica 7 | El plan de la Práctica 6 se crea en el grupo `CierreOperativo-Practica` |
| Carga de archivos en Forms | Solo con formularios restringidos a la organización | Práctica 5 (pregunta «Documento de soporte») | Configuración del formulario |
| Archivos de entrada | Versión de la rama `changes_course` | Prácticas 1 a 6 y 8 | Carpetas `CapituloNN/recursos/` |

## Licencias, cuentas y permisos

| Recurso o servicio | Licencia o suscripción | Cuenta o rol requerido | Permiso mínimo | Responsable de habilitación |
|---|---|---|---|---|
| Microsoft 365 | Licencia del cliente con Teams, SharePoint, Forms, Planner y Power Automate | Cuenta institucional | Usuario | TI del cliente |
| Sitio `CierreOperativo-Practica` (grupo de Microsoft 365) | Incluida | Participante | **Miembro** del grupo (crear bibliotecas, listas, columnas y planes) | Instructor o TI |
| Equipo de Teams personal `CierreOperativo-[Apellido]` | Incluida | Participante | Crear equipos, o equipo creado por el instructor con el participante como propietario | TI del cliente o instructor |
| Power Automate | Incluido en Microsoft 365 (conectores estándar) | Cuenta institucional | Crear flujos de nube | TI del cliente |
| Copilot Chat básico | Incluido para cuentas con Entra ID | Cuenta institucional | Usuario | TI del cliente |

Los accesos se entregan por el canal institucional del cliente. No registrar contraseñas, códigos MFA ni tokens en el repositorio ni en los entregables.

# Instalación y Configuración

## 1. Obtener los materiales

- Repositorio autorizado: https://github.com/Netec-Mx/PROD-DIG-M365-Priv (botón **Code > Download ZIP**) o paquete ZIP del instructor.
- Revisión que se utilizará: rama `main` después de integrar `changes_course`.
- Directorio de trabajo del participante: OneDrive, carpeta `CierreOperativo/Semana1/` (se crea en la Práctica 1).
- Archivos de entrada distribuidos: `Capitulo01/recursos` a `Capitulo06/recursos` y `Capitulo08/recursos`. Los archivos de las prácticas 4, 6 y 8 los publica el instructor en el sitio de práctica (ver el paso 2).

## 2. Instalar o habilitar los componentes

### Cuenta y aplicaciones

1. Iniciar sesión en [m365.cloud.microsoft](https://m365.cloud.microsoft) con una cuenta de participante.
2. Abrir **Aplicaciones** y confirmar OneDrive, Word, Excel, PowerPoint, Teams, SharePoint, Forms, Planner y Power Automate.
3. Abrir [Copilot Chat](https://m365.cloud.microsoft/chat) y confirmar el indicador de protección de datos empresariales.

**Plataforma y terminal:** cualquier sistema operativo compatible, navegador web.

**Resultado esperado:** todas las aplicaciones abren con la cuenta institucional y Copilot Chat muestra la protección de datos empresariales.

### Sitio de práctica `CierreOperativo-Practica` (instructor, antes del curso)

1. En SharePoint, seleccionar **+ Crear sitio** > **Sitio de grupo** con el nombre `CierreOperativo-Practica` y privacidad **Privada**. Agregar a todos los participantes como **miembros**.
2. En la biblioteca **Documentos** del sitio, cargar los 10 archivos de [Archivos_Problema_P4.zip](Capitulo04/recursos/Archivos_Problema_P4.zip).
3. Abrir `Informe_CierreOp_Abr2025_v1.xlsx`, hacer un cambio menor y guardar; repetir dos veces para que el historial tenga al menos 3 versiones.
4. Para cada participante, cargar una copia `Notas_reunion_borrador_[Apellido].docx` y, en **Administrar acceso**, conceder **Puede editar** a **Todos excepto usuarios externos** (escenario de permisos excesivos de la Práctica 4).
5. Crear la biblioteca `CierreMensual_Practicas` y cargar [Escenario_CierreMensual_P6.pdf](Capitulo06/recursos/Escenario_CierreMensual_P6.pdf) y [Expediente_CierreMensual_P8.zip](Capitulo08/recursos/Expediente_CierreMensual_P8.zip). Dejar a los participantes con permiso de lectura en esa biblioteca.

**Resultado esperado:** el sitio tiene la biblioteca **Documentos** con 10 archivos más una copia de notas por participante, y la biblioteca `CierreMensual_Practicas` con 2 archivos.

### Equipos de Teams personales

1. Con una cuenta de participante, comprobar si se puede crear un equipo: **Teams > Equipos > + > Crear equipo**.
2. Si no se puede, el instructor o TI crea un equipo privado por participante con el nombre `CierreOperativo-[Apellido]` y lo agrega como **propietario**.

**Resultado esperado:** cada participante puede crear su equipo en la Práctica 3 o ya es propietario de uno.

### Power Automate

1. Con una cuenta de participante, abrir [make.powerautomate.com](https://make.powerautomate.com) > **+ Crear** > **Flujo de nube automatizado**.
2. Buscar el desencadenador **Cuando se completa una tarea** (Microsoft Planner).

**Resultado esperado:** el desencadenador aparece sin la etiqueta **Premium** y la directiva de datos permite combinar Planner, SharePoint y Office 365 Outlook.

## 3. Preparar archivos de configuración

No se requieren archivos de configuración.

# Variables de Entorno

No se requieren variables de entorno.

# Configuración Base para los Laboratorios

## Parámetros comunes

| Parámetro | Valor o convención | Observaciones |
|---|---|---|
| Raíz de trabajo | OneDrive: `CierreOperativo/Semana1/` | Se crea en la Práctica 1 y se usa en todas |
| Sitio de práctica | `https://[tenant].sharepoint.com/sites/CierreOperativo-Practica` | Compartido; `[tenant]` es el nombre del tenant del cliente |
| Biblioteca del participante | `Documentos-CierreOperativo-[Apellido]` | Se crea en la Práctica 4 y se usa en las prácticas 5 y 8 |
| Equipo de Teams | `CierreOperativo-[Apellido]` | Se crea en la Práctica 3 |
| Plan de Planner | `CierreMensual_[Apellido]` en el grupo `CierreOperativo-Practica` | Práctica 6; disparador de la Práctica 7 |
| Lista de SharePoint | `Registro_Cierre_[Apellido]` | Práctica 7 |
| Periodo del caso | Cierre operativo de abril 2025 | Igual en las 8 prácticas |
| Nombres de archivo | `Nombre_[Apellido].ext` | Sin espacios ni acentos |

## Estructura de carpetas

```text
OneDrive\CierreOperativo\Semana1\
├── PlanSemanal, ListaVerificacion, AnalisisHerramientas, Microflujo (prácticas 1 y 2)
├── Evidencias de las prácticas 6 y 7 (.png)
└── P8_Auditoria\   Expediente de la Práctica 8
```

## Recursos compartidos

| Recurso | Nombre o identificador | Estructura o configuración base | Responsable de creación |
|---|---|---|---|
| Sitio y grupo de Microsoft 365 | `CierreOperativo-Practica` | Privado; participantes como miembros | Instructor o TI |
| Biblioteca | `Documentos` (predeterminada) | 10 archivos problema de la Práctica 4, 3 versiones del informe v1 y una copia de notas con permisos abiertos por participante | Instructor |
| Biblioteca | `CierreMensual_Practicas` | `Escenario_CierreMensual_P6.pdf` y `Expediente_CierreMensual_P8.zip`; lectura para participantes | Instructor |
| Bibliotecas, listas y planes del participante | `Documentos-CierreOperativo-[Apellido]`, `Registro_Cierre_[Apellido]`, `CierreMensual_[Apellido]` | Las crea cada participante en el sitio; el sufijo `[Apellido]` evita conflictos | Participante |

## Correcciones de coherencia

| Inconsistencia o dependencia omitida | Configuración unificada | Ajuste necesario en las copias de trabajo |
|---|---|---|
| Las prácticas usaban meses distintos (junio, marzo y abril de 2025) aunque el temario pide un mismo caso | Todas las misiones usan el cierre de abril de 2025 | Aplicado en las prácticas 1, 4 y 5 |
| Todos los participantes creaban la biblioteca `Documentos-CierreOperativo` en el mismo sitio | Biblioteca `Documentos-CierreOperativo-[Apellido]` | Aplicado en las prácticas 3, 4, 5 y 8 |
| Los participantes corregían el permiso de un mismo archivo de notas | Una copia `Notas_reunion_borrador_[Apellido].docx` por participante | Preparación del instructor (paso 2) |
| La Práctica 6 marcaba como atrasadas solo 4 actividades, pero otras 3 también vencían antes del 30 de abril; la actividad 12 vencía antes que su dependencia | Fechas ajustadas: atrasadas 1, 2, 3 y 9; la actividad 12 vence después de la 10 | Aplicado en la Práctica 6 y su archivo de escenario |
| La Práctica 7 proponía un desencadenador de cambio de cubo que el conector estándar de Planner no ofrece | Registro y notificación en un solo flujo con *Cuando se completa una tarea* | Aplicado en la Práctica 7 |
| Enlaces a servicios de consumo (`onedrive.live.com`, `copilot.microsoft.com`) y 5 enlaces de ayuda inexistentes | `m365.cloud.microsoft`, `m365.cloud.microsoft/chat` y enlaces oficiales vigentes | Aplicado en las 8 prácticas |

# Servicios Externos Requeridos

| Servicio | URL, endpoint o región | Uso | Acceso requerido |
|---|---|---|---|
| Microsoft 365 | [m365.cloud.microsoft](https://m365.cloud.microsoft) | Todas las prácticas | Cuenta institucional |
| Copilot Chat | [m365.cloud.microsoft/chat](https://m365.cloud.microsoft/chat) | Prácticas 1, 2, 3 y 8 | Cuenta institucional |
| Power Automate | [make.powerautomate.com](https://make.powerautomate.com) | Práctica 7 | Cuenta institucional |
| GitHub | [github.com](https://github.com) | Descarga de materiales | Lectura del repositorio |

## Configuración de red

| Origen | Destino | Protocolo y puerto | Sentido | Condición |
|---|---|---|---|---|
| Equipo del participante | Puntos de conexión de Microsoft 365 y github.com | HTTPS 443 | Saliente | Según la [lista oficial de URL y direcciones IP de Microsoft 365](https://learn.microsoft.com/es-es/microsoft-365/enterprise/urls-and-ip-address-ranges) |

# Creación de Entornos / Máquinas Virtuales / Emuladores

No aplica. El curso se realiza en el tenant de Microsoft 365 del cliente.

<a id="validacion-entorno"></a>

# Validación del Entorno

| ID | Componente o capacidad | Procedimiento | Resultado esperado | Evidencia mínima |
|---|---|---|---|---|
| V-01 | Cuenta | Iniciar sesión en m365.cloud.microsoft con una cuenta de participante | Aparecen las aplicaciones del curso | Captura |
| V-02 | Copilot Chat | Abrir Copilot Chat y pegar la lista de la Práctica 1 | Responde con la protección de datos empresariales visible | Captura |
| V-03 | Teams | Crear o abrir el equipo `CierreOperativo-[Apellido]` y agregar un canal | El canal se crea | Captura |
| V-04 | Sitio de práctica | Abrir `CierreOperativo-Practica` como participante y crear una biblioteca de prueba con una columna de elección | Biblioteca creada; los 10 archivos de **Documentos** son visibles | Captura |
| V-05 | Historial de versiones | Abrir el historial de `Informe_CierreOp_Abr2025_v1.xlsx` | 3 o más versiones | Captura |
| V-06 | Forms | Crear un formulario con una pregunta obligatoria y otra de carga de archivos | Formulario creado; la carga de archivos está disponible | Captura |
| V-07 | Planner | Crear un plan en el grupo `CierreOperativo-Practica` | Plan creado en el grupo | Captura |
| V-08 | Power Automate | Crear un flujo *Cuando se completa una tarea* > *Crear elemento* y completar una tarea de prueba | Elemento creado en una lista | Historial de ejecuciones |

**Criterio de entorno listo:** V-01 a V-08 aprobadas con una cuenta de participante. Si V-03 falla por permisos, el instructor crea los equipos antes del curso. Si V-06 no permite carga de archivos, el participante omite la pregunta «Documento de soporte» de la Práctica 5.

# Comandos de Verificación

No aplica. El curso se valida en las interfaces web de Microsoft 365 con los procedimientos V-01 a V-08.

# Troubleshooting

| Síntoma | Causa probable | Comprobación | Corrección | Validación posterior |
|---|---|---|---|---|
| No se puede crear un equipo | Creación de grupos restringida | Mensaje de Teams | El instructor o TI crea los equipos | V-03 |
| El participante no puede crear bibliotecas en el sitio | Es visitante, no miembro | **Configuración** > **Permisos del sitio** | Agregarlo como miembro del grupo | V-04 |
| Copilot Chat sin protección de datos empresariales | Sesión con cuenta personal | Cuenta en la esquina superior | Cerrar sesión e iniciar con la cuenta institucional | V-02 |
| El desencadenador de Planner no muestra el plan | El plan no está en un grupo o el participante no es miembro | **Configuración del plan** en Planner | Crear el plan en `CierreOperativo-Practica` | V-07, V-08 |
| Power Automate marca un conector como Premium o bloqueado | Licencia o directiva de datos | Mensaje del diseñador | Usar solo Planner, SharePoint y Outlook; solicitar a TI ajustar la directiva | V-08 |

# Checklist Final

- [ ] Cuentas de participante con todas las aplicaciones del curso.
- [ ] Copilot Chat con protección de datos empresariales.
- [ ] Sitio `CierreOperativo-Practica` con los participantes como miembros.
- [ ] Biblioteca **Documentos** con los archivos de la Práctica 4, 3 versiones del informe v1 y una copia de notas por participante.
- [ ] Biblioteca `CierreMensual_Practicas` con los archivos de las prácticas 6 y 8.
- [ ] Permiso para crear equipos o equipos creados por el instructor.
- [ ] Power Automate con conectores estándar permitidos.
- [ ] Validaciones V-01 a V-08 aprobadas y registradas.

# Resumen

Para iniciar el curso, cada participante necesita una cuenta institucional de Microsoft 365 con OneDrive, aplicaciones web de Office, Teams, SharePoint, Forms, Planner, Power Automate con conectores estándar y Copilot Chat básico, y ser miembro del sitio `CierreOperativo-Practica`, que el instructor prepara con los archivos de las prácticas 4, 6 y 8. No se instala software adicional; Power BI Desktop es opcional.

<a id="registro-validacion"></a>

## Registro de validación

| Fecha | Responsable | Plataforma o entorno probado | Resultado | Limitaciones o acciones pendientes |
|---|---|---|---|---|
| 2026-11-13 | Desarrollo de contenido Netec | Revisión documental, enlaces, recursos y coherencia con el temario | APTO para publicación del repositorio | No se validó en el tenant del cliente. Pendiente: V-01 a V-08 con una cuenta de participante |

## Referencias oficiales

| Documento o recurso | URL | Fecha de consulta |
|---|---|---|
| Microsoft 365 Copilot Chat | https://learn.microsoft.com/es-es/copilot/overview | 2026-11-13 |
| Protección de datos empresariales | https://learn.microsoft.com/es-es/copilot/privacy-and-protections | 2026-11-13 |
| Conector de Planner | https://learn.microsoft.com/es-es/connectors/planner/ | 2026-11-13 |
| Niveles de permisos de SharePoint | https://learn.microsoft.com/es-es/sharepoint/understanding-permission-levels | 2026-11-13 |
| Control de versiones en SharePoint | https://support.microsoft.com/es-es/office/habilitar-y-configurar-el-control-de-versiones-en-una-lista-o-biblioteca-1555d642-23ee-446a-990a-bcab618c7a37 | 2026-11-13 |
| URL e intervalos de IP de Microsoft 365 | https://learn.microsoft.com/es-es/microsoft-365/enterprise/urls-and-ip-address-ranges | 2026-11-13 |

[Inicio](README.md)
