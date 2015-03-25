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

#¿Por qué utilizar Slim?

Slim le permite escribir plantillas fáciles de mantener y prácticamente garantiza que usted escribe bien formado y XML y HTML

También pensamos que la sintaxis Slim también es estético y lo hace mucho más divertido de escribir plantillas. Ya que se puede utilizar Slim como un gota en el reemplazo de todo el marco principal se puede empezar fácilmente.

La arquitectura Slim es muy flexible y permite escribir extensiones y plugins de sintaxis. Slim fue desarrollado desde el principio con el rendimiento en mente.Acabamos de garantizar que Slim no tiene un impacto negativo en el rendimiento de la aplicación.

---

##Instale Slim como un gem:

	"gem install slim"

Incluir Slim en su Gemfile con gem 'slim' o lo requieran con require 'slim'. Eso es todo! Ahora, sólo tiene que utilizar la extensión .slim y ya está listo para ir.

----

##Lista de Algunos atributos más utilizados


###Código comentario /

Utilice la barra inclinada para comentarios de código - nada después de que no conseguirá que se muestra en el render final. Utilice / para comentarios de código y /! para comentarios html

body 
  p 
    / Esta línea no quede visualizada. 
      Ni hace esta línea.
     /! Esto hará que se muestra como comentarios HTML.
El resultado del análisis de las anteriores:

		< body > < p > <! - Esto hará que se muestra como comentarios HTML .--> </ p > </ body >

---

Etiquetas cerradas (trailing / )

Puede cerrar las etiquetas explícitamente añadiendo un trailing / .

img src = " image.png " /

Tenga en cuenta, que esto no suele ser necesaria, ya que las etiquetas HTML estándar (img, br, ...) se cierran automáticamente.

----

###Arrastrando y espacios en blanco ( < , > )

Puede forzar delgado para agregar un espacio en blanco detrás después de una etiqueta mediante la adición de un > .

un > href = ' url1 ' LINK1
 un > href = ' url2 ' Link2
Puede agregar un espacio en blanco que conduce añadiendo < .

un < href = ' url1 ' Link1
 un < href = ' url2 ' Link2
También se pueden combinar ambos.

---

###Atributos cotizadas

Ejemplo:

a href = " http://slim-lang.com "  title = ' Página Delgado ' Ir a la página de inicio Delgado
Puede utilizar la interpolación texto en los atributos citados:

a href = " http: // # { url } " Ir a la # { url }
El valor del atributo se escapó por defecto. Utilice == si quieres desactivar escapar en el atributo.

a href = = " & amp; "
Usted puede romper atributos con barra invertida citado \

un título de datos = " ayuda "  datos-content = " extremadamente largo texto de ayuda que va a \ 
  y uno y uno y luego comienza de nuevo .... "

  ---

  Atajos Tag

Puede definir atajos de etiquetas personalizadas mediante el establecimiento de la opción : acceso directo .

Slim::Engine.set_options shortcut: {'c' => {tag:'container'}, '#' => {attr:'id'}, '.' => {attr:'class'} }

Podemos utilizarlo en código Slim como este

c.content Text

**lo que hace a**

<containerclass="content">Text</container>

----

###Atributo atajos

Puede definir accesos directos personalizados (similar a # de Identificación y . para la clase).

En este ejemplo le sumamos y crear un acceso directo para los elementos de entrada con atributo type.

Slim::Engine.set_options shortcut: {'&' => {tag:'input', attr:'type'}, '#' => {attr:'id'}, '.' => {attr:'class'}}

Podemos utilizarlo en código Delgado como este

&text name="user" 
&password name="pw" 
&submit

lo que hace a

<inputtype="text"name="user"/> 
<inputtype="password"name="pw"/> 
<inputtype="submit"/>

---

En otro ejemplo añadimos @ para crear un acceso directo para el atributo role

Slim::Engine.set_options shortcut: {'@' => {attr:'role'}, '#' => {attr:'id'}, '.' => {attr:'class'}}

Podemos utilizarlo en código Slim como este

.person@admin = person.name

lo que hace a

<divclass="person"role="admin">Daniel</div>

También puede configurar varios atributos a la vez utilizando un acceso directo.

Slim::Engine.set_options shortcut: {'@' => {attr:%w(data-role role)}}

Podemos utilizarlo en código Slim como este

.person@admin = person.name

<divclass="person"role="admin"data-role="admin">Daniel</div>



---

##Motores de Incrustación compatibles

| Filter | Required gems | Type | Description |
| ------ | ------------- | ---- | ----------- |
| ruby: | ninguno | Atajo | Acceso directo a incrutación código ruby|
| javascript: | ninguno | Atajo | Acceso directo a incrutación código javascript y envuelto en etiqueta de script |
| css: | ninguno | Atajo | Acceso directo a incrutación código css y envuelto en etiqueta de estilo |
| sass: | sass | Tiempo de Copilación | Insertar código sass y envuelto en etiqueta de estilo |
| scss: | sass | Tiempo de Copilación | Código SCSS embedd y envuelto en etiqueta de estilo |
| less: | less | Tiempo de Copilación | Insertar código less css y envuelto en etiqueta de estilo |
| styl: | styl | Tiempo de Copilación | Insertar código css stylus y envuelto en etiqueta de estilo |
| coffee: | coffee-script | Tiempo de Copilación | Compilar código cofee-script y envolver en etiqueta de script |
| asciidoc: | asciidoctor | Tiempo de compilación + interpolación | Compilar código AsciiDoc e interpolar # {} las variables en el texto |
| markdown: | redcarpet/rdiscount/kramdown | Tiempo de compilación + interpolación | Compilar código de rebajas e interpolar # {} las variables en el texto |
| textile: | redcloth | Tiempo de compilación + interpolación | Compilar código textil e interpolar # {} las variables en el texto |
| creole: | creole | Tiempo de compilación + interpolación | Compilar código criolla e interpolar # {} las variables en el texto |
| wiki:, mediawiki: | wikicloth | Tiempo de compilación + interpolación | Compilar código wiki e interpolar # {} las variables en el texto |
| rdoc: | rdoc | Tiempo de compilación + interpolación | Compilar código rdoc e interpolar # {} las variables en el texto |
| builder: | builder | precompilado | Insertar código constructor |
| nokogiri: | nokogiri | precompilado | Insertar código constructor nokogiri |
| erb: | ninguno | precompilado | Código erb incrutación |

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

####Jimmy Corella
Busqueda de información, Escritura en Markdown
####Alexis Pizarro 
Busqueda de información
####Diego Artavia
Escritura en Markdown y Repositorio

---






