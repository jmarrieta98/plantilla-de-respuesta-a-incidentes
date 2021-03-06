# Plan de respuesta a Incidentes para {{COMPANY_NAME}}

Autores: {{AUTHOR_NAME}},

Autores: {{AUTHOR_NAME_2}}, {{AUTHOR_EMAIL}}

Revisión {{REVISION_NUMBER}}, Publicado {{RELEASE_DATE}}

Este plan de respuesta a incidentes se basa en el plan conciso, directivo, específico, flexible y gratuito disponible en [Github](https://github.com/counteractive/incident-response-plan-template) de Counteractive Security y comentado en [www.counteractive.net](https://www.counteractive.net/posts/an-ir-plan-you-will-use/)

Fue revisado por última vez el {{REVIEW_DATE}}. Se probó por última vez {{TEST_DATE}}.

`TODO: Personalice esta plantilla de plan para su organización utilizando las instrucciones en https://github.com/counteractive/incident-response-plan-template. Para obtener servicios de respuesta a incidentes, o ayuda para personalizar, implementar o probar su plan, póngase en contacto con nosotros en contact@counteractive.net o en el (888) 925-5765.`

# Evaluar

1. **Mantenga la calma y la profesionalidad.**
2. Reúna la información pertinente, _e.j._, alarmas, eventos, datos, suposiciones, intuiciones (**observe**).
3. Considerar las categorías de impacto, a continuación (**orientar**), y determinar si hay un posible incidente (**decidir**):
4. Iniciar una respuesta si hay un incidente (**actuar**). En caso de duda, inicie una respuesta. El Incident Commander y el equipo de respuesta pueden ajustarse tras la investigación y la revisión.

## Evaluar el Impacto Funcional

¿Cuál es el impacto directo o probable en su misión? (_e.j._, operaciones comerciales, empleados, clientes, usuarios)

* Degradación o fracaso de la misión/negocio: **incidente!**
* Ninguno: evalúe el impacto de la información.

## Evaluar el Impacto de la Información

¿Cuál es el impacto directo o probable en su información/datos, especialmente en los que se refiere a los sensibles? (_e.j_, PII (Información de Identificación Personal), datos de propiedad, financieros o sanitarios)

* Información a la que se ha accedido, tomado, cambiado o borrado: **incidente!**
* Ninguno: gestión a través de canales no relacionados con incidentes (_e.j._, un ticket de soporte).

**Cada miembro del equipo está facultado para iniciar este proceso.** Si ves algo, di algo.

`TODO: Personalizar las categorías/severidades según sea necesario. Este sencillo ejemplo (incidente frente a no incidente) se basa en las categorías de impacto del NIST SP 800-61r2.`

# Iniciar la Respuesta

## Nombrar el Incidente

Cree una [frase simple de dos palabras](http://creativityforyou.com/combomaker.html) para referirse al incidente---un nombre en clave---que se utilizará para el archivo y el canale(s) del incidente. `TODO: Personalizar el procedimiento de nomenclatura de incidentes.`

## Reunir el Equipo de Respuesta

1. Llame al Incident Commander de turno/guardia. `TODO: Añadir lista o procedimiento de llamada del Incident Commander`
2. **No** discuta el incidente fuera del equipo de respuesta a menos que el Incident Commander lo autorice
3. Inicie y/o únase al chat de respuesta en {{RESPONSE_CHAT}}. `TODO: Añadir el procedimiento de lanzamiento del chat de respuesta.`
4. Iniciar y/o unirse a la llamada de respuesta en {{RESPONSE_PHONE}} y/o {{RESPONSE_VTC}}. `TODO: Añadir el procedimiento de lanzamiento de la llamada de respuesta.`
5. Prefiera la llamada de voz, el chat y el intercambio seguro de archivos sobre cualquier otro método.
6. **No** utilizar el correo electrónico principal si es posible.  Si el correo electrónico es necesario, utilícelo con moderación o use {{ALTERNATE_EMAIL}}. Encripte los correos electrónicos cuando cualquier participante esté fuera del dominio {{ORGANIZATION_DOMAIN}}. `TODO: Añadir detalles y procedimiento de correo electrónico alternativo, por ejemplo, Office 365 o GSuite bajo demanda`
7. **No** usar SMS/texto para comunicar el incidente, a menos que sea para decirle a alguien que se mueva a un canal más seguro.
8. Invite a los intervinientes de servicio/guardia a la llamada de respuesta y al chat de respuesta.
    * Invite al equipo de seguridad. `TODO: Añadir lista de contactos del equipo de seguridad o procedimiento.`
    * Invitar a un SME para los equipos y sistemas afectados. `TODO: Añadir lista de contactos de los SME del equipo o procedimiento.`
    * Invitar a las partes interesadas ejecutivas y a los asesores jurídicos lo antes posible, pero dar prioridad a los responsables operativos. `TODO: Añadir una lista de contactos de las partes interesadas ejecutivas o procedimiento.`
9. _OPCIONAL:_ Establecer una sala de colaboración en persona ("sala de guerra") para incidentes complejos o graves. `TODO: Añadir el procedimiento de la sala de colaboración.`

### Referencia: Estructura del Equipo de Respuesta

* Equipo de Mando
  * [Incident Commander](#rol-incident-commander)
  * [Incident Commander-Adjunto](#rol-incident-commander-adjunto)
  * [Escriba](#rol-escriba)
* Equipo de enlace
  * Enlace [interno](#rol-enlace)
  * Enlace externo
* Equipo de operaciones
  * [Expertos en la materia](#rol-experto-en-la-materia-subject-matter-expert-sme) (SME's) para sistemas
  * SME's para equipos/unidades de negocio
  * SME's para Funciones Ejecutivas (_e.j._, Legal, RRHH, Finanzas)

`TODO: Modificar la estructura de roles según sea necesario.`

### Referencia: Información de Contacto del Equipo de Respuesta

Rol del Equipo de Respuesta         | Información de Contacto
----------------------------------- | ---------------------------
Localizador del Incident Commander  | {{INCIDENT_COMMANDER_PAGER_NUMBER}}
url del Incident Commander          | {{INCIDENT_COMMANDER_PAGER_URL}}
Lista de Incident Commander's       | {{INCIDENT_COMMANDER_ROSTER}}
Lista del equipo de Seguridad       | {{SECURITY_TEAM_ROSTER}}
Lista del equipo SME                | {{TEAM_SME_ROSTER}}
Lista de Ejecutivos                 | {{EXECUTIVE_ROSTER}}

`TODO: Personalizar la información de contacto del equipo de respuesta. Incluya los procedimientos de contacto en las listas, que pueden ser estáticas o dinámicas.`

## Establecer el Ritmo de la Batalla

### Realizar la Llamada de Respuesta Inicial

1. Realice la llamada inicial utilizando la [estructura de llamada de respuesta inicial](#referencia-estructura-de-la-llamada-de-respuesta-inicial)
2. Siga las instrucciones del Incident Commander. Si el Incident Commander de turno/guardia no se une a la llamada **dentro de {{INCIDENT_COMMANDER_RESPONSE_SLA}}** y usted es un Incident Commander capacitado, tome el mando de la llamada.
3. Siga las [instrucciones correspondientes a su rol](#roles).
4. Siga la llamada y el chat, y comente según corresponda.  Si no es un SME, filtre las aportaciones a través del SME de su equipo si es posible.
5. **Mantenga la llamada y el chat activos durante todo el incidente para una comunicación basada en eventos.**
6. Programe actualizaciones **cada {{UPDATE_FREQUENCY}}** en el puente activo.

#### Referencia: Estructura de la llamada de respuesta inicial

* Incident Commander (IC): Mi nombre es [NOMBRE], soy el Incident Commander.  He designado a [NOMBRE] como Incident Commander-Adjunto y a [NOMBRE] como Escriba. ¿Quién está en la llamada?
* ESCRIBA: [Toma asistencia]
* IC: [Si falta personal clave] Incident Commander-Adjunto, por favor llame a [PERSONAL_FALTANTE].
* IC: [Hace preguntas para comprender la situación, los síntomas, el alcance, el vector, el impacto y el calendario del informador del incidente, los SME's aplicables para los sistemas y las unidades de negocio]
* SME's: [Responde brevemente a las preguntas del IC].
* IC: [Si se trata de un incidente]:
  * En este momento, el resumen del incidente es el siguiente: [reitera el resumen]. El equipo de investigación estará dirigido por [NOMBRE], el equipo de remediación estará dirigido por [NOMBRE] y el equipo de comunicación estará dirigido por [NOMBRE]. Ellos coordinarán la composición del equipo y me informarán. Los miembros del equipo, por favor, informen a su jefe de equipo correspondiente.
  * ¿Qué medidas de investigación, corrección o comunicación se han tomado ya? [esta debería ser una lista corta, pero tiene que salir ahora]
  * Esta llamada y el chat permanecerán activos y disponibles hasta el cierre del incidente, por favor, utilícelos para todas las comunicaciones relacionadas con el incidente. Proporcione actualizaciones de estado en tiempo real en el chat, si es posible. ¿Hay alguna pregunta o aportación restante? [responde a las preguntas]
  * Líderes de equipo, por favor procedan con sus acciones planeadas. Nos reuniremos de nuevo en [UPDATE_TIME] para discutir el estado. Gracias.
* IC: [Si esto no es un incidente]: En este momento, estos hechos no alcanzan el nivel de un incidente. Me coordinaré directamente con el informador del incidente para las acciones de seguimiento. Gracias por su tiempo.

#### Referencia: Etiqueta de la Llamada

* Únase tanto a la llamada como al chat.
* Mantenga el ruido de fondo al mínimo.
* Mantenga su micrófono silenciado hasta que tenga algo que decir.
* Identifícate cuando te unas a la llamada; di tu nombre y tu función (_e.j._, "Soy el SME del equipo x").
* Habla con claridad.
* Sea directo y objetivo.
* Mantenga conversaciones/discusiones cortas y al grano.
* Comunicar cualquier preocupación al Incident Commander (CI) en la llamada.
* Respetar las limitaciones de tiempo impuestas por el Incident Commander.
* **Utilizar una terminología clara y evitar acrónimos o abreviaturas. La claridad y la precisión son más importantes que la brevedad.**

### Actualización de la Respuesta de la Conducta

* Llevar a cabo actualizaciones programadas utilizando la [estructura de la llamada de actualización de la respuesta](#referencia-estructura-de-la-llamada-de-actualización-de-la-respuesta) cada {{UPDATE_FREQUENCY}} en el puente activo. `TODO: Personalizar la frecuencia de actualización y los scripts; se recomienda no más de dos veces al día.`
* Ajustar la frecuencia según sea necesario.
* Coordinar las actualizaciones independientes (_e.j._, ejecutivas, legales) según sea necesario, pero con la menor frecuencia posible.

#### Referencia: Estructura de la llamada de Actualización de la Respuesta

* INCIDENT COMMANDER (IC): Desde la última actualización programada, el resumen del incidente es el siguiente:
  * [Impacto]
  * [Vector]
  * [Actualización del resumen]
  * [Actualización de la línea de tiempo]
  * IC: Equipo de investigación, por favor proporcione una breve actualización
    * LÍDER DE LA INVESTIGACIÓN: [Actividades de investigación o "nada que informar"]
    * ¿Cuál es su plan de investigación recomendado?
    * ¿Qué acciones de investigación necesitan ser asignadas o aprobadas?  [escuchar, obtener consenso, encargar/aprobar]
  * IC: Equipo de remediación, por favor proporcione una breve actualización
    * LÍDER DE REMEDIACIÓN: [Actividades de remediación o "nada que informar"]
    * ¿Cuál es su estrategia de remediación recomendada?. ¿Objeciones fuertes? [escuchar, obtener el consenso, asignar/aprobar]
    * ¿Qué acciones de remediación necesitan ser asignadas o aprobadas?
  * IC: Equipo de comunicación, por favor, proporcione una breve actualización:
    * LÍDER DE COMUNICACIÓN: [Actividades de comunicación o "nada que informar"]
    * ¿Cuál es su estrategia de comunicación recomendada?. ¿Objeciones fuertes? [escuchar, obtener consenso, encargar/aprobar]
    * ¿Qué acciones de comunicación necesitan ser asignadas o aprobadas?
  * IC: Esta llamada y el chat permanecerán activos y disponibles hasta el cierre del incidente, por favor, utilícelos para todas las comunicaciones relacionadas con el incidente. Si es posible, proporcione actualizaciones del estado en tiempo real en el chat. ¿Hay alguna pregunta o aportación restante? [responde a las preguntas]
  * IC: Líderes de equipo, por favor procedan. Nos reuniremos de nuevo en {{UPDATE_TIME}} para discutir la situación. Gracias.

## Supervisar el Alcance

* Supervisar el alcance de la respuesta para asegurarse de que no excede el ámbito de control del Incident Commander.
* Si un incidente es lo suficientemente complejo y hay suficientes intervinientes, considere la posibilidad de crear subequipos.

### Crear Sub-Equipos

* En la preparación de incidentes complejos, se predefinen tres subequipos: Investigación, Remediación y Comunicación, generalmente responsables de esas funciones de respuesta. `TODO: Personalizar la estructura de los subequipos si es necesario.`
* Crear un puente de llamadas y un chat para cada subequipo.
* El Incident Commander designará a los líderes de los equipos, que dependen del IC, y a los miembros de los equipos, que dependen de su líder.  _Los Líderes de Equipo no tienen que estar formados como Incident Commander's, pero es preferible que tengan alguna experiencia de liderazgo._
* El Incident Commander puede ajustar el propósito o el nombre de los subequipos según sea necesario.
* Si desea cambiar de equipo, pregunte a su **líder de equipo actual**. **No** pregunte al Incident Commander, o al líder del otro(s) equipo(s). Utilice la cadena de mando.

### Incidente Dividido

Si un incidente resulta ser dos o más incidentes distintos:

* Establezca un nuevo [archivo de incidentes](#crear-archivo-del-incidente).
* Haga un seguimiento y coordine la investigación, la remediación y la comunicación en el archivo correspondiente.
* Considere la posibilidad de establecer subequipos para cada incidente.
* **Mantener un Incident Commander de alto nivel**, para coordinar los activos de baja densidad, alta demanda y mantener la unidad de mando.

# Investigar

**[Investigar](#investigar), [Remediar](#remediar) y [Comunicar](#comunicar) en paralelo!, utilizando equipos separados, si es posible.** El Incident Commander coordinará estas actividades. Notifique al Incident Commander si hay pasos que el equipo debe considerar.

## Crear Archivo del incidente

1. Cree un nuevo archivo de incidentes en {{INCIDENT_FILE_LOCATION}} utilizando el [nombre del incidente](#nombre-del-incidente). Utilice este archivo para el almacenamiento seguro de documentación, pruebas, artefactos, _etc._.
    * Proporcionar un almacenamiento digital seguro.
    * Proporcionar un intercambio de archivos seguro.
    * Obtener almacenamiento físico.
    * Compartir la ubicación del archivo del incidente en la llamada y el chat.
    * `TODO: Personalizar y automatizar la ubicación del archivo y procedimiento`
2. Documente el impacto funcional y de la información, si se conoce (véase [Evaluar](#evaluar)). `TODO: Personalizar las categorías de impacto, si es necesario.`
3. Documentar el vector, si se conoce (_e.j._ web, correo electrónico, medios extraíbles). `TODO: Personalizar la lista de vectores, si es necesario.`
4. Documente el resumen del incidente: un breve resumen del vector, el impacto, la investigación y la situación de remediación, si se conoce.
5. Documente la línea de tiempo del incidente, incluyendo la actividad del atacante y la actividad de la respuesta. `TODO: Añadir líneas de tiempo con diferentes detalles, según sea necesario.`
6. Documente los pasos de investigación, remediación y comunicación. Documente las actividades de forma independiente para que puedan combinarse y reutilizarse, si es posible.
7. Registre la información significativa, como:
    * **Evidencia**, con la hora de recogida, la fuente, la cadena de custodia, _etc._.
    * **Sistemas afectados**, con el modo y el momento en que se identificó el sistema, y el resumen del efecto (_e.j._, tiene malware, datos a los que se han accedido).
    * **Archivos de interés**, como el malware o los archivos de datos, con el sistema y los metadatos.
    * **Datos accedidos y tomados**, con nombres de archivos, metadatos y hora de presunta exposición.
    * **Actividad significativa del atacante**, como inicios de sesión y ejecución de malware, con la hora del evento.
    * **Indicadores de compromiso (IOC's)** basados en la red, como direcciones IP y dominios.
    * **Indicadores de compromiso basados en el host**, como nombres de archivos, hashes y claves de registro.
    * **Cuentas comprometidas**, con el alcance del acceso y la hora del compromiso.

`TODO: Personalizar el procedimiento de documentación del incidente, incluyendo hojas de cálculo, bases de datos, formularios, sistemas, y plantillas, si es necesario.`

## Recoger las Pistas Iniciales

1. Entrevistar a los informador(es) del incidente.
2. Recoger los datos de apoyo iniciales (_e.j._, alarmas, eventos, datos, suposiciones, intuiciones) en el archivo del incidente.
3. Entrevistar a los SME's con experiencia en el dominio o el sistema, para comprender los detalles técnicos, el contexto y el riesgo.
4. Entrevistar a los SME's de la unidad de negocio afectada, para comprender el impacto de la misión/negocio, el contexto y el riesgo.
5. Asegúrese de que las pistas son relevantes, detalladas y procesables.

### Referencia: Lista de Recursos de Respuesta

Recurso                             | Ubicación
----------------------------------- | ------------------------------------
Lista de Información Crítica        | {{CRITICAL_INFO_LIST_LOCATION}}
Lista de Activos Críticos           | {{CRITICAL_ASSET_LIST_LOCATION}}
Base de datos de Gestión de Activos | {{ASSET_MGMT_DB_LOCATION}}
Mapa de Red                         | {{NETWORK_MAP_LOCATION}}
Consola SIEM                        | {{SIEM_CONSOLE_LOCATION}}
Agregador de registros              | {{LOG_AGGREGATOR_CONSOLE}}

`TODO: Completar la información crítica y las listas de activos ("joyas de la corona"). Esto es increíblemente importante para una respuesta eficaz.`

`TODO: Personalizar la lista de recursos de respuesta`

## Actualizar El plan de Investigación y el Archivo del Incidente

1. Revisar y perfeccionar el impacto del incidente.
2. Revisar y perfeccionar el vector del incidente.
3. Revisar y perfeccionar el resumen del incidente.
4. Revisar y perfeccionar la línea de tiempo del incidente con hechos e inferencias.
5. Crear hipótesis: qué puede haber ocurrido y con qué seguridad.
6. **Identificar y priorizar las preguntas clave** (lagunas de información) para apoyar o desacreditar las hipótesis.
    * Utilizar la matriz ATT&CK de MITRE o un marco similar para [desarrollar preguntas](#referencia-matriz-de-tácticas-de-ataque-a-las-preguntas-clave).
        * [ATT&CK for Enterprise](https://attack.mitre.org/wiki/Main_Page), incluyendo enlaces a los específicos de Windows, Mac y Linux.
        * [ATT&CK Mobile Profile](https://attack.mitre.org/mobile/index.php/Main_Page) para dispositivos móviles.
    * Utilizar palabras interrogativas como inspiración:
        * **¿Cuándo?**: primer compromiso, primera pérdida de datos, acceso a x datos, acceso a y sistema, _etc._
        * **¿Qué?**: impacto, vector, causa de origen, motivación, herramientas/exploits utilizadas, cuentas/sistemas comprometidos, datos atacados/perdidos, infraestructura, IOC's, _etc._
        * **¿Dónde?**: ubicación del atacante, unidades de negocio afectadas, infraestructura, _etc._
        * **¿Cómo?**: compromiso (exploit), persistencia, acceso, exfiltración, movimiento lateral, _etc._
        * **¿Por qué?**: objetivo, momento, acceso a x datos, acceso a y sistema, _etc._
        * **¿Quién?**: atacante, usuarios afectados, clientes afectados, _etc._
1. **Identificar y priorizar los dispositivos y estrategias de los testigos** para responder a las preguntas clave.
    * Consultar los diagramas de la red, los sistemas de gestión de activos y la experiencia de los SME
    * Consultar la [Lista de Recursos de Respuesta](#referencia-lista-de-recursos-de-respuesta))
1. Consulte los [playbook de incidentes](#playbooks) para conocer las preguntas clave, los dispositivos de los testigos y las estrategias para investigar las amenazas comunes o muy dañinas.

**El plan de investigación es fundamental para una respuesta eficaz; impulsa todas las acciones de investigación. Utilice el pensamiento crítico, la creatividad y el buen juicio.**

### Referencia: Matriz de Tácticas de Ataque a las Preguntas Clave

Táctica del atacante    | La forma en que los atacantes...         | Posibles preguntas clave
----------------------- | ---------------------------------------- | -----------------------------------------
Reconocimiento          | ...aprender sobre los objetivos          | ¿Cómo? ¿Desde cuándo? ¿Dónde? ¿Qué sistemas?
Desarrollo de recursos  | ...construir infraestructuras.           | ¿Qué sistemas?
Acceso inicial          | ...entrar                                | ¿Cómo? ¿Desde cuándo? ¿Dónde? ¿Qué sistemas?
Ejecución               | ...ejecutar código hostil                | ¿Qué malware? ¿Qué herramientas? ¿Dónde? ¿Cuándo?
Persistencia            | ...quédate por aquí                      | ¿Cómo? ¿Desde cuándo? ¿Dónde? ¿Qué sistemas?
Escalada de Privilegios | ...obtener acceso de mayor nivel         | ¿Cómo? ¿Dónde? ¿Qué herramientas?
Evasión de la defensa   | ...esquivar la seguridad                 | ¿Cómo? ¿Dónde? ¿Desde cuándo?
Acceso a credenciales   | ...obtener/crear cuentas                 | ¿Qué cuentas? ¿Desde cuándo? ¿Por qué?
Descubrimiento          | ...aprender nuestra red                  | ¿Cómo? ¿Dónde? ¿Qué saben?
Movimiento lateral      | ...moverse                               | ¿Cómo? ¿Cuándo? ¿Qué cuentas?
Recogida                | ...encontrar y reunir datos              | ¿Qué datos? ¿Por qué? ¿Cuándo? ¿Dónde?
Mando y control         | ...herramientas y sistemas de control    | ¿Cómo? ¿Dónde? ¿Quién? ¿Por qué?
Exfiltración            | ...tomar datos                           | ¿Qué datos? ¿Cómo? ¿Cuándo? ¿Dónde?
Impacto                 | ...romper cosas.                         | ¿Qué sistemas o datos? ¿Cómo? ¿Cuándo? ¿Dónde? ¿Cómo de malo?

Consulte la página [MITRE ATT&CK](https://attack.mitre.org/) para obtener más información e ideas.

## Crear y Desplegar Indicadores de Compromiso (IOC's)

> Enfatice en los indicadores **dinámicos y de comportamiento** junto a las huellas digitales estáticas.

* Crear IOC's basados en [pistas iniciales](#recoger-las-pistas-iniciales) y [análisis](#analyze-evidence).
* Cree IOC's usando un formato abierto soportado por sus herramientas (_e.j._, [STIX 2.0](https://oasis-open.github.io/cti-documentation/stix/intro)), si es posible. `TODO: Personalizar el formato de los IOC's, según sea necesario.`
* Utilice la automatización, si es posible. `TODO: Añadir un procedimiento de despliegue/revocación de IOC's.`
* **No** desplegar "feeds" de IOC's no relacionados y no curados, ya que pueden causar confusión y fatiga.
* Considerar todos los tipos de IOC:
  * IOC's basados en la red, como direcciones IP o MAC, puertos, direcciones de correo electrónico, contenido o metadatos del correo electrónico, URLs, dominios o patrones PCAP.
  * IOC's basados en el host, como rutas, hashes de archivos, contenido o metadatos de archivos, claves de registro, MUTEXes, autoejecuciones o artefactos y permisos de usuarios.
  * IOC's basados en la nube, como patrones de registro para despliegues [SaaS](https://en.wikipedia.org/wiki/Software_as_a_service) o [IaaS](https://en.wikipedia.org/wiki/Infrastructure_as_a_service)
  * IOC's de comportamiento (a.ka., patrones, TTPs) tales como patrones de árbol de procesos, heurística, desviación de la línea base y patrones de inicio de sesión.
* Correlacionar varios tipos de IOC, como indicadores basados en la red y en el host en los mismos sistemas.

## Identificar los Sistemas de Interés

1. Validar si son relevantes.
2. Categorizar la(s) razón(es) por la(s) que son "de interés": tiene malware, acceso por cuenta comprometida, tiene datos sensibles, _etc._  Trátelas como "etiquetas", puede haber más de una categoría por sistema.
3. Prioriza la recogida, el análisis y la remediación en función de las necesidades de la investigación, el impacto en el negocio, _etc._

## Recogida de pruebas

* Priorizar en base al plan de investigación
* Recoger datos de respuesta en vivo utilizando {{LIVE_RESPONSE_TOOL}}. `TODO: Personalizar las herramientas y el procedimiento de respuesta en vivo.`
* Recoger los registros relevantes de los sistemas (si no forman parte de la respuesta en vivo), agregadores, SIEM o consolas de dispositivos. `TODO: Personalizar las herramientas y el procedimiento de recopilación de registros.`
* Recoger la imagen de la memoria, si es necesario y si no forma parte de la respuesta en vivo, utilizando {{MEMORY_COLLECTION_TOOL}}. `TODO: Personalizar las herramientas y el procedimiento de recogida de memoria.`
* Recoger la imagen del disco, si es necesario, utilizando {{DISK_IMAGE_TOOL}}. `TODO: Personalizar la herramienta y el procedimiento de recogida de imágenes de disco.`
* Recoger y almacenar las pruebas de acuerdo con la política, y con la cadena de custodia adecuada. `TODO: Personalizar la política de recogida de pruebas y cadena de custodia.`

Considere la posibilidad de recopilar los siguientes artefactos como evidencia, ya sea en tiempo real (_e.j._, a través de EDR o un SIEM) o bajo demanda:

###  Ejemplo de artefactos útiles

`TODO: Personalizar y priorizar los artefactos útiles.`

* Procesos en ejecución
* Servicios en ejecución
* Hashes ejecutables
* Aplicaciones instaladas
* Usuarios locales y de dominio
* Puertos de escucha y servicios asociados
* Configuración de resolución del sistema de nombres de dominio (DNS) y rutas estáticas
* Conexiones de red establecidas y recientes
* Clave de ejecución y otra persistencia de la ejecución automática
* Tareas programadas y tareas cron
* Artefactos de ejecución pasada (_e.j._, Prefetch y Shimcache)
* Registros de eventos
* Política de grupo y artefactos WMI
* Detecciones antivirus
* Binarios en ubicaciones de almacenamiento temporal
* Credenciales de acceso remoto
* Telemetría de conexiones de red (_e.j_, netflow, permisos de cortafuegos)
* Tráfico y actividad de DNS
* Actividad de acceso remoto, incluido el Protocolo de Escritorio Remoto (RDP), la red privada virtual (VPN), SSH, la computación de red virtual (VNC), y otras herramientas de acceso remoto
* Cadenas de identificadores de recursos uniformes (URI), cadenas de user-agent y acciones de aplicación del proxy
* Tráfico web (HTTP/HTTPS)

## Analizar las Pruebas

* Priorizar basándose en el plan de investigación
* Analizar y clasificar los datos de la respuesta en vivo
* Analizar la memoria y las imágenes de disco (es decir, realizar análisis forenses)
* Analizar el malware
* _OPCIONAL:_ Enriquecer con investigación e inteligencia
* Documentar nuevos indicadores de compromiso (IOC's)
* Actualizar el archivo del caso

### Ejemplo de Indicadores Útiles

`TODO: Personalizar y priorizar los indicadores útiles.`

* Comportamiento inusual de autenticación (_e.j._, frecuencia, sistemas, hora del día, ubicación remota)
* Nombres de usuario con formato no estándar
* Binarios no firmados que se conectan a la red
* Baliza o transferencias de datos significativas
* Solicitudes de línea de comandos PowerShell con comandos codificados en Base64
* Actividad excesiva de RAR, 7zip o WinZip, especialmente con nombres de archivo sospechosos
* Conexiones en puertos no utilizados previamente.
* Patrones de tráfico relacionados con el tiempo, la frecuencia y el recuento de bytes
* Cambios en las tablas de enrutamiento, como la ponderación, las entradas estáticas, las puertas de enlace y las relaciones entre pares.

## Iterar la investigación

[Actualizar el plan de investigación](#actualizar-el-plan-de-investigación-y-el-archivo-del-incidente) y repetir hasta el cierre.

# Remediar

**[Investigar](#investigar), [Remediar](#remediar) y [Comunicar](#comunicar) en paralelo, utilizando equipos separados, si es posible.** El Incident Commander coordinará estas actividades. Notifique al Incident Commander si hay pasos que el equipo debe considerar

## Actualización del Plan de Remediación

1. Revise el archivo del incidente en {{INCIDENT_FILE_LOCATION}} utilizando el [nombre del incidente](#nombre-del-incidente)
2. Revise los [playbook](#playbooks) aplicables.
3. Revise la [lista de recursos de respuesta](#referencia-lista-de-recursos-de-respuesta).
4. Considere qué tácticas del atacante están en juego en este incidente.  Utilice la lista de MITRE [ATT&CK](https://attack.mitre.org/wiki/Main_Page) (_es decir_, Persistencia, Escalada de Privilegios, Evasión de la Defensa, Acceso a Credenciales, Descubrimiento, Movimiento Lateral, Ejecución, Recolección, Exfiltración y Command & Control), o un marco similar.
5. Desarrollar remedios para cada táctica en juego, en la medida en que sea factible teniendo en cuenta las herramientas y los recursos existentes. Considere remedios para [Proteger](#protección), [Detectar](#detección), [Contener](#contención), y [Erradicar](#erradicar) cada comportamiento del atacante.
6. Priorizar en base a la [estrategia de tiempo](#elegir-el-momento-de-la-remediación), el impacto y la urgencia.
7. Documentar en el archivo de incidentes.

Utilice [marcos de seguridad de la información (infosec)](https://www.nist.gov/cyberframework) como inspiración, pero **no utilice la remediación de incidentes como sustituto de un programa de infosec con un marco apropiado.** Utilícelos para complementarse.

### Protección

> "¿Cómo podemos evitar que la táctica X vuelva a ocurrir de nuevo o reducir el riesgo? ¿Cómo podemos mejorar la protección futura?"

Utilice lo siguiente como punto de partida para la corrección de la remediación:

* Parchear las aplicaciones.
* Parchee los sistemas operativos.
* Actualice las firmas de IPS de la red y del host.
* Actualizar las firmas de protección de enpoints/EDR/antivirus.
* Reducir las ubicaciones con datos críticos.
* Reducir las cuentas administrativas o privilegiadas.
* Habilitar la autenticación multifactor.
* Reforzar los requisitos de las contraseñas.
* Bloquear los puertos y protocolos no utilizados en los límites del segmento y de la red, tanto entrantes como salientes.
* Poner en lista blanca las conexiones de red para los servidores y servicios críticos.

### Detección

> "¿Cómo podemos detectar esto en los nuevos sistemas o en el futuro? ¿Cómo podemos mejorar la detección y la investigación en el futuro?"

Utilice lo siguiente como punto de partida para la remediación de detecciones:

* Mejorar el registro y la retención de los registros del sistema, en particular de los sistemas críticos.
* Mejorar el registro de las aplicaciones, incluidas las aplicaciones SaaS.
* Mejorar la agregación de registros.
* Actualizar las firmas de IDS de la red y del host utilizando IOC's.

### Contención

> "¿Cómo podemos evitar que esto se extienda o se agrave? ¿Cómo podemos mejorar la contención en el futuro?"

Utilice lo siguiente como punto de partida para la remediación de la contención:

* Implementar listas de acceso (ACL's) en los límites de los segmentos de la red.
* Implementar bloqueos en el límite de la empresa, en múltiples capas del [modelo OSI](https://en.wikipedia.org/wiki/OSI_model).
* Desactivar o eliminar el acceso de las cuentas comprometidas.
* Bloquear direcciones IP o redes maliciosas.
* Bloquee los dominios maliciosos.
* Actualizar las firmas de IPS y antimalware de la red y el host mediante IOC's.
* Retirar de la red los sistemas críticos o comprometidos.
* Póngase en contacto con los proveedores para obtener ayuda (_e.j._, proveedores de servicios de Internet, proveedores de SaaS).
* Poner en lista blanca las conexiones de red para los servidores y servicios críticos.
* Matar o deshabilitar procesos o servicios.
* Bloquear o eliminar el acceso de proveedores y socios externos, especialmente el acceso privilegiado.

### Erradicar

> "¿Cómo podemos eliminar esto de nuestros activos? ¿Cómo podemos mejorar la erradicación en el futuro?"

Utilice lo siguiente como punto de partida para la remediación de la erradicación:

* Reconstruir o restaurar los sistemas y datos comprometidos a partir de un estado bueno conocido.
* Restablecer las contraseñas de las cuentas.
* Eliminar cuentas o credenciales hostiles.
* Borrar o eliminar malware específico (¡difícil!).
* Implementar proveedores alternativos.
* Activar y migrar a ubicaciones, servicios o servidores alternativos.

## Elegir el Momento de la Remediación

Determine la estrategia de plazos---cuando se llevarán a cabo las acciones de remediación---involucrando al Incident Commander, a los SME's y propietarios del sistema, a los SME's y propietarios de la unidad de negocio, y al equipo ejecutivo. Cada estrategia es apropiada en diferentes circunstancias:

* Elija remediación **inmediata** cuando sea más importante detener inmediatamente las actividades del atacante que seguir investigando. Por ejemplo, una pérdida financiera en curso, o un fracaso de la misión en curso, una pérdida de datos activa, o la prevención de una amenaza significativa inminente.
* Elija remediación **retrasada** cuando sea importante completar la investigación o no alertar al atacante. Por ejemplo, el compromiso a largo plazo de un atacante avanzado, el espionaje corporativo o el compromiso a gran escala de un número desconocido de sistemas.
* Elija remediación **combinada** cuando las circunstancias inmediatas y retardadas se apliquen en el mismo incidente. Por ejemplo, la segmentación inmediata de un servidor o red sensible para cumplir con los requisitos reglamentarios mientras se investiga un compromiso a largo plazo.

## Ejecutar la Remediación

* Evaluar y explicar los riesgos de las acciones de remediación a las partes interesadas. `TODO: Personalizar el procedimiento de aprobación de los riesgos de la remediación, si es necesario.`
* Implementar inmediatamente aquellas acciones de remediación que afecten poco o nada al atacante (a veces llamadas "acciones de postura"). Por ejemplo, muchas de las acciones de [protección](#protección) y [detección](#detección) anteriores son buenas candidatas.
* Programar y asignar acciones de remediación de acuerdo con la estrategia de tiempo.
* Ejecute las acciones de corrección en lotes, como eventos, para lograr la máxima eficacia y el mínimo riesgo.
* Documentar el estado de ejecución y el tiempo en el archivo de incidentes, especialmente para las medidas temporales.

## Iterar la Remediación

[Actualizar el plan de remediación](#actualización-del-plan-de-remediación) y repetir hasta el cierre.

# Comunicar

**[Investigar](#investigar), [Remediar](#remediar) y [Comunicar](#comunicar) en paralelo, utilizando equipos separados, si es posible.** Notifique al Incident Commander si hay pasos que el equipo debe considerar

Toda comunicación debe incluir la información más precisa disponible. Muestre integridad. No comunicar especulaciones.

## Comunicar Internamente

### Notificar y Actualizar a las Partes Interesadas

* Comunicarse con las partes interesadas como parte de las llamadas iniciales y de actualización, así como a través de actualizaciones basadas en eventos en la llamada y el chat.
* Coordinar las actualizaciones independientes (_e.j._, ejecutivas, legales) según sea necesario, pero con la menor frecuencia posible, para mantener el foco en la investigación y la remediación.
* Concéntrese en la mejor evaluación del vector, el impacto, el resumen y los aspectos más destacados de la línea de tiempo, incluidos los pasos de remediación. No especule.

### Notificar y Actualizar la Organización

* **No** notifique o actualice al personal que no responde hasta que el Incident Commander lo autorice, en particular si existe el riesgo de una amenaza interna.
* Coordine las actualizaciones de los equipos o de toda la organización con los ejecutivos y la dirección de la empresa.
* Concéntrese en la mejor evaluación del vector, el impacto, el resumen y los aspectos más destacados de la línea de tiempo, incluidos los pasos de remediación.  No especule.

### Crear Informe de Incidentes

* Tras el cierre del incidente, capture la información en el [archivo del incidente](#crear-archivo-del-incidente) para su distribución utilizando el formato en {{INCIDENT_REPORT_TEMPLATE}}. **Si los informes de vector, impacto, resumen, línea de tiempo y actividad están completos, esto puede ser totalmente automatizado.**
* Distribuir el informe de incidentes a lo siguiente: {{INCIDENT_REPORT_RECIPIENTS}}.
* `TODO: Personalizar la creación y distribución del informe de incidentes, si es necesario`

## Comunicar Externamente

### Notificar a los Reguladores

* **No** notifique ni ponga al día al personal que no ha respondido hasta que el Incident Commander lo autorice.
* Notificar a los organismos reguladores (por ejemplo, HIPAA/HITRUST, PCI DSS, SOX) si es necesario y de acuerdo con la política.
* Coordinar los requisitos, el formato y los plazos con el {{COMPLIANCE_TEAM}}.

### Notificar a los Clientes

* **No** notifique o actualice al personal que no responde hasta que el Incident Commander lo autorice.
* Coordine las notificaciones a los clientes con {{COMMUNICATIONS_TEAM}}.
* Incluya la fecha en el título de cualquier anuncio, para evitar confusiones.
* No utilice tópicos como "nos tomamos la seguridad muy en serio". Céntrese en los hechos.
* Sea honesto, acepte la responsabilidad y presente los hechos, junto con el plan para prevenir incidentes similares en el futuro.
* Sea lo más detallado posible con la línea de tiempo.
* Sea lo más detallado posible en cuanto a la información que se vio comprometida y cómo afecta a los clientes. Si estábamos almacenando algo que no debíamos, sé honesto al respecto. Saldrá a la luz más tarde y será mucho peor.
* No hablemos de las partes externas que podrían haber causado el problema, a menos que ya lo hayan hecho público, en cuyo caso enlazaremos con su información. Comunícate con ellos de forma independiente (ver [Notificar a los proveedores](#notificar-a-los-proveedores-y-socios))
* Publique la comunicación externa lo antes posible. Las malas noticias no mejoran con el tiempo.
* Si es posible, contacte con los equipos de seguridad internos de los clientes antes de notificar al público.

### Notificar a los Proveedores y Socios

* **No** notifique o actualice al personal que no responde hasta que el Incident Commander lo autorice.
* Si es posible, póngase en contacto con los equipos de seguridad internos de los proveedores y socios antes de notificar al público.
* Céntrese en los aspectos específicos del incidente que afectan o implican al proveedor o socio.
* Coordine los esfuerzos de respuesta y comparta la información si es posible.

### Notificar a las Fuerzas de Seguridad

* **No** notifique o actualice al personal que no responde hasta que el Incident Commander lo autorice.
* Coordinar con {{EXECUTIVE_TEAM}} y {{LEGAL_TEAM}} antes de interactuar con las fuerzas del orden.
* Póngase en contacto con las fuerzas del orden locales en {{LOCAL_LE_CONTACT}}.
* Póngase en contacto con el FBI en {{FBI_CONTACT}} o a través del [Internet Crime Complaint Center (IC3)](https://www.ic3.gov).
* Póngase en contacto con los operadores de los sistemas utilizados en el ataque, sus sistemas también pueden haber sido comprometidos.

### Contactar con el Servicio de Asistencia de Respuesta Externa

* Póngase en contacto con {{INCIDENT_RESPONSE_VENDOR}} para que le ayude a evaluar el riesgo, la gestión de incidentes, la respuesta a los mismos y el apoyo posterior al incidente.
* Póngase en contacto con {{PUBLIC_RELATIONS_VENDOR}} para que le ayude con las relaciones públicas y la comunicación externa.
* Póngase en contacto con {{INSURANCE_VENDOR}} para obtener ayuda con el seguro cibernético.

### Compartir Inteligencia

* Comparta los IOC's con [Infragard](https://www.infragard.org/) si procede.
* Comparta los IOC's con su [ISAC](https://en.wikipedia.org/wiki/Information_Sharing_and_Analysis_Center) de servicio a través de {{ISAC_CONTACT}}, si procede.

# Recuperación

`TODO: Personalizar los pasos de recuperación.`

`TODO: Especificar las herramientas y procedimientos para cada paso, a continuación.`

**La recuperación suele estar dirigida por las unidades de negocio y los propietarios de los sistemas. Tome medidas de recuperación sólo en colaboración con las partes interesadas pertinentes.**

1. Poner en marcha un plan de continuidad de negocio/recuperación de desastres: _e.j._, considerar la migración a ubicaciones operativas alternativas, sitios de conmutación por error, sistemas de copia de seguridad.
2. Integrar las acciones de seguridad con los esfuerzos de recuperación de la organización.

