## Playbook: Ramsomware

**Investigar, remediar (contener, erradicar) y comunicar en paralelo!**

Asigne los pasos a individuos o equipos para que trabajen simultáneamente, cuando sea posible; este playbook no es puramente secuencial. Utilice su mejor criterio.

### Investigar 

1. **Determinar el tipo** de ransomware (es decir, ¿Cuál es la familia, la variante o el tipo?)
    1. Encuentre cualquier mensaje relacionado. 
        * Las interfaces gráficas de usuario (GUIs) del propio malware
        * Archivos de texto o html, que a veces se abren automáticamente tras el cifrado
        * Archivos de imágen, a menudo como fondo de pantalla en los sistemas infectados.
        * Correos electrónicos de contacto en extensiones de archivos encriptados
        * Ventanas emergentes despúes de intentar abrir un archivo encriptado
        * Mensajes de voz
    1. Analice los mensajes en busca de pistas sobre el tipo de ransomware:
        * Nombre del ransomware
        * Lenguaje, estructura, frases, material gráfico
        * Correo electrónico de contacto
        * Formato de la identificación del usuario
        * Especificaciones de la demanda de rescate (_e.j._, moneda digital, tarjetas de regalo)
        * Dirección de pago en caso de moneda digital
        * Chat de soporte o página de soporte
    1. Analice los archivos afectados y/o nuevos.  
        * El esquema de cambio de nombre de los archivos encriptados, incluyendo la extensión (_e.j._, `.crypt`, `.cry`, `.locked`) y el nombre base
        * Corrupción de archivos frente a encriptación
        * Tipos de archivos y ubicaciones específicas
        * Usuario/grupo propietario de los archivos afectados
        * Icono de los archivos encriptados
        * Marcadores de archivos
        * Existencia de listados de archivos, archivos clave u otros archivos de datos
1. **Determinar el alcance:**
    1. ¿Qué sistemas están afectados?
        * Busque indicadores de compromiso (IOCs), como archivos/hashes, procesos, conexiones de red, etc.
        * Comprobar la infección de sistemas similares (_e.j._, usuarios, grupos, datos, herramientas, departamento, configuración, estado de los parches)
        * Encontrar comando & control externos (C2), si está presente, y encuentra otros sistemas que se conecten a él
    1. ¿Qué datos están afectados? (_e.j._, tipos de archivo, departamento o grupo, software afectado)
        * Buscar cambios anómalos en los metadatos de los archivos, como cambios masivos en las horas de creación o modificación.
        * Buscar cambios en archivos de datos normalmente-estables o críticos.
1. **Encuentra el vector de infección.** Comprueba las tácticas capturadas en la de MITRE ATT&CK. Las especificaciones y fuentes de datos más comunes son:
    * Archivo adjunto de correo electrónico
    * Protocolo de escritorio remoto inseguro (RDP)
    * Auto-propagación (gusano o virus)
    * Infección via dispositivos extraíbles (gusano o virus)
    * Entregado por otro malware o herramienta de ataque

### Remediar
1. **Planificar eventos de remediación** en los que estos pasos se lancen juntos (o de forma coordinada), con los equipos apropiados listos para responder a cualquier interrupción.
    1. Equipos infectados
        * Retirar el cable de red
        * Adquirir imagen de disco forese para realizar la investigación
1. **Considere el tiempo y las compensaciones** de las acciones de remediación: su respuesta tiene consecuencias.
    1. ¿Qué información tenemos crítica?
        * Ver los gastos que supone la restauración de información y si no renta asimilar las pérdidas.

#### Contención

Las cuarentenas (lógicas, físicas o ambas) impiden la propagación _desde_ los sistemas infectados y evitan la propagación _hacia_ los sistemas y datos críticos. Las cuarentenas deben ser exhaustivas: incluir el acceso a la nube/SaaS, el inicio de sesión único, el acceso a sistemas como el ERP u otras herramientas empresariales, _etc._.

