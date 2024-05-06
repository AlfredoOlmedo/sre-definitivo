# Buenas Prácticas, Refactoring, Código Limpio, Deuda técnica

Terminología Buenas Prácticas, Refactoring, Código Limpio, Deuda técnica

### Buenas Prácticas
- Estándares comprobados y verificados
- Resuelven desafíos de escenarios comunes
- Brindan guías fáciles de aprender y comprender
- Permiten Tener una estructura similar para múltiples proyectos

### Código Limpio
- Un código que sigue las buenas prácticas
- Código fácil de entender y analizar
- Código fácil de mantener
- Código fácil de actualizar
- Código fácil de escalar

### Cómo lo logramos
- Cómo logramos código limpio
- Mantener bajo acoplamiento
- Utilizar sintaxis simple y moderna
- Evitar incorporar muchas librerías de terceros
- Distribución de Responsabilidades
- Crecion de componentes pequeños

### Deuda Técnica
- Se refiere a los problemas técnicos que pueda tener un software que son adquiridos durante la fase de desarrollo y que deben ser soluciones en el futuras
- Puede Estar presente en cualquier aspecto de una aplicación como seguridad, rendimiento, escalabilidad etc
- A veces puede resultar más costosa que el mismo desarrollo

### Refactoring
- Proceso de cambios sobre un código para el mejoramiento en cualquier aspecto Rendimiento, seguridad, legibilidad, soporte etc=
- Lo más importante es hacer los cambios manteniendo la lógica de negocio sin afectaciones
- Ser recurrente
- Disminuye la deuda técnica a futuro

### Nombramiento
- Descriptivo y según convencion de desarrollo
- Usar nomenclatura
- Sobre los tipos de nomenclatura/notación en programación:
- Nomenclaturas de programación: camelCase, PascalCase, snake_case
- Tipos de notación: Camelcase, Pascal Case, Snake Case y Kebab Case

### Code Smell
Transmite la sensación de que algo en el codigo esta mal

- Nombramiento
- Métodos y clases grandes
- Demasiados Parámetros
- Número magicos

### Principio DRY
- Don't Repeat Yourself
- El objetivo de este principio es evitar la duplicación de partes de nuestro código
- "Every piece of knowledge must have a single, unambiguous, authoritative representation within a system"
- El código duplicado no siempre es fácil de reconocer o para poder eliminarlo puede que resulte más compleja la solución. una regla de oro en el refactoring es la Regla de tres: repetir una vez el mismo código puede ser aceptable, pero la tercera vez que utilizamos el mismo código es señal inequívoca de que hay que refactorizar y solucionar la duplicación

### Principio Kiss
- Es un acronimo de Keep it simple stupid | Keep it short and simple
- Se trata acerca de Simplificar el código, mantenerlo simple

La mayoría de los sistemas funcionan mejor si se mantienen simples o sencillos a diferencia de aquellos que se hacen complejos de manera innecesaria, muchas veces esta complejidad ocurre cuando se diseñan grandes soluciones para objetivos simples

Es importante tener a consideración que:
- si no comprendes tu propio código es momento de hacer una refactorización
- mantenlo simple

Ejemplos de complejidad innecesaria:
- incluir bibliotecas enormes en el proyecto cuando solo se necesita un par de funciones de ellas
- Abstracción excesiva en el código
- Funciones que resultan enormes por la lógica que contienen
- Anidaciones de condicionales que solo cumplen una función

### Usando Try Catch
- Son escenarios excepcionales o inusuales en el código
- se implementa donde se desee devolver un valor específico después de realizar el control
- el rendimiento se ve afectado al capturar la excepción

### Comentarios
- Don't comment bad code, rewrite it "Brian Kernighan"
- No abuses de los comentarios
- Si los comentarios son obvios, no los pongas
- Escribe código fácil de entender como filosofía
- No comentes la trazabilidad de cambios
- Mantén los comentario correctos y claros
- No dejes código comentado

### Recomendaciones
- Lee sobre buenas prácticas
- Realiza code review entre colegas, así como entre compañeros(as) de trabajo
- Realiza refactoring luego de implementar tu código
- Utiliza herramientas que te ayuden a limpiar tu código
- Implementa estándares y prácticas comunes en tu empresa o proyecto