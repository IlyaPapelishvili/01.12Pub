# Contribuir a la documentación de la API de TensorFlow

## Cadenas de documentos comprobables

TensorFlow usa [DocTest](https://docs.python.org/3/library/doctest.html) para probar fragmentos de código en cadenas de documentos de Python. El fragmento debe ser un código Python ejecutable. Para habilitar la prueba, anteponga la línea con `>>>` (tres corchetes en ángulo izquierdo). Por ejemplo, aquí hay un extracto de la función `tf.concat` en el archivo fuente [array_ops.py](https://www.tensorflow.org/code/tensorflow/python/ops/array_ops.py) :

```
def concat(values, axis, name="concat"):
  """Concatenates tensors along one dimension.
  ...

  >>> t1 = [[1, 2, 3], [4, 5, 6]]
  >>> t2 = [[7, 8, 9], [10, 11, 12]]
  >>> concat([t1, t2], 0)
  <tf.Tensor: shape=(4, 3), dtype=int32, numpy=
  array([[ 1,  2,  3],
         [ 4,  5,  6],
         [ 7,  8,  9],
         [10, 11, 12]], dtype=int32)>

  <... more description or code snippets ...>

  Args:
    values: A list of `tf.Tensor` objects or a single `tf.Tensor`.
    axis: 0-D `int32` `Tensor`.  Dimension along which to concatenate. Must be
      in the range `[-rank(values), rank(values))`. As in Python, indexing for
      axis is 0-based. Positive axis in the rage of `[0, rank(values))` refers
      to `axis`-th dimension. And negative axis refers to `axis +
      rank(values)`-th dimension.
    name: A name for the operation (optional).

    Returns:
      A `tf.Tensor` resulting from concatenation of the input tensors.
  """

  <code here>
```

Nota: TensorFlow DocTest usa TensorFlow 2 y Python 3.

### Haga que el código sea comprobable con DocTest

Actualmente, muchas cadenas de documentos usan comillas invertidas (`` `) para identificar el código. Para hacer que el código sea comprobable con DocTest:

- Quite las comillas invertidas (`` `) y use los corchetes izquierdos (>>>) delante de cada línea. Utilice (...) delante de las líneas continuas.
- Agregue una nueva línea para separar los fragmentos de DocTest del texto Markdown para que se procesen correctamente en tensorflow.org.

### Personalizaciones

TensorFlow usa algunas personalizaciones para la lógica de prueba de documentos integrada:

- No se puede comparar valores de coma flotante como texto: valores flotantes se extraen del texto y compararon mediante `allclose` con *liberales `atol` y `rtol` tolerancias.* Esto permite :
    - Documentos más claros: los autores no necesitan incluir todos los decimales.
    - Pruebas más sólidas: los cambios numéricos en la implementación subyacente nunca deberían hacer que una prueba de documentación falle.
- Solo verifica la salida si el autor incluye la salida de una línea. Esto permite que los documentos sean más claros porque los autores generalmente no necesitan capturar valores intermedios irrelevantes para evitar que se impriman.

### Consideraciones sobre las cadenas de documentos

- *En general* : el objetivo de doctest es proporcionar documentación y confirmar que la documentación funciona. Esto es diferente a las pruebas unitarias. Entonces:

    - Mantenga los ejemplos simples.
    - Evite salidas largas o complicadas.
    - Utilice números redondos si es posible.

- *Formato de salida* : la salida del fragmento debe estar directamente debajo del código que genera la salida. Además, la salida en la cadena de documentos debe ser exactamente igual a la salida después de que se ejecute el código. Vea el ejemplo anterior. Además, consulte [esta parte](https://docs.python.org/3/library/doctest.html#warnings) en la documentación de DocTest. Si la salida supera el límite de 80 líneas, puede colocar la salida adicional en la nueva línea y DocTest la reconocerá. Por ejemplo, consulte los bloques de varias líneas a continuación.

- *Globals* : Los módulos <code><code data-md-type="codespan">tf</code> , `np` y `os` siempre están disponibles en DocTest de TensorFlow.

- *Usar símbolos* : En DocTest puede acceder directamente a los símbolos definidos en el mismo archivo. Para usar un símbolo que no está definido en el archivo actual, use la API pública `tf.xxx` TensorFlow en lugar de `xxx` . Como se puede ver en el siguiente ejemplo, <code><code data-md-type="codespan">random.normal</code> se accede a través <code><code data-md-type="codespan">tf.random.normal</code> . Esto se debe a que <code><code data-md-type="codespan">random.normal</code> no es visible en `NewLayer` .

    ```
    def NewLayer():
      “””This layer does cool stuff.

      Example usage:

      >>> x = tf.random.normal((1, 28, 28, 3))
      >>> new_layer = NewLayer(x)
      >>> new_layer
      <tf.Tensor: shape=(1, 14, 14, 3), dtype=int32, numpy=...>
      “””
    ```

- *Valores de coma flotante* : la prueba documental de TensorFlow extrae valores flotantes de las cadenas de resultados y los compara utilizando `np.allclose` con tolerancias razonables ( `atol=1e-6` , `rtol=1e-6` ). De esta manera, los autores no necesitan preocuparse por cadenas de documentos demasiado precisas que causen fallas debido a problemas numéricos. Simplemente pegue el valor esperado.

- *Salida no determinista* : use puntos suspensivos ( `...` ) para las partes inciertas y DocTest ignorará esa subcadena.

    ```
    >>> x = tf.random.normal((1,))
    >>> print(x)
    <tf.Tensor: shape=(1,), dtype=float32, numpy=..., dtype=float32)>
    ```

- *Bloques de varias líneas* : DocTest es estricto sobre la diferencia entre una declaración de una sola línea y una de varias líneas. Tenga en cuenta el uso de (...) a continuación:

    ```
    >>> if x > 0:
    ...   print("X is positive")
    >>> model.compile(
    ...   loss="mse",
    ...   optimizer="adam")
    ```

- *Excepciones* : los detalles de la excepción se ignoran, excepto la excepción que se genera. Vea [esto](https://docs.python.org/3/library/doctest.html#doctest.IGNORE_EXCEPTION_DETAIL) para más detalles.

    ```
    >>> np_var = np.array([1, 2])
    >>> tf.keras.backend.is_keras_tensor(np_var)
    Traceback (most recent call last):
    ...
    ValueError: Unexpectedly found an instance of type `<class 'numpy.ndarray'>`.
    ```

### Prueba en tu máquina local

Hay dos formas de probar el código en la cadena de documentos localmente:

- Si solo está cambiando la cadena de documentos de una clase / función / método, puede probarlo pasando la ruta de ese archivo a [tf_doctest.py](https://www.tensorflow.org/code/tensorflow/tools/docs/tf_doctest.py) . Por ejemplo:

    <pre class="prettyprint lang-bsh">&lt;code class = &quot;devsite-terminal&quot;&gt; GL_CODE_23 &lt;/code&gt;
    </pre>

    Esto lo ejecutará usando su versión instalada de TensorFlow. Para asegurarse de que está ejecutando el mismo código que está probando:

    - Utilice una instalación actualizada [de](https://pypi.org/project/tf-nightly/) `pip install -U tf-nightly`
    - Rebase your pull request onto a recent pull from [TensorFlow's](https://github.com/tensorflow/tensorflow) master branch.

- Si está cambiando el código y la cadena de documentación de una clase / función / método, deberá [compilar TensorFlow desde la fuente](../../install/source.md) . Una vez que esté configurado para compilar desde la fuente, puede ejecutar las pruebas:

    <pre class="prettyprint lang-bsh">&lt;code class = &quot;devsite-terminal&quot;&gt; GL_CODE_25 &lt;/code&gt;
    </pre>

    o

    <pre class="prettyprint lang-bsh">&lt;code class = &quot;devsite-terminal&quot;&gt; GL_CODE_26 &lt;/code&gt;
    </pre>

    El `--module` es relativo a `tensorflow.python` .