* Poner en cuarentena los sistemas infectados
* Poner en cuarentena a los usuarios y grupos afectados.
* Ponga en cuarentena los archivos compartidos (no sólo los conocidos; proteja también los no infectados).
* Ponga en cuarentena las bases de datos compartidas (no sólo los servidores infectados conocidos; proteja también las bases de datos no infectadas)
* Ponga en cuarentena las copias de seguridad, si no están ya protegidas
* Bloquee los dominios y direcciones de comando & control
* Elimine los correos electrónicos vectoriales de las bandejas de entrada.
* Confirmar que los parches se despliegan en todos los sistemas (priorizando los sistemas, SO's, software, _etc._).
* Despliegue de firmas personalizadas en las herramientas de protección de endpoints y de seguridad de la red, basándose en los IOC's descubiertos.

#### Erradicar

* Reconstruir los sistemas infectados a partir de soportes conocidos como buenos.
* Restaurar a partir de copias de seguridad conocidas y limpias.
* Confirmar que la protección de los endpoints (AV, NGAV, EDR, etc.) está actualizada y activada en todos los sistemas.
* Confirmar que los parches se despliegan en todos los sistemas (dando prioridad a los sistemas, SO's, software, _etc._).
* Despliegue de firmas personalizadas en las herramientas de protección de endpoints y de seguridad de la red, basándose en los IOC's descubiertos.
* **Vigilar la re-infección:** considerar el aumento de la prioridad de las alarmas/alertas relacionadas con este incidente.

### Comunicar

1. Escalar el incidente y comunicarlo a la dirección según el procedimiento.
1. Documentar el incidente según el procedimiento
1. Comunicarse con los asesores jurídicos internos y externos según el procedimiento, incluyendo discusiones sobre el cumplimiento, la exposición al riesgo, la responsabilidad, el contacto con las fuerzas del orden, _etc._
1. Comunicarse con los usuarios (internos)
    1. Comunicar las actualizaciones de la respuesta al incidente según el procedimiento
    1. Comunicar el impacto del incidente y las acciones de respuesta al incidente.
    1. Comunicar los requisitos: "¿Qué deben hacer y no hacer los usuarios?" Véase "Referencia: Acciones del usuario en caso de sospecha de ransomware", a continuación
1. Comuníquese con los clientes
    1. Centrarse especialmente en aquellos cuyos datos se han visto afectados
    1. Genere las notificaciones requeridas en base a las regulaciones aplicables (particularmente aquellas que puedan considerar el ransomware como una violación de datos o que de alguna manera requieran notificaciones
1. Póngase en contacto con los proveedore(s) de seguros
    1. Discutir qué recursos pueden poner a disposición, qué herramientas y proveedores apoyan y pagarán, _etc._
    1. Cumplir con los requisitos de notificación y reclamación para proteger la elegibilidad
1. Comuníquese con los organismos reguladores, incluyendo una discusión sobre los recursos que pueden poner a su disposición (no sólo una notificación de tipo repetitivo: muchos pueden ayudar activamente)
1. Considerar la posibilidad de notificar e implicar a las fuerzas del orden
1. Comuníquese con los proveedores de seguridad y de TI
    1. Notificar y colaborar con los proovedores según el procedimiento


### Recuperación

> **No recomendamos pagar el rescate:** no garantiza la solución del problema. Puede salir mal (_e.j._, los errores podrían hacer que los datos sean irrecuperables incluso con la clave).  Además, pagar demuestra que el ransomware funciona y podría aumentar los ataques contra ti o contra otros grupos.

1. Poner en marcha un plan de continuidad de la actividad/recuperación de desastres: _e.j._, considerar la migración a ubicaciones operativas alternativas, sitios de conmutación por error, sistemas de respaldo.
1. Recuperar los datos de las copias de seguridad ya limpias en sistemas ya limpios, parcheados y monitorizados (post-erradicación)
    * Comprobar las copias de seguridad en busca de indicadores de compromiso
    * Considerar la recuperación parcial y las pruebas de integridad de las copias de seguridad
1. Considerar el pago del rescate por los activos/datos críticos irrecuperables, de acuerdo con la política
    * Considerar las ramificaciones con las partes interesadas apropiadas
    * Comprender las implicaciones financieras y el presupuesto
    * Comprender las implicaciones legales, reglamentarias y de seguros
    * Comprender los mecanismos (_e.j._, tecnologías, plataformas, proveedores intermedios/intermediarios)

### Recursos

1. Mantenga la calma y respire profundamente.
1. Desconecte su sistema de la red
1. Haz fotos de tu pantalla con tu smartphone mostrando las cosas que has notado: mensajes de rescate, archivos encriptados, mensajes de error del sistema, _etc._.
1. 2. Toma notas sobre el problema o los problemas utilizando la aplicación de notas de voz de tu smartphone o con papel y boli. Documenta lo siguiente:
    1. ¿Qué has notado?
    1. ¿Por qué pensaste que era un problema?
    1. ¿Qué estabas haciendo en el momento en que lo detectaste?
    1. ¿Cuándo se produjo por primera vez, y con qué frecuencia desde entonces?
    1. ¿Dónde estaba cuando ocurrió y en qué red?
    1. ¿Qué sistemas está utilizando?
    1. ¿Qué cuenta utilizas?
    1. ¿A qué datos suele acceder?
    1. ¿Con quién más se ha puesto en contacto en relación con este incidente y qué le ha dicho?
1. Contacta al servicio de asistencia y ser lo más útil posible

#### Información adicional

1. <a name="playbook-ransomware-ref-1`"></a>No More Ransom [No More Ransom!](https://www.nomoreransom.org)