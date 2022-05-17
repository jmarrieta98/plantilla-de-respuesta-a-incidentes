
## Playbook: Ransomware

**Investigar, remediar (contener, erradicar), y comunicar en paralelo. La contención es crítica en los incidentes de ransomware, priorice en consecuencia.**

Asigne pasos a individuos o equipos para que trabajen simultáneamente, cuando sea posible; este playbook no es puramente secuencial. Utilice su mejor criterio.

### Investigación

`TODO: Ampliar los pasos de la investigación, incluyendo las preguntas y estrategias clave, para el ransomware.`

1. **Determinar el tipo** de ransomware (es decir, ¿Cuál es la familia, la variante o el tipo?)[<sup>[1]</sup>](#ransomware-playbook-ref-1)
    1. Encuentre cualquier mensaje relacionado.  Compruebe:
        * las interfaces gráficas de usuario (GUIs) del propio malware
        * archivos de texto o html, que a veces se abren automáticamente tras el cifrado
        * archivos de imágen, a menudo como fondo de pantalla en los sistemas infectados.
        * correos electrónicos de contacto en extensiones de archivos encriptados
        * ventanas emergentes despúes de intentar abrir un archivo encriptado
        * mensajes de voz
    1. Analice los mensajes en busca de pistas sobre el tipo de ransomware:
        * nombre del ransomware
        * lenguaje, estructura, frases, material gráfico
        * correo electrónico de contacto
        * formato de la identificación del usuario
        * especificaciones de la demanda de rescate (_e.j._, moneda digital, tarjetas de regalo)
        * dirección de pago en caso de moneda digital
        * chat de soporte o página de soporte
    1. Analice los archivos afectados y/o nuevos.  Compruebe:
        * el esquema de cambio de nombre de los archivos encriptados, incluyendo la extensión (_e.j._, `.crypt`, `.cry`, `.locked`) y el nombre base
        * corrupción de archivos frente a encriptación
        * tipos de archivos y ubicaciones específicas
        * usuario/grupo propietario de los archivos afectados
        * icono de los archivos encriptados
        * marcadores de archivos
        * existencia de listados de archivos, archivos clave u otros archivos de datos

    1. Analice los tipos de software o sistemas afectados.  Algunas variantes de ransomware sólo afectan a determinadas herramientas (_e.j._, [bases de datos](https://www.bleepingcomputer.com/news/security/mongodb-apocalypse-professional-ransomware-group-gets-involved-infections-reach-28k-servers/)) o plataformas (_e.j._, [productos NAS](https://forum.synology.com/enu/viewtopic.php?f=3&t=88716))
    1. Subir los indicadores a servicios de categorización automatizados como [Crypto Sheriff](https://www.nomoreransom.org/crypto-sheriff.php), [ID Ransomware](https://id-ransomware.malwarehunterteam.com/), o similar.
1. **Determinar el alcance:**
    1. ¿Qué sistemas están afectados? `TODO: Especificar herramientas y procedimientos`
        * Busque indicadores de compromiso (IOCs), como archivos/hashes, procesos, conexiones de red, etc.  Utilice [protección endpoint/EDR](#TODO-link-to-actual-resource), [telemetría endpoint](#TODO-link-to-actual-resource), [logs del sistema](#TODO-link-to-actual-resource), etc.
        * Comprobar la infección de sistemas similares (_e.j._, usuarios, grupos, datos, herramientas, departamento, configuración, estado de los parches): comprobar [herramientas IAM](#TODO-link-to-actual-resource), [herramientas de administración de persmisos](#TODO-link-to-actual-resource), [servicios de directorio](#TODO-link-to-actual-resource), _etc._
        * Encontrar comando y control externos (C2), si está presente, y encuentra otros sistemas que se conecten a él: comprobar [firewall o logs de IDS](#TODO-link-to-actual-resource), [logs de sistemas/EDR](#TODO-link-to-actual-resource), [logs DNS](#TODO-link-to-actual-resource), [logs de netflow o router](#TODO-link-to-actual-resource), _etc._
    1. ¿Qué datos están afectados? (_e.j._, tipos de archivo, departamento o grupo, software afectado) `TODO: Especifique la(s) herramienta(s) y el procedimiento`
        * Buscar cambios anómalos en los metadatos de los archivos, como cambios masivos en las horas de creación o modificación. Comprobar [herramientas de búsqueda de metadatos de archivos](#TODO-link-to-actual-resource)
        * Buscar cambios en archivos de datos normalmente-estables o críticos. Comprobar herramientas de [monitorización de integridad de archivos](#TODO-link-to-actual-resource)
1. **Evaluar el impacto** para priorizar y motivar los recursos
    1. Evaluar el impacto funcional: impacto en la empresa o en la misión.
        * ¿Cuánto dinero se pierde o está en riesgo?
        * ¿Cuántas (y cuáles) misiones se degradan o están en riesgo?
    1. Evaluar el impacto en la información: impacto en la confidencialidad, integridad y disponibilidad de los datos.
        * ¿Qué importancia tienen los datos para la empresa/misión?
        * ¿Cuán sensibles son los datos? (_e.j._, secretos comericales)
        * ¿Cuál es la situación reglamentaria de los datos (_e.j._, PII, PHI)?

1. **Encuentra el vector de infección.** Comprueba las tácticas capturadas en la [Initial Access tactic](https://attack.mitre.org/tactics/TA0001/) de MITRE ATT&CK[<sup>[4]</sup>](#ransomware-playbook-ref-4).  Las especificaciones y fuentes de datos más comunes son:
    * archivo adjunto de correo electrónico: comprobar [logs de correo electrónico](#TODO-link-to-actual-resource), [dispositivos y servicios de seguridad del correo electrónico](#TODO-link-to-actual-resource), [herramientas e-discovery](#TODO-link-to-actual-resource), _etc._
    * protocolo de escritorio remoto inseguro (RDP): comprueba [resultado de escaneo de vulnerabilidades](#TODO-link-to-actual-resource), [configuraciones del firewall](#TODO-link-to-actual-resource), _etc._
    * auto-propagación (gusano o virus) (comprueba [telemetría del host/EDR](#TODO-link-to-actual-resource), [logs del sistema](#TODO-link-to-actual-resource), [análisis forense](#TODO-link-to-actual-resource), _etc._)
    * infección via dispositivos extraíbles (gusano o virus)
    * entregado por otro malware o herramienta de ataque: `TODO: ampliar la investigación para incluir otras herramientas de ataque o malware`

### Remediar

**Planificar eventos de remediación** en los que estos pasos se lancen juntos (o de forma coordinada), con los equipos apropiados listos para responder a cualquier interrupción.
**Considere el momento y las compensaciones** de las acciones de remediación: su respuesta tiene consecuencias.

#### Contención

`TODO: Personalizar los pasos de contención, tácticos y estratégicos, para el ransomware.`

`TODO: especificar las herramientas y los procedimientos para cada paso, a continuación.`

**En situaciones de ransomware, la contención es crítica.  Informar de las medidas de contención con los datos de la investigación.  Dé mayor prioridad a las cuarentenas y otras medidas de contención que durante una respuesta típica.**

Las cuarentenas (lógicas, físicas o ambas) impiden la propagación _desde_ los sistemas infectados y evitan la propagación _hacia_ los sistemas y datos críticos. Las cuarentenas deben ser exhaustivas: incluir el acceso a la nube/SaaS, el inicio de sesión único, el acceso a sistemas como el ERP u otras herramientas empresariales, _etc._.

* Poner en cuarentena los sistemas infectados
* Poner en cuarentena a los usuarios y grupos afectados.
* Ponga en cuarentena los archivos compartidos (no sólo los conocidos; proteja también los no infectados).
* Ponga en cuarentena las bases de datos compartidas (no sólo los servidores infectados conocidos; proteja también las bases de datos no infectadas)
* Ponga en cuarentena las copias de seguridad, si no están ya protegidas
* Bloquee los dominios y direcciones de comando & control
* Elimine los correos electrónicos vectoriales de las bandejas de entrada.
* Confirme que la protección de enpoints (AV, NGAV, EDR, etc.) está actualizada y activada en todos los sistemas.
* Confirmar que los parches se despliegan en todos los sistemas (priorizando los sistemas, SO's, software, _etc._).
* Despliegue de firmas personalizadas en las herramientas de protección de endpoints y de seguridad de la red, basándose en los IOC's descubiertos.

`TODO: Considerar la posibilidad de automatizar las medidas de contención mediante herramientas de orquestación.`

#### Erradicar

`TODO: Personalizar los pasos de erradicación, tácticos y estratégicos, para el ransomware.`

`TODO: Especificar las herramientas y los procedimientos para cada paso, a continuación.`

* Reconstruir los sistemas infectados a partir de soportes conocidos como buenos.
* Restaurar a partir de copias de seguridad conocidas y limpias.
* Confirmar que la protección de los endpoints (AV, NGAV, EDR, etc.) está actualizada y activada en todos los sistemas.
* Confirmar que los parches se despliegan en todos los sistemas (dando prioridad a los sistemas, SO's, software, _etc._).
* Despliegue de firmas personalizadas en las herramientas de protección de endpoints y de seguridad de la red, basándose en los IOC's descubiertos.
* **Vigilar la re-infección:** considerar el aumento de la prioridad de las alarmas/alertas relacionadas con este incidente.

#### Referencia: Recursos de Remediación

`TODO: Especifique los recursos financieros, de personal y logísticos para llevar a cabo la remediación.`

### Comunicar

`TODO: Personalizar los pasos de comunicación para el ransomware.`

`TODO: Especifique las herramientas y los procedimientos (incluyendo quién debe participar) para cada paso, a continuación, o remítase al plan general.`

1. Escalar el incidente y comunicarlo a la dirección según el procedimiento.
1. Documentar el incidente según procedimiento
1. Comunicarse con los asesores jurídicos internos y externos según el procedimiento, insluyendo discusiones sobre el cumplimiento, la exposición al riesgo, la responsabilidad, el contacto con las fuerzas del orden, _etc._
1. Comunicarse con los usuarios (internos)
    1. Comunicar las actualizaciones de la respuesta al incidente según el procedimiento
    1. Comunicar el impacto del incidente y las acciones de respuesta al incidente (_e.j._, contención: "¿Por qué está caído el archivo compartido?"), que pueda ser más intrusivo/disruptivo durante los incidentes de ransomware
    1. Comunicar los requisitos: "¿Qué deben hacer y no hacer los usuarios?" Véase "Referencia: Acciones del usuario en caso de sospecha de ransomware", a continuación
1. Comuníquese con los clientes
    1. Centrarse especialmente en aquellos cuyos datos se han visto afectados
    1. Genere las notificaciones requeridas en base a las regulaciones aplicables (particularmente aquellas que puedan considerar el ransomware como una violación de datos o que de alguna manera requieran notificaciones (_e.j._, [HHS/HIPAA](https://www.hhs.gov/sites/default/files/RansomwareFactSheet.pdf))) `TODO: Amplíe los requisitos y procedimientos de notificación para las regulaciones aplicables`
1. Póngase en contacto con los proveedore(s) de seguros
    1. Discutir qué recursos pueden poner a disposición, qué herramientas y proveedores apoyan y pagarán, _etc._
    1. Cumplir con los requisitos de notificación y reclamación para proteger la elegibilidad
1. Comuníquese con los organismos reguladores, incluyendo una discusión sobre los recursos que pueden poner a su disposición (no sólo una notificación de tipo repetitivo: muchos pueden ayudar activamente)
1. Considerar la posibilidad de notificar e implicar a las fuerzas del orden [las fuerzas del orden](https://www.nomoreransom.org/en/report-a-crime.html)
    1. [Aplicación de la ley local](#TODO-link-to-actual-resource)
    1. [Aplicación de la ley local a nivel estatal o regional](#TODO-link-to-actual-resource)
    1. [Fuerzas de seguridad europeas o nacionales](#TODO-link-to-actual-resource)
1. Comuníquese con los proveedores de seguridad y de TI
    1. Notificar y colaborar con los [proveedores gestionados](#TODO-link-to-actual-resource) según el procedimiento
    1. Notificar y colaborar con los [consultores de respuesta a incidentes](#TODO-link-to-actual-resource) según el procedimiento

### Recuperación

`TODO: Personalizar los pasos de recuperación para el ransomware`

`TODO: Especificar las herramientas y procedimientos para cada paso, a continuación.`

> **No recomendamos pagar el rescate:** no garantiza la solución del problema. Puede salir mal (_e._, los errores podrían hacer que los datos sean irrecuperables incluso con la clave).  Además, pagar demuestra que el ransomware funciona y podría aumentar los ataques contra ti o contra otros grupos.[<sup>[2, paraphrased]</sup>](#ransomware-playbook-ref-2)

1. Poner en marcha un plan de continuidad de la actividad/recuperación de desastres: _e.j._, considerar la migración a ubicaciones operativas alternativas, sitios de conmutación por error, sistemas de respaldo.
1. Recuperar los datos de las copias de seguridad ya limpias en sistemas ya limpios, parcheados y monitorizados (post-erradicación), de acuerdo con nuestra [estrategia de copias de seguridad bien-testeadas](#TODO-link-to-actual-resource).
    * Comprobar las copias de seguridad en busca de indicadores de compromiso
    * Considerar la recuperación parcial y las pruebas de integridad de las copias de seguridad
1. ¡Encuentre y pruebe desencriptadores conocidos para la(s) variante(s) descubierta(s) utilizando recursos como el proyecto No More Ransom! Project's [página de Herramientas de Desencriptación](https://www.nomoreransom.org/en/decryption-tools.html).
1. Considerar el pago del rescate por los activos/datos críticos irrecuperables, de acuerdo con la política `TODO: Ampliar y socializar esta matriz de decisión`
    * Considerar las ramificaciones con las partes interesadas apropiadas
    * Comprender las implicaciones financieras y el presupuesto
    * Comprender las implicaciones legales, reglamentarias y de seguros
    * Comprender los mecanismos (_e.j._, tecnologías, plataformas, proveedores intermedios/intermediarios)

### Recursos

#### Referencia: Acciones de los Usuarios ante la Sospecha de Ransomware

`TODO: Personalizar los pasos para los usuarios ante la sospecha de ransomware`.

1. Mantenga la calma y respire profundamente.
1. Desconecte su sistema de la red `TODO: incluya pasos detallados con capturas de pantalla, una herramienta preinstalada o un script para facilitar esta tarea ("romper en caso de emergencia"), considere los interruptores de corte de red por hardware`.
1. Haz fotos de tu pantalla con tu smartphone mostrando las cosas que has notado: mensajes de rescate, archivos encriptados, mensajes de error del sistema, _etc._.
1. 2. Toma notas sobre el problema o los problemas utilizando la aplicación de notas de voz de tu smartphone o con papel y boli. Todo ayuda!. Documenta lo siguiente:
    1. ¿Qué has notado?
    1. ¿Por qué pensaste que era un problema?
    1. ¿Qué estabas haciendo en el momento en que lo detectaste?
    1. ¿Cuándo se produjo por primera vez, y con qué frecuencia desde entonces?
    1. ¿Dónde estaba cuando ocurrió y en qué red? (oficina/casa/tienda, con cable/inalámbrica, con/sin VPN, _etc._)
    1. ¿Qué sistemas está utilizando? (sistema operativo, nombre de host, _etc._)
    1. ¿Qué cuenta utilizas?
    1. ¿A qué datos suele acceder?
    1. ¿Con quién más se ha puesto en contacto en relación con este incidente y qué le ha dicho?
1. Contacta al  [servicio de asistencia](#TODO-link-to-actual-resource) y ser lo más útil posible
1. Tenga paciencia: la respuesta puede ser perturbadora, pero está protegiendo a su equipo y a la organización!  **Gracias.**

#### Referencia: Acciones del Help Desk ante la Sospecha de Ransomware

`TODO: Personalizar los pasos para el personal del servicio de asistencia ante la sospecha de ransomware`.

1. Mantenga la calma y respire profundamente.
1. Abra un ticket para documentar el incidente, según el procedimiento `TODO: Personalizar la plantilla con las preguntas clave (veáse más abajo) y el flujo de trabajo posterior`
1. 2. Pídale al usuario que tome fotos de su pantalla usando su smartphone mostrando las cosas que notó: mensajes de rescate, archivos encriptados, mensajes de error del sistema, _etc._ Si es algo que ha notado directamente, haga lo mismo usted.
1. Toma notas sobre el problema o los problemas utilizando la aplicación de notas de voz de tu smartphone o con papel y boli. Si se trata de un informe de usuario, haz preguntas detalladas, incluyendo:
    1. ¿Qué has notado?
    1. ¿Por qué pensaste que era un problema?
    1. ¿Qué estabas haciendo en el momento en que lo detectaste?
    1. ¿Cuándo se produjo por primera vez, y con qué frecuencia desde entonces?
    1. ¿De qué redes se trata? (oficina/casa/tienda, cableada/inalámbrica, con/sin VPN, _etc._)
    1. 2. ¿De qué sistemas se trata? (sistema operativo, nombre de host, _etc._)
    1. 2. ¿De qué datos se trata? (rutas, tipos de archivos, archivos compartidos, bases de datos, software, _etc._)
    1. ¿Qué usuarios y cuentas están implicados? (directorio activo, SaaS, SSO, cuentas de servicio, _etc._)
    1. ¿A qué datos suelen acceder los usuarios implicados?
    1. ¿Con quién más has contactado acerca de este incidente y qué les has dicho?
1. Haz las preguntas de seguimiento que sean necesarias.  **Usted es el encargado de responder al incidente, contamos con usted.**
1. Obtenga información de contacto detallada del usuario (domicilio, oficina, móvil), si procede
1. Registre toda la información en el ticket, incluyendo notas manuscritas y de voz
1. Poner en cuarentena a los usuarios y sistemas afectados `TODO: Personalizar los pasos de contención, automatizar todo lo posible`
1. Póngase en contacto con el [equipo de seguridad](#TODO-link-to-actual-resource) y estar preparados para participar en la respuesta según las indicaciones: investigación, remediación, comunicación y recuperación

#### Información adicional

1. <a name="ransomware-playbook-ref-1"></a>["Identificación de Ransomware para el analista Juicioso"](https://www.gdatasoftware.com/blog/2019/06/31666-ransomware-identification-for-the-judicious-analyst), Hahn (12 Jun 2019)
1. <a name="ransomware-playbook-ref-2"></a>[No More Ransom!](https://www.nomoreransom.org) Proyecto, incluyendo su [Crypto Sheriff](https://www.nomoreransom.org/crypto-sheriff.php?lang=en) servicio y su [Q&A](https://www.nomoreransom.org/en/ransomware-qa.html)
1. <a name="ransomware-playbook-ref-3"></a>[ID Ransomware](https://id-ransomware.malwarehunterteam.com/) servicio
1. <a name="ransomware-playbook-ref-4"></a>[MITRE ATT&CK Matrix](https://attack.mitre.org), incluyendo [Accesos Iniciales](https://attack.mitre.org/tactics/TA0001/) y tácticas de [Impacto](https://attack.mitre.org/tactics/TA0040/)

