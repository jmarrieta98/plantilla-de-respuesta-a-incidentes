
## Playbook: Cryptojacking

**Investigar, remediar (contener, erradicar) y comunicar en paralelo!**

### Preparación

Asigne los pasos a individuos o equipos para que trabajen simultáneamente, cuando sea posible; este playbook no es puramente secuencial. Utilice su mejor criterio.

Fase inicial en la que debe pereparar las medidas, para asegurarse que pueden responder de manera efectiva:

* Determinar y definir los Roles del equipo de Operaciones
    * Incident Commander (IC): Gerente del riesgo.
    * Incident Commander-Adjunto: Gerente de Amenaza.
    * Escriba: Documenta el incidente.
    * SME's: Gerente de Vulnerabilidad, si tiene servicios externalizados o internos.
* Revise y mantenga la línea de tiempo.
* Entrevístese con los usuarios, gerentes y seguridad física. Y tanto con los SME's internos o externos, si los hubiera y procede.
* El Escriba debe ir documentando durante la resolución del incidente y servirá de apoyo.

### Investigar 

1. **Que ocurre en la web** 
    1. Hemos detectado que la web va con lentitud.
    2. Los clientes han emitido quejas sobre el tema anterior.

### Remediar

1. **Planificar eventos de remediación**
    1. Analizar todo el código de la web buscando anomalias.
    2. Analizar logs buscando nuevas entradas.
    3. Analizar vulnerabilidades de los sistemas.

#### Contención

1. **Cuarentena**
    1. Poner en cuarentena los servidores afectados.
    2. Adquirir otro servidor para duplicar el servidor con las copias de seguridad, para tener disponibilidad en el tiempo de volver a la normalidad.

#### Erradicar

1. **Disponibilidad**
    1. Ingresar en otro servidor las copias de seguridad, asegurandonos que la web estaba correcta en ese momento para no perder la disponibilidad.
2. **Encuentra el vector de infección.**
    1. Comprobar todos los archivos de la web para 
3. **Vigilar la infección** Debemos considerar el aumento de la infección, ya que puede haber mas de una web infectada.

### Comunicar

1. Escalar el incidente y comunicarlo a la dirección según el procedimiento.
2. Documentar el incidente según el procedimiento.
3. Comunicarse con los usuarios (internos)
    1. Comunicar las actualizaciones de la respuesta al incidente según el procedimiento
    2. Comunicar el impacto del incidente y las acciones de respuesta al incidente.
    3. Comunicar los requisitos: "¿Qué deben hacer y no hacer los usuarios?"

### Recuperación

1. **Revisión** Revisar que el servidor esta totalmente limpio cuando se vuelva a iniciar, comprobar entradas y vulnerabilidades por si el atacante creo otra entrada.
2. Poner en marcha un plan de continuidad.
3. Implementar software de monitorización para captar antes que el rendimiento de la web es más lenta.

### Recursos

1. Mantenga la calma y respire profundamente.
2. Desconecte su sistema de la red
3. Haz fotos de tu pantalla con tu smartphone mostrando las cosas que has notado: mensajes de rescate, archivos encriptados, mensajes de error del sistema, _etc._.
4. Toma notas sobre el problema o los problemas utilizando la aplicación de notas de voz de tu smartphone o con papel y boli. Documenta lo siguiente:
    1. ¿Qué has notado?
    2. ¿Por qué pensaste que era un problema?
    3. ¿Qué estabas haciendo en el momento en que lo detectaste?
    4. ¿Qué sistemas está utilizando?
    5. ¿Qué cuenta utilizas?
    6. ¿A qué datos suele acceder?
    7. ¿Con quién más se ha puesto en contacto en relación con este incidente y qué le ha dicho?
1. Contacta al servicio de asistencia y ser lo más útil posible

#### Información adicional

1. <a name="playbook-criptojacking-ref-1"></a>[INCIBE  - CryptoJacking ](https://www.incibe.es/aprendeciberseguridad/cryptojacking)
