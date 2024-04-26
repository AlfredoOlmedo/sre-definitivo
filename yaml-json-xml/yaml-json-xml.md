# YAML, JSON, XML, CSV

## Archivos de Intercambio de Datos

### YAML (YAML Ain't Markup Language o Yet Another Markup Language)
Es un lenguaje de serialización de datos legible por humanos.
Se utiliza comúnmente para la creación de archivos de configuración y puede usarse junto con todos los lenguajes de programación.

Los archivos YAML utilizan una extensión de archivos *.yml* o *.yaml* y siguen reglas de sintaxis específicas.

No hay símbolos de formato habituales, como llaves, corchetes, etiquetas de cierre o comillas.

En su lugar, los archivos son más sencillos para su lectura, ya que utilizan la sangría al estilo Python para determinar la estructura e indicar la incorporación de un elemento de código dentro de otro.

*Sintaxis:* Basado en la indentación.

*Legibilidad:* Muy legible para humanos.	

*Tipo de Datos:* Compatible con tipos de datos complejos como listas y diccionarios.

*Extensibilidad:* Menos extensible que XML.	

*Uso Principal:* Configuración de aplicaciones, escritura de scripts y almacenamiento de datos.	

### JSON (JavaScript Object Notation)
Es un formato basado en texto estándar para representar datos estructurados en la sintaxis de objetos de JavaScript.

Es comúnmente utilizado para transmitir datos en aplicaciones web.

Los JSON son cadenas, útiles cuando se quiere transmitir datos a través de una red.

Debe ser convertido a un objeto nativo de JavaScript cuando se requiere acceder a sus datos.

*Sintaxis:* Basado en pares clavevalor.

*Legibilidad:* Legible para humanos pero con más marcas de puntuación.

*Tipo de Datos:* Compatible con tipos de datos simples como cadenas, números, booleanos y listas/diccionarios anidados.

*Extensibilidad:* Más extensible que YAML.

*Uso Principal:* Intercambio de datos entre sistemas web y almacenamiento de configuraciones.	

### XML (Extensible Markup Language)
Es un lenguaje de marcado que define un conjunto de reglas para la codificación de documentos.

A diferencia de otros lenguajes de marcado, XML no está predefinido, por lo que debes definir tus propias etiquetas.
El propósito principal del lenguaje es compartir datos a través de diferentes sistemas, como Internet.

*Sintaxis:* Basado en etiquetas y elementos.

*Legibilidad:* Menos legible para humanos debido a las etiquetas de apertura y cierre.

*Tipo de Datos:*  Compatible con cualquier tipo de datos, aunque la estructura de datos generalmente es más rígida.

*Extensibilidad:*  Muy extensible con la definición de esquemas.

*Uso Principal:*  Intercambio de datos entre sistemas, almacenamiento de información estructurada y definición de documentos.

### CSV (Comma Separated Values)
Los archivos CSV (Comma Separated Values o Valores Separados por Comas) tambien son formatos de intercambio de datos.

Un archivo CSV es un tipo de archivo que se utiliza para almacenar datos tabulares, como una hoja de cálculo.

Los datos están organizados en filas y columnas, y cada celda está separada por comas.

Estos archivos son muy útiles para manejar una gran cantidad de datos en formato tabla, sin que ello conlleve sobrecoste computacional alguno. Son tremendamente sencillos de generar y de leer en programas como Excel.

Además, su capacidad de ser exportados y leídos mediante una amplia gama de programas de texto y bases de datos, hace que sean prácticamente universales.

Por lo tanto, al igual que JSON, XML y YAML, los archivos CSV son una forma común de almacenar y transferir datos estructurados.

*Diferencias con YAML, JSON y XML:* 
Los CSV no admiten una estructura jerárquica como los diccionarios o árboles de JSON o XML. En los CSV, los datos se organizan en filas y columnas simples.

No tienen la capacidad de almacenar tipos de datos complejos como listas o diccionarios como YAML o JSON.

*Tipos:* Los CSV pueden contener una variedad de tipos de datos, incluyendo:
- Números
- Texto
- Fechas
- Valores booleanos

*Usos:*  Los CSV son comúnmente utilizados en una variedad de aplicaciones, incluyendo Intercambio de datos entre sistemas y programas. Almacenamiento de datos en hojas de cálculo y bases de datos simples. Importación y exportación de datos desde y hacia aplicaciones y herramientas de análisis de datos.

## Ejemplos

**YAML**
```
nombre  Juan
edad  30
ciudad  Ciudad de México
```

**JSON**
```
{
  "nombre"  "Juan",
  "edad"  30,
  "ciudad"  "Ciudad de México"
}
```

**XML**
```
<persona>
  <nombre>Juan</nombre>
  <edad>30</edad>
  <ciudad>Ciudad de México</ciudad>
</persona>
```

**CSV**
```
Nombre,Edad,Ciudad
Juan,30,Ciudad de México
María,25,Barcelona
Carlos,35,Londres
```

## Ejemplos

## Arrays

**YAML Arrays**
```
numeros 
   1
   2
   3
```

**JSON Arrays**
```
{
  "numeros"  [1, 2, 3]
}
```

**XML Arrays**
```
<numeros>
  <numero>1</numero>
  <numero>2</numero>
  <numero>3</numero>
</numeros>
```

## Listas

**YAML Listas**
```
frutas 
   manzana
   plátano
   naranja
```

**JSON Listas**
```
{
  "frutas"  ["manzana", "plátano", "naranja"]
}
```

**XML Listas**
```
<frutas>
  <fruta>manzana</fruta>
  <fruta>plátano</fruta>
  <fruta>naranja</fruta>
</frutas>
```

## Diccionarios

**YAML Diccionarios**
```
persona 
  nombre  Juan
  edad  30
```

**JSON Diccionarios**
```
{
  "persona"  {
    "nombre"  "Juan",
    "edad"  30
  }
}
```

**XML Diccionarios**
```
<persona>
  <nombre>Juan</nombre>
  <edad>30</edad>
</persona>
```

## Mapas

**YAML Mapas**
```
dirección 
  calle  Calle Principal
  ciudad  Ciudad de México
  país  México
```

**JSON Mapas**
```
{
  "dirección"  {
    "calle"  "Calle Principal",
    "ciudad"  "Ciudad de México",
    "país"  "México"
  }
}
```

**XML Mapas**
```
<dirección>
  <calle>Calle Principal</calle>
  <ciudad>Ciudad de México</ciudad>
  <país>México</país>
</dirección>
```