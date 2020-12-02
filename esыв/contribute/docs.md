# Contribuir a la documentación de TensorFlow

TensorFlow agradece las contribuciones de documentación; si mejora la documentación, mejora la biblioteca de TensorFlow en sí. La documentación de tensorflow.org se divide en las siguientes categorías:

- *Referencia de la* [API: los documentos de referencia de la API](https://www.tensorflow.org/api_docs/) se generan a partir de cadenas de documentos en el [código fuente de TensorFlow](https://github.com/tensorflow/tensorflow) .
- *Documentación narrativa: estos* son [tutoriales](https://www.tensorflow.org/tutorials) , [guías](https://www.tensorflow.org/guide) y otros escritos que no forman parte del código de TensorFlow. Esta documentación se encuentra en el repositorio de GitHub [tensorflow / docs](https://github.com/tensorflow/docs) .
- -Estos son *traducciones de la comunidad* guías y tutoriales traducidos por la comunidad. Todas las traducciones de la comunidad se encuentran en el [repositorio de tensorflow / docs](https://github.com/tensorflow/docs/tree/master/site) .

Algunos [proyectos de TensorFlow](https://github.com/tensorflow) mantienen los archivos fuente de la documentación cerca del código en un repositorio separado, generalmente en un directorio `docs/` . Vea el archivo `CONTRIBUTING.md` del proyecto o comuníquese con el mantenedor para contribuir.

Para participar en la comunidad de documentos de TensorFlow:

- Mira el repositorio de GitHub de [tensorflow / docs](https://github.com/tensorflow/docs) .
- Suscríbase a [docs@tensorflow.org](https://groups.google.com/a/tensorflow.org/forum/#!forum/docs) .

## Referencia de API

To update reference documentation, find the [source file](https://www.tensorflow.org/code/tensorflow/python/) and edit the symbol's <a href="https://www.python.org/dev/peps/pep-0257/" class="external">docstring</a>. Many API reference pages on tensorflow.org include a link to the source file where the symbol is defined. Docstrings support <a href="https://help.github.com/en/articles/about-writing-and-formatting-on-github" class="external">Markdown</a> and can be (approximately) previewed using any <a href="http://tmpvar.com/markdown.html" class="external">Markdown previewer</a>.

Para obtener información sobre la calidad de la documentación de referencia y cómo involucrarse con los sprints de documentos y la comunidad, consulte el [consejo de Documentos de la API de TensorFlow 2](https://docs.google.com/document/d/1e20k9CuaZ_-hp25-sSd8E8qldxKPKQR-SkwojYr_r-U/preview) .

### Versiones y ramas

The site's [API reference](https://www.tensorflow.org/api_docs/python/tf) version defaults to the latest stable binary—this matches the package installed with `pip install tensorflow`.

The default TensorFlow package is built from the stable branch `rX.x` in the main <a href="https://github.com/tensorflow/tensorflow" class="external">tensorflow/tensorflow</a> repo. The reference documentation is generated from code comments and docstrings in the source code for <a href="https://www.tensorflow.org/code/tensorflow/python/" class="external">Python</a>, <a href="https://www.tensorflow.org/code/tensorflow/cc/" class="external">C++</a>, and <a href="https://www.tensorflow.org/code/tensorflow/java/" class="external">Java</a>.

Las versiones anteriores de la documentación de TensorFlow están disponibles como [ramas rX.x](https://github.com/tensorflow/docs/branches) en el repositorio de TensorFlow Docs. Estas ramas se agregan cuando se lanza una nueva versión.

### Compilar documentos de API

Nota: Este paso no es necesario para editar o obtener una vista previa de las cadenas de documentos de la API, solo para generar el HTML utilizado en tensorflow.org.

#### Referencia de Python

El paquete `tensorflow_docs` incluye el generador de los [documentos de referencia de la API de Python](https://www.tensorflow.org/api_docs/python/tf) . Instalar:

<pre class="prettyprint lang-bsh">&lt;code class = &quot;devsite-terminal&quot;&gt; GL_CODE_5 &lt;/code&gt;
</pre>

Para generar los documentos de referencia de TensorFlow 2, use la `tensorflow/tools/docs/generate2.py` :

<pre class="prettyprint lang-bsh">&lt;code class = &quot;devsite-terminal&quot;&gt; GL_CODE_7 &lt;/code&gt;
&lt;code class = &quot;devsite-terminal&quot;&gt; GL_CODE_8 &lt;/code&gt;
&lt;code class = &quot;devsite-terminal&quot;&gt; GL_CODE_9 &lt;/code&gt;
&lt;code class = &quot;devsite-terminal&quot;&gt; GL_CODE_10 &lt;/code&gt;
</pre>

Nota: Esta secuencia de comandos usa el paquete TensorFlow *instalado* para generar documentos y solo funciona para TensorFlow 2.x.

## Documentación narrativa

Las [guías](https://www.tensorflow.org/guide) y los [tutoriales de](https://www.tensorflow.org/tutorials) TensorFlow se escriben como archivos <a href="https://guides.github.com/features/mastering-markdown/" class="external">Markdown</a> y cuadernos interactivos de <a href="https://jupyter.org/" class="external">Jupyter</a> . Los blocs de notas se pueden ejecutar en su navegador mediante <a href="https://colab.research.google.com/notebooks/welcome.ipynb" class="external">Google Colaboratory</a> . Los documentos narrativos en [tensorflow.org](https://www.tensorflow.org) se crean a partir de la rama `master` <a href="https://github.com/tensorflow/docs" class="external">tensorflow / docs</a> . Las versiones anteriores están disponibles en GitHub en las ramas de la versión `rX.x`

### Cambios simples

La forma más sencilla de realizar actualizaciones de documentación sencillas a los archivos Markdown es utilizar el <a href="https://help.github.com/en/articles/editing-files-in-your-repository" class="external">editor de archivos basado en web</a> de GitHub. Explore el repositorio de [tensorflow / docs](https://github.com/tensorflow/docs/tree/master/site/en) para encontrar el Markdown que corresponde aproximadamente a la estructura de URL de <a href="https://www.tensorflow.org">tensorflow.org</a> . En la esquina superior derecha de la vista del archivo, haga clic en el ícono de lápiz <svg version="1.1" width="14" height="16" viewbox="0 0 14 16" class="octicon octicon-pencil" aria-hidden="true"></svg><path fill-rule="evenodd" d="M0 12v3h3l8-8-3-3-8 8zm3 2H1v-2h1v1h1v1zm10.3-9.3L12 6 9 3l1.3-1.3a.996.996 0 0 1 1.41 0l1.59 1.59c.39.39.39 1.02 0 1.41z"></path> para abrir el editor de archivos. Edite el archivo y luego envíe una nueva solicitud de extracción.

### Configurar un repositorio de Git local

Para ediciones de varios archivos o actualizaciones más complejas, es mejor usar un flujo de trabajo de Git local para crear una solicitud de extracción.

Nota: <a href="https://git-scm.com/" class="external">Git</a> es el sistema de control de versiones de código abierto (VCS) que se utiliza para realizar un seguimiento de los cambios en el código fuente. <a href="https://github.com" class="external">GitHub</a> es un servicio en línea que proporciona herramientas de colaboración que funcionan con Git. Consulte la <a href="https://help.github.com" class="external">Ayuda de GitHub</a> para configurar su cuenta de GitHub y comenzar.

Los siguientes pasos de Git solo son necesarios la primera vez que configura un proyecto local.

#### Bifurcar el repositorio de tensorflow / docs

En la página de GitHub de <a href="https://github.com/tensorflow/docs" class="external">tensorflow / docs, haz</a> clic en el botón *Fork* <svg class="octicon octicon-repo-forked" viewbox="0 0 10 16" version="1.1" width="10" height="16" aria-hidden="true"></svg><path fill-rule="evenodd" d="M8 1a1.993 1.993 0 0 0-1 3.72V6L5 8 3 6V4.72A1.993 1.993 0 0 0 2 1a1.993 1.993 0 0 0-1 3.72V6.5l3 3v1.78A1.993 1.993 0 0 0 5 15a1.993 1.993 0 0 0 1-3.72V9.5l3-3V4.72A1.993 1.993 0 0 0 8 1zM2 4.2C1.34 4.2.8 3.65.8 3c0-.65.55-1.2 1.2-1.2.65 0 1.2.55 1.2 1.2 0 .65-.55 1.2-1.2 1.2zm3 10c-.66 0-1.2-.55-1.2-1.2 0-.65.55-1.2 1.2-1.2.65 0 1.2.55 1.2 1.2 0 .65-.55 1.2-1.2 1.2zm3-10c-.66 0-1.2-.55-1.2-1.2 0-.65.55-1.2 1.2-1.2.65 0 1.2.55 1.2 1.2 0 .65-.55 1.2-1.2 1.2z"></path> para crear su propia copia de repositorio en su cuenta de GitHub. Una vez bifurcada, eres responsable de mantener actualizada la copia del repositorio con el repositorio de TensorFlow ascendente.

#### Clona tu repositorio

Descargue una copia de *su* <var>nombre de usuario</var> / repositorio de documentos remoto en su máquina local. Este es el directorio de trabajo donde realizará cambios:

<pre class="prettyprint lang-bsh">&lt;code class = &quot;devsite-terminal&quot;&gt; GL_CODE_13 &lt;/code&gt;
&lt;code class = &quot;devsite-terminal&quot;&gt; GL_CODE_14 &lt;/code&gt;
</pre>

#### Agregue un repositorio ascendente para mantenerse actualizado (opcional)

Para mantener su repositorio local sincronizado con `tensorflow/docs` , agregue un control remoto *ascendente* para descargar los últimos cambios.

Nota: asegúrese de actualizar su repositorio local *antes de* comenzar una contribución. Las sincronizaciones periódicas en sentido ascendente reducen la posibilidad de un <a href="https://help.github.com/articles/resolving-a-merge-conflict-using-the-command-line" class="external">conflicto de fusión</a> cuando envías tu solicitud de extracción.

Agregar un control remoto:

<pre class="prettyprint lang-bsh">&lt;code class = &quot;devsite-terminal&quot;&gt; GL_CODE_16 &lt;/code&gt;

# Ver repositorios remotos
&lt;code class = &quot;devsite-terminal&quot;&gt; GL_CODE_17 &lt;/code&gt;
origen git@github.com: &lt;var&gt; nombre de usuario &lt;/var&gt; /docs.git (buscar)
origen git@github.com: &lt;var&gt; nombre de usuario &lt;/var&gt; /docs.git (push)
&lt;var&gt; aguas arriba &lt;/var&gt; git@github.com: tensorflow / docs.git (buscar)
&lt;var&gt; aguas arriba &lt;/var&gt; git@github.com: tensorflow / docs.git (push)
</pre>

Actualizar:

<pre class="prettyprint lang-bsh">&lt;code class = &quot;devsite-terminal&quot;&gt; GL_CODE_18 &lt;/code&gt;
&lt;code class = &quot;devsite-terminal&quot;&gt; GL_CODE_19 &lt;/code&gt;

&lt;code class = &quot;devsite-terminal&quot;&gt; GL_CODE_20 &lt;/code&gt; # Envía cambios a tu cuenta de GitHub (por defecto es el origen)
</pre>

### Flujo de trabajo de GitHub

#### 1. Crea una nueva rama

Después de actualizar su repositorio desde `tensorflow/docs` , cree una nueva rama desde la rama *maestra* local:

<pre class="prettyprint lang-bsh">&lt;code class = &quot;devsite-terminal&quot;&gt; GL_CODE_22 &lt;/code&gt;

&lt;code class = &quot;devsite-terminal&quot;&gt; GL_CODE_23 &lt;/code&gt; # Lista de sucursales locales
Maestro
* &lt;var&gt; nombre-característica &lt;/var&gt;
</pre>

#### 2.Haz cambios

Edite archivos en su editor favorito y siga la [guía de estilo de la documentación de TensorFlow](./docs_style.md) .

Confirme su cambio de archivo:

<pre class="prettyprint lang-bsh"># Ver cambios
&lt;code class = &quot;devsite-terminal&quot;&gt; GL_CODE_24 &lt;/code&gt; # Vea qué archivos han cambiado
&lt;code class = &quot;devsite-terminal&quot;&gt; GL_CODE_25 &lt;/code&gt; # Ver cambios dentro de los archivos

&lt;code class = &quot;devsite-terminal&quot;&gt; GL_CODE_26 &lt;/code&gt;
&lt;code class = &quot;devsite-terminal&quot;&gt; GL_CODE_27 &lt;/code&gt;
</pre>

Agregue más confirmaciones, según sea necesario.

#### 3. Cree una solicitud de extracción

Sube tu sucursal local a tu repositorio remoto de GitHub (github.com/ <var>username</var> / docs):

<pre class="prettyprint lang-bsh">&lt;code class = &quot;devsite-terminal&quot;&gt; GL_CODE_28 &lt;/code&gt;
</pre>

Una vez que se completa el envío, un mensaje puede mostrar una URL para enviar automáticamente una solicitud de extracción al repositorio ascendente. De lo contrario, vaya al repositorio de <a href="https://github.com/tensorflow/docs" class="external">tensorflow / docs</a> , o su propio repositorio, y GitHub le pedirá que cree una solicitud de extracción.

#### 4. Revisión

Los mantenedores y otros colaboradores revisarán su solicitud de extracción. Participe en la discusión y realice los cambios solicitados. Cuando se apruebe su solicitud de extracción, se combinará con el repositorio de documentos de TensorFlow ascendente.

Éxito: sus cambios se han aceptado en la documentación de TensorFlow.

Hay un paso de publicación independiente para actualizar [tensorflow.org](https://www.tensorflow.org) desde el repositorio de GitHub. Por lo general, los cambios se agrupan y el sitio se actualiza con una frecuencia regular.

## Cuadernos interactivos

Si bien es posible editar el archivo JSON del cuaderno con el <a href="https://help.github.com/en/articles/editing-files-in-your-repository" class="external">editor de archivos basado en web</a> de GitHub, no se recomienda ya que un JSON con formato incorrecto puede dañar el archivo. Asegúrese de probar el portátil antes de enviar una solicitud de extracción.

<a href="https://colab.research.google.com/notebooks/welcome.ipynb" class="external">Google Colaboratory</a> es un entorno de cuaderno alojado que facilita la edición y ejecución de la documentación del cuaderno. Los cuadernos en GitHub se cargan en Google Colab pasando la ruta a la URL de Colab, por ejemplo, el cuaderno ubicado en GitHub aquí: <a href="https://github.com/tensorflow/docs/blob/master/site/en/tutorials/keras/classification.ipynb">https://github.com/tensorflow/docs/blob/master/site/en/tutorials/keras /classification.ipynb</a><br> se puede cargar en Google Colab en esta URL: <a href="https://colab.research.google.com/github/tensorflow/docs/blob/master/site/en/tutorials/keras/classification.ipynb">https://colab.research.google.com/github/tensorflow/docs/blob/master/site/en/tutorials/keras/classification.ipynb</a>

<!-- github.com path intentionally formatted to hide from import script. -->

Hay una extensión <a href="https://chrome.google.com/webstore/detail/open-in-colab/iogfkhleblhcpcekbiedikdehleodpjo" class="external">Open in Colab</a> Chrome que realiza esta sustitución de URL cuando se navega por un cuaderno en GitHub. Esto es útil al abrir un cuaderno en su bifurcación de repositorio, porque los botones superiores siempre se vinculan a la rama `master` TensorFlow Docs.

### Formateo del cuaderno

Para crear una nueva libreta, copie y edite la <a href="https://github.com/tensorflow/docs/blob/master/tools/templates/notebook.ipynb" external="class">plantilla de libreta de TensorFlow</a> .

Los cuadernos se almacenan en disco como JSON y las diversas implementaciones de cuadernos dan formato al JSON de forma diferente. Las herramientas de diferenciación y el control de versiones no manejan esto muy bien, por lo que TensorFlow Docs impone un formato de cuaderno estándar.

Utilice el comando `nbfmt` para aplicar este formato:

```
# Install the tensorflow-docs package:
$ python3 -m pip install -U [--user] git+https://github.com/tensorflow/docs

# Format individual notebooks:
$ python3 -m tensorflow_docs.tools.nbfmt ./path/to/notebook.ipynb [...]

# Or a directory of notebooks:
$ python3 -m tensorflow_docs.tools.nbfmt ./path/to/notebooks/
```

Por las mismas razones, la salida del cuaderno debe borrarse antes del envío (excepto en algunos casos especiales). En Colab, la opción "salidas privadas" se usa para hacer cumplir esto. Otras implementaciones de portátiles no reconocen esta opción. Puede borrar las salidas pasando `--preserve_outputs=False` a `nbfmt` :

```
$ python3 -m tensorflow_docs.tools.nbfmt --preserve_outputs=False \
    path/to/notebooks/example.ipynb
```

### Editar en Colab

Dentro del entorno de Google Colab, haga doble clic en las celdas para editar texto y bloques de código. Las celdas de texto usan Markdown y deben seguir la [guía de estilo de documentos de TensorFlow](./docs_style.md) .

Descargue archivos de cuaderno de Colab con *Archivo> Descargar .pynb* . Confirme este archivo en su [repositorio de Git local](##set_up_a_local_git_repo) y envíe una solicitud de extracción.

Para crear una nueva libreta, copie y edite la <a href="https://github.com/tensorflow/docs/blob/master/tools/templates/notebook.ipynb" external="class">plantilla de libreta de TensorFlow</a> .

### Flujo de trabajo Colab-GitHub

En lugar de descargar un archivo de cuaderno y usar un flujo de trabajo de Git local, puede editar y actualizar su repositorio de GitHub bifurcado directamente desde Google Colab:

1. En su repositorio bifurcado de <var>nombre de usuario</var> / documentos, use la IU web de GitHub para <a href="https://help.github.com/articles/creating-and-deleting-branches-within-your-repository" class="external">crear una nueva rama</a> .
2. Navegue hasta el archivo del cuaderno para editar.
3. Abra el cuaderno en Google Colab: use el intercambio de URL o la extensión *Abrir en Colab* Chrome.
4. Edite el cuaderno en Colab.
5. Confirme los cambios en su repositorio desde Colab con *Archivo> Guardar una copia en GitHub ....* El cuadro de diálogo de guardado debe vincularse al repositorio y la rama correspondientes. Agrega un mensaje de confirmación significativo.
6. Después de guardar, busque su repositorio o el repositorio <a href="https://github.com/tensorflow/docs" class="external">tensorflow / docs</a> , GitHub debería solicitarle que cree una solicitud de extracción.
7. Los encargados de mantenimiento revisan la solicitud de extracción.

Éxito: sus cambios se han aceptado en la documentación de TensorFlow.

## Traducciones comunitarias

Las traducciones de la comunidad son una excelente manera de hacer que TensorFlow sea accesible en todo el mundo. Para actualizar una traducción, busque o agregue un archivo en el [directorio de idioma](https://github.com/tensorflow/docs/tree/master/site) que coincida con la misma estructura de directorio del directorio `en/` . Los documentos en inglés son la *fuente de la verdad* y las traducciones deben seguir estas guías lo más cerca posible. Dicho esto, las traducciones se escriben para las comunidades a las que sirven. Si la terminología, la redacción, el estilo o el tono en inglés no se traducen a otro idioma, utilice una traducción adecuada para el lector.

Nota: La referencia de la API *no* está traducida para tensorflow.org.

Hay grupos de documentos específicos del idioma que facilitan la organización de los contribuyentes de traducción. Únase si es autor, revisor o simplemente está interesado en crear contenido de TensorFlow.org para la comunidad:

- Chino (simplificado): [docs-zh-cn@tensorflow.org](https://groups.google.com/a/tensorflow.org/forum/#!forum/docs-zh-cn)
- Italiano: [docs-it@tensorflow.org](https://groups.google.com/a/tensorflow.org/forum/#!forum/docs-it)
- Japonés: [docs-ja@tensorflow.org](https://groups.google.com/a/tensorflow.org/forum/#!forum/docs-ja)
- Coreano: [docs-ko@tensorflow.org](https://groups.google.com/a/tensorflow.org/forum/#!forum/docs-ko)
- Ruso: [docs-ru@tensorflow.org](https://groups.google.com/a/tensorflow.org/forum/#!forum/docs-ru)
- Turco: [docs-tr@tensorflow.org](https://groups.google.com/a/tensorflow.org/forum/#!forum/docs-tr)

### Revisar notificaciones

Todas las actualizaciones de la documentación requieren una revisión. Para colaborar de manera más eficiente con las comunidades de traducción de TensorFlow, aquí hay algunas formas de mantenerse al tanto de la actividad específica del idioma:

- Únase a un grupo de idiomas mencionado anteriormente para recibir un correo electrónico para cualquier solicitud de extracción *creada* que toque <code><a data-md-type="raw_html" href="https://github.com/tensorflow/docs/tree/master/site">site/<var data-md-type="raw_html">lang</var></a></code> directorio para ese idioma.
- Agregue su nombre de usuario de GitHub al archivo `site/<lang>/REVIEWERS` para obtener etiquetas de comentario automáticamente en una solicitud de extracción. Cuando se etiqueta como comentario, GitHub le enviará notificaciones de todos los cambios y discusiones en esa solicitud de extracción.

### Mantenga el código actualizado en las traducciones

Para un proyecto de código abierto como TensorFlow, mantener la documentación actualizada es un desafío. Después de hablar con la comunidad, los lectores de contenido traducido tolerarán el texto un poco desactualizado, pero el código desactualizado es frustrante. Para que sea más fácil mantener el código sincronizado, utilice la herramienta [nb-code-sync](https://github.com/tensorflow/docs/blob/master/tools/nb_code_sync.py) para los cuadernos traducidos:

<pre class="prettyprint lang-bsh">&lt;code class = &quot;devsite-terminal&quot;&gt; GL_CODE_38 &lt;/code&gt;
</pre>

Este script lee las celdas de código de un cuaderno de idiomas y las compara con la versión en inglés. Después de eliminar los comentarios, compara los bloques de código y actualiza el cuaderno de idiomas si son diferentes. Esta herramienta es particularmente útil con un flujo de trabajo interactivo de git para agregar selectivamente trozos del archivo a la confirmación usando: `git add --patch site/lang/notebook.ipynb`
