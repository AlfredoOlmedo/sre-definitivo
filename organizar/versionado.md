# Versionado

## Versionado del Software
El versionado de software es el proceso de asignación de un nombre, código o número único, a un software para indicar su nivel de desarrollo

## General
En tecnología, es muy importante el ciclo de vida y su continua mejora, es por ello que constantemente existen actualizaciones las cuales van desde Grandes Mejoras y Correcciones a Pequeñas y detalladas.

Cada empresa tiene diferentes políticas respecto al ciclo de vida y adopción de las mismas pero generalmente por convención se parte de estas

- Versionado Tradicional
- Otros Sistemas de Versionado

## Versionado tradicional
Generalmente se asigna dos números que van incrementando conforme el desarrollo del software y aumente y se requiera la asignación de un nuevo nombre, código o número único, Aunque menos habituales, también puede indicarse otro número más, micro y la fase de desarrollo en que se encuentra el software.

- Mayor Cuando sufre grandes cambios y mejoras
- Menor Cuando sufre pequeños cambios y/o correcciones de errores
- Micro Cuando solo es una corrección de algo menor
- Fase Se indica si se encuentra en una fase de desarrollo que no sea la final o estable, es decir una fase inestable o en pruebas, se suele indicar con un guión seguido de la fase correspondiente en minúsculos, o un espacio seguido de la fase. Puede haber varias versiones de una misma fase, para indicar el avance en el desarrollo del software pero manteniendo la fase para indicar que todavias es inestable, indicándose añadiendo un número al final del nombre de la fase que va incrementando conforme se publiquen nuevas versiones de esta fase.

## Otros sistemas de Versionado
Existen sistemas que No siguen el versionado tradicional Algunos proyectos, como Ubuntu, usan los dígitos para indicar la fecha de lanzamiento.

Otros proyectos, como arcades, usan códigos varipos, finalizando en una fecha y la versión del parche

En algunos proyectos de desarrollo ágil, como Google Chrome, se usa una versión similar al tradicional. Aunque los cambios en el dígito mayor indican cambios relevantes en el Software, no son tantos como es habitual en el versionado tradicional

Ejemplos

Con Fechas
```
15.4 - Anio.Mes
15.4.2 - Anio.Mes.Menor
2015.1.2 - Anio.Mayor.Menor
```

Usando Arcades
```
Codigo.Idioma.Mueble.Modificador.AnioMesDiaParche - ABC.S.A.0.2021092501
```
Desarrollo Ágil Mayor.Menor.Construccion.Parche

## Versiones por estabilidad
Estabilidad de proyecto, Alpha, Beta
`Alpha:` Es una versión inestable que es muy probable que tenga amplio margen de mejora, pero que está en una etapa de revisión para encontrar bugs, mejoras y funcionalidad, en la mayoría de los casos se dice que está casi lista
Ejemplos
```
- 1.0Alpha
- 1.1a1
- 1.0a2
```

`Beta:` Es una versión más estable, en la que contamos con el producto en su totalidad, en esta se realizan pruebas de rendimiento, usabilidad y funcionamiento de algunos módulos para ver cómo funciona bajo un ambiente no tan controlado. un nombre común es BetaTester
Ejemplo
```
- 2.0Beta
- 2.0b
- 2.0b1
```

## Conclusión
No existe una Regla universal y esta depende de cada política de las empresas, pero siempre es buena práctica determinar un sistema de versionado de software y documentar y conforme se itere y mejore ir versionando.