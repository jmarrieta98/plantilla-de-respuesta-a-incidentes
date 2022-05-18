# Plantilla para el Plan de Respuesta a Incidentes

## Acerca de

Esta plantilla ha sido creada por el equipo de [Counteractive Security](https://www.counteractive.net/), para ayudar a todas las organizaciones a comenzar de forma concisa, directa, especifica, flexible y gratuita un plan de respuesta a incidentes. Crea un plan [que utilizarás](https://www.counteractive.net/posts/an-ir-plan-you-will-use/) para responder de manera eficiente, minimizando los costes e impactos, para volver a trabajar tran pronto como sea posible.

Descarga la última versión [aquí](https://github.com/counteractive/incident-response-plan-template/releases/latest), por favor cree un issue o suba un pull request con cualquier retroalimentación, sugerencias, o actualizaciones. 

## Instrucciones

**💡 Si prefieres trabajar con Microsoft Word (.docx format), por favor descargue [ejemplo de word](examples/plan.docx) y personalice directamente utilizando las [siguientes instrucciones](#personalizar-aún-más-el-plan).** 

Para aquellos que esten trabajando con markdown, html, o pdf, por favor sigan leyendo.

### Descargue o haga fork esta plantilla

El diseño es el siguiente:

* `during.md`: el núcleo del plan, acciones llevadas a cabo durante una respuesta a incidentes.
* `playbooks/`: carpeta la cual contiene playbooks de investigación, remediación y sugerencias de comunicación para incidentes específicos. Cree playboks para cualquier incidente que sea muy probable o muy perjudicial para su organización. `playbooks/index.md` contiene el contenido de la cabecera de la sección del playbook, y cada playbook debe seguir la convención. `playbooks/playbook-[THREAT].md`.
* `roles/`: carpeta la cual contiene descripciones de cada rol en el plan, además de deberes y las notas de formación. `index.md` contiene los contenido de la cabecera de la sección de roles y cada rol debe seguir la convención. `playbooks/role-[ORDER]-[NAME].md`.
* `after.md`: la guía para la revisión posterior a la acción (_a.k.a._, hotwash, debrief, o post-mortem)---acciones llevadas a cabo después de una respuesta a incidentes.
* `about.md`: footer que contiene información acerca de toda la plantilla.
* `info.yml`: archivo que contiene valores para las cadenas de texto de la plantilla durante todo el plan (ver más abajo)

### Rellenar `info.yml` con la información de tu organización

Los archivos de la plantilla tienen muchos marcadores de posición que `{{LOOK_LIKE_THIS}}`. El propósito de cada marcador debería ser discernible del contexto y del [archivo `info.yml` por defecto](./info.yml). Está comentado para claridad adicional. Esta es la sintaxis de la plantilla [mustache](https://mustache.github.io/), y tiene un enorme soporte en una variedad de herramientas y lenguajes.  

La manera más fácil de reemplazar esas variables es personalizar el archivo `info.yml` con la información de tu organización y usar el proporcionado [Makefile](https://en.wikipedia.org/wiki/Make_(software)) (as of v1.0.0) para encontrar y reemplazar automáticamente todas las cadenas de texto relevantes.  _NOTA:_ esto requiere que `make` (naturalmente), `mustache`, y `pandoc` esten instalados y disponibles en el path del usuario `$PATH`. _NOTA:_ la salida en pdf necesita `pdflatex` (ver [this gist](https://gist.github.com/rain1024/98dd5e2c6c8c28f9ea9d) para instrucciones en Ubuntu/Debian), y necesitarás `git` si quieres clonar el repositorio antes que descargarlo en formato zip.

Si no tiene la información o las herramientas referenciadas en las variables de la plantilla, es definitivamente mejor solucionar eso. **Especialmente** la lista de información crítica (datos que quieres proteger) y la lista de activos críticos (sistemas que quieres proteger).

### Construye la plantilla

En la terminal de su linux, mac, o [WSL](https://docs.microsoft.com/en-us/windows/wsl/faq):

```bash
# instalar dependencias, indispensables si no están ya
sudo apt-get install make ruby-mustache pandoc

# para formato pdf (big)
sudo apt-get install texlive-latex-base texlive-fonts-recommended texlive-fonts-extra texlive-latex-extra

# cambiar al directorio del repositorio clonado
cd /path/to/incident-response-plan-template

# construir la plantilla
make
```

Esto fusiona los componentes de la plantilla, los combina con tus datos personalizados de `info.yml`, y los saca en todos los formatos soportados en el directorio `public/`. Eso es todo!.

*Si tiene un caso específico y quiere más detalles, siga leyendo!*

### Personalizar aún más el plan

1. Rellenar cualquier variable restante de la plantilla (las cadenas como `{{LOOK_LIKE_THIS}}`).
1. Repasar todos los indicadores `TODO` para probables areas personalizables, si se desea.  Borrarlas si los cambios no se requieren.
1. Añadir cualquier roles o playbooks relevantes para tu organización. Pueden ser añadidos con el tiempo.
1. Personalizar cualquier cosa más! Lo que sea que sienta que sea más efectivo para su organización.
1. _Opcional:_ Personalizar el formato directamente o [usar opciones de pandoc](https://learnbyexample.github.io/customizing-pandoc/). El Makefile por defecto usa los estilos predeterminados de pandoc, y no son para cualquiera.

### Despliegue y uso del plan

El Makefile usa [pandoc](https://pandoc.org) para crear una variedad de formatos, o puede usar los archivos markdown con [mkdocs](http://www.mkdocs.org/), [hugo](https://gohugo.io/), o un sinfín de otras plataformas.

### Ejemplos

Ejemplos de cada formato están disponibles en [directorio de ejemplos](./examples). La [versión markdown](./examples/plan.md) es un buen lugar para empezar, renderizado de markdown a html automáticamente por github.

### Contactenos 

Para asistencia profesional con respuesta a incidentes, o con la personalización, aplicación, o prueba de su plan, póngase en contacto con nosotros en contact@counteractive.net o [(888) 925-5765](tel:+18889255765).

## Licencia

Esta plantilla está proporcionada bajo una licencia Apache, version 2.0. Ver los archivos [LICENCIA](./LICENSE) y [AVISO](./NOTICE) para información adicional.

## Referencias y Material adicional

* [Awesome Incident Response](https://github.com/meirwah/awesome-incident-response)
* [NIST Computer Security Incident Handling Guide](http://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-61r2.pdf) (NIST)
* [CERT Societe Generale Incident Response Methodologies](https://github.com/certsocietegenerale/IRM/tree/master/EN)
* [Incident Handler's Handbook](https://www.sans.org/reading-room/whitepapers/incident/incident-handlers-handbook-33901) (SANS)
* [Technical Approaches to Uncovering and Remediating Malicious Activity](https://us-cert.cisa.gov/ncas/alerts/aa20-245a) (Cybersecurity and Infrastructure Security Agency (CISA))
* [Responding to IT Security Incidents](https://technet.microsoft.com/en-us/library/cc700825.aspx) (Microsoft)
* [Defining Incident Management Processes for CSIRTs: A Work in Progress](http://resources.sei.cmu.edu/library/asset-view.cfm?assetid=7153) (CMU)
* [Creating and Managing Computer Security Incident Handling Teams (CSIRTS)](https://www.first.org/conference/2008/papers/killcrece-georgia-slides.pdf) (CERT)
* [Incident Management for Operations](http://shop.oreilly.com/product/0636920036159.do) (Rob Schnepp, Ron Vidal, Chris Hawley)
* [_Incident Response & Computer Forensics, Third Edition_](http://a.co/cUkFzMh) (Jason Luttgens. Matthew Pepe. Kevin Mandia)
* [_Incident Response_](http://shop.oreilly.com/product/9780596001308.do) (Kenneth R. van Wyk, Richard Forno)
* [The Checklist Manifesto](http://atulgawande.com/book/the-checklist-manifesto/) (Atul Gawande)
* [The Field Guide to Understanding Human Error](https://www.amazon.com/Field-Guide-Understanding-Human-Error/dp/0754648265) (Sidney Dekker)
* [Normal Accidents: Living with High-Risk Technologies](https://www.amazon.com/Normal-Accidents-Living-High-Risk-Technologies/dp/0691004129) (Charles Perrow)
* [Site Reliability Engineering](https://landing.google.com/sre/book.html) (Google)
* [Debriefing Facilitation Guide](http://extfiles.etsy.com/DebriefingFacilitationGuide.pdf) (Etsy)
* [Every Minute Counts: Leading Heroku's Incident Response](https://www.heavybit.com/library/video/every-minute-counts-coordinating-herokus-incident-response/) (Blake Gentry)
* [Three Analytical Traps in Accident Investigation](https://www.youtube.com/watch?v=TqaFT-0cY7U) (Dr. Johan Bergström)
* [US National Incident Management System (NIMS)](https://www.fema.gov/national-incident-management-system) (FEMA)
* [Informed's NIMS Incident Command System Field Guide](https://www.amazon.com/gp/product/1284038408) (Michael J. Ward)
* [PagerDuty IR Docs](https://response.pagerduty.com/)
* [NIST 800-61r2](http://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-61r2.pdf)
* [NIST CSF](https://www.nist.gov/cyberframework)
* [CSO Online 10 Steps](https://www.csoonline.com/article/3203705/security/10-steps-for-a-successful-incident-response-plan.html) (June 2017) and [CSO Online 9 Steps](https://www.csoonline.com/article/3099684/disaster-recovery/9-steps-for-a-successful-incident-response-plan.html) (July 2016)
* [SecurityMetrics blog 6 Steps to Making an IR Plan](http://blog.securitymetrics.com/2017/01/6-steps-to-making-incident-response-plan.html)
* [Cal Berkeley IR Plan Development](https://security.berkeley.edu/incident-response-planning-guideline)
* [EPA IR Plan](https://www.epa.gov/sites/production/files/2016-01/documents/cio_2150-p-08.2.pdf)
* [incidentresponse.com playbooks](https://www.incidentresponse.com/playbooks/)

## Hoja de ruta

Ver lista de [issues](https://github.com/counteractive/incident-response-plan-template/issues) .

## Changelog

Ver página de [versiones](https://github.com/counteractive/incident-response-plan-template/releases) .
