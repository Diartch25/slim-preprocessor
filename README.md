#Preprocesador Slim

Slim es un lenguaje de plantillas, cuyo objetivo es reducir la sintaxis de las partes esenciales sin llegar a ser críptico.

El diseño inicial de Slim es comenzó como un ejercicio para ver cuánto podría ser eliminada de una plantilla estándar HTML (<,>, etiquetas de cierre, etc ...). A medida que más personas se interesaron por Slim, la funcionalidad creció y también lo hizo la flexibilidad de la sintaxis.

Slim se esfuerzan por mantener la simplicidad, pero la sintaxis de definición legible de todo el mundo no es la misma.

##¿Que es Slim?

Slim es un motor de plantillas rápido, ligero con soporte para **Rails 3 y 4**.Se ha probado en gran medida en las principales implementaciones de rubí. Utiliza integración continua (travis-ci)

**Pensamiento:** *"¿Cuál es el mínimo necesario para hacer este trabajo"*

A medida que más personas han contribuido a Slim, se han agregado adiciones de sintaxis influenciados por su uso de **Haml y Jade**. El equipo de Slim está abierto a estas adiciones porque sabemos la belleza está en el ojo del espectador.

Slim utiliza **Temple** para analizar/compilar y también está integrado en **Tilt**, por lo que se puede utilizar junto con **Sinatra o un estante Rack**.

La arquitectura del Temple es muy flexible y permite la extensión del proceso de análisis y compilación sin monoparches. Esto es utilizado por logic less plugin y el plugin traductor que proporciona *I18n*. En el modo logic less puede utilizar Slim si te gusta la sintaxis para construir su HTML, pero no quiere escribir **Rubí** en sus plantillas.



[Click para ver la fuente](http://www.rubydoc.info/gems/slim/file/doc/logic_less.md)

---

¿Por qué utilizar Slim?

Slim le permite escribir plantillas fáciles de mantener y prácticamente garantiza que usted escribe bien formado y XML y HTML

También pensamos que la sintaxis Slim también es estético y lo hace mucho más divertido de escribir plantillas. Ya que se puede utilizar Slim como un gota en el reemplazo de todo el marco principal se puede empezar fácilmente.

La arquitectura Slim es muy flexible y permite escribir extensiones y plugins de sintaxis. Slim fue desarrollado desde el principio con el rendimiento en mente.Acabamos de garantizar que Slim no tiene un impacto negativo en el rendimiento de la aplicación.

---

##Links
* Homepage: [http://slim-lang.com](http://slim-lang.com)
* Source: [http://github.com/slim-template/slim](http://github.com/slim-template/slim)
* Bugs: [http://github.com/slim-template/slim/issues](http://github.com/slim-template/slim/issues)
* List: [http://groups.google.com/group/slim-template](http://groups.google.com/group/slim-template)
* API documentation:
* Latest Gem: [http://rubydoc.info/gems/slim/frameshttps://www.omniref.com/ruby/gems/slim](http://rubydoc.info/gems/slim/frameshttps://www.omniref.com/ruby/gems/slim)
* GitHub master: [http://rubydoc.info/github/slim-template/slim/master/frameshttps://www.omniref.com/github/slim-template/slim](http://rubydoc.info/github/slim-template/slim/master/frameshttps://www.omniref.com/github/slim-template/slim)

---
