---
title: "¿Por qué, Cómo, Qué? "
date: 2020-08-25T00:00:59-03:00
position: 1
toc: true
toc_label: "Qué hay en esta página"
categories:
  - ciclos
tags:
  - ciclos
  - metodologias
---

Lo primero que uno debe hacer al desarrollar una aplicación es entender el problema.
Muchos de nosotros estamos acostumbrados a pensar en un problema partiendo por la solución. Recibimos un pedido de un cliente, creemos entender todo y nos ponemos a diseñar una posible solución casi inmediatamente. Apenas dedicamos tiempo a preguntarnos cuál es el origen de dicho requerimiento, que ya estamos trabajando en cómo podemos solucionarlo.
Luego, a medida que vamos diagramando lo que podría tener nuestra solución, encontramos cosas nuevas que originalmente no habíamos contemplado. Este es un síntoma de que el problema no quedó claro.

Siguiendo un ejemplo de la gente de Basecamp:

> "Un cliente pidió que agregáramos un módulo de permisos de usuarios más sofisticado. En vez de dedicar un ciclo entero a cumplir con el pedido, nos pusimos a analizar el problema y resultó que alguien había archivado un documento sin saber que, al hacerlo, el documento desaparecía para todos los demás usuarios.
> Con esa información en nuestro poder, en vez de crear una regla para prevenir que algunos usuarios puedan archivar, decidimos agregar una alerta sobre el botón, para explicar cómo esa acción podría afectar al resto.
> El cliente quedó conforme, el problema no ocurrió más y, para nosotros, significó un 1hs de trabajo contra un ciclo de 6 semanas."

Como se ve, el error es de origen y creemos que es el punto más importante que debemos atacar. Por eso vamos a iniciar nuestro trabajo procurando entender el *porqué*.

No podemos pensar en una solución, sin antes entender qué necesitamos resolver. Tenemos que modificar nuestro enfoque y hacernos una serie de preguntas iniciales para entender el problema completo:
- ¿Por qué estamos haciendo esto?
- ¿A quién afecta y a quién le importa?
- ¿Cuándo fue un problema para alguien por última vez? ¿Cuán recurrentemente aparece?

Todas estas preguntas, nos permitirán entender la razón de lo que estamos haciendo, antes de concentrarnos en cómo solucionarlo. Puede incluso que, tras este análisis, nos encontremos con que no había tal problema o que no era lo suficientemente importante como para que merezca dedicarle tiempo ahora.

## Soluciones sin detalles
Una vez identificado el porqué ya podemos movernos a descubrir el *qué* y el *cómo*. El mayor riesgo aquí es entrar en un excesivo nivel de detalle. A más detalles introduzcamos en la solución, más riesgo hay de perder de vista lo importante. Por eso, una de las claves es todavía no meterese con pantallas ni diseños visuales y *trabajar con técnicas/herramientas que permitan moverse con velocidad*.

Para mantener el foco en lo importante y obviar los detalles, vamos a utilizar unos diagramas bastante básicos que incluyen Entidades, Acciones e Interacciones.

La idea es que este diagrama permita responder 3 preguntas que ayuden a definir el qué:
* ¿Cuáles son las componentes o funcionalidades claves?
* ¿Cómo se llega ahí?
* ¿Adónde me lleva?

Para ir directo a un ejemplo, veamos un diagrama que usamos recientemente con SADOP:

![Entidades e Interacciones](/images/entidades_interacciones.png)

Estos diagramas se componen de tres elementos:
- *entidades*: cosas que se accedan, pantallas, procesos complejos, menús, modals, etc. _Son las que se representan arriba, subrayadas_.
- *acciones o puntos de contacto*: son las cosas sobre las que el usuario puede actuar, como botones, campos o textos que leer. _Son todas los items dentro de la entidad_.
- *interacciones*: son las conexiones entre las entidades y/o puntos de contacto. Reflejan cómo el usuario puede llegar de un lugar a otro. _Son las flechas que conectan las entidades_.

En el ejemplo de arriba, el sistema necesita calcular la deuda de un establecimiento para un conjunto de períodos seleccionados. Las entidades son:
- La pantalla de Determinación de deuda, donde el usuario ve los datos del establecimiento y los períodos a seleccionar
- El proceso para calcular la deuda. _Sí, un proceso que quizás no es visible para el usuario, también es una entidad_.
- El cambio de estado.

Lo que está dentro de cada entidad son las acciones o puntos de contacto. En este caso incluye todos los botones, campos, selectores y textos que ve el usuario. Finalmente, las flechas naranjas muestran los posibles flujo. Por ejemplo, en la segunda Entidad, tras confirmar el cálculo de deuda, se genera un cambio de estado.
_Además, en verde, se incluyen algunas notas que ayudan a la comprensión del diagrama_.

Notar que nos estamos abstrayendo de todo lo visual y los detalles. Aquí, lo importante es concentrarse en los elementos y los flujos entre ellos. Todo, desde una notación simple en 2D, que nos permite movernos muy rápidamente entre las preguntas que vayan surgiendo sin entrar en detalles innecesarios.
Si a medida que avanzamos con las entidades y las acciones encontramos que nos faltó algo, podemos borrar y empezar de nuevo. O si encontramos un camino alternativo, podemos plantearlo en segundos. Por esto es fundamental no caer en herramientas sofisticadas antes de tiempo.

## Soluciones visuales
Una vez que tengamos el qué, podemos pasar al *cómo*. Aquí vamos a empezar a usar una técnica más visual, por lo que vamos a hacer algunos bocetos, pero aún sin entrar en muchos detalles. Recordemos que no queremos dedicar tiempo en detalles innecesarios, por lo que vamos a evitar los wireframes o diseños de alta fidelidad.

Por ello, vamos a usar los bocetos de Brocha Gorda. Estos bocetos se llaman así, en referencia al uso de un pincel grueso que impide meterse con detalles finos. El objetivo de estos bocetos es que, quien los ve, pueda hacerse una idea general de la pantalla sin ser demasiado concreto.

![Formulario con explicación al costadito](/images/form.png)

![Otro boceto](/images/list.png)

Como aquí estamos analizando el *cómo*, es fundamental colaborar con quien sepa los detalles técnicos de la implementación, para confirmar si lo que se imaginó es complicado de lograr en los plazos disponibles, o si ya hay algún componente que se pueda reutilizar.

Los bocetos nos ayudarán de muchas maneras:
- Permiten hacernos las preguntas necesarias para completar un buen análisis,
- Sirven para disparar el trabajo de diseño y programación, en paralelo. El/la programador/a hace cosas en el backend mientras el diseñador arma los wireframes,
- Le dan libertad al diseñador sin afectar la experiencia de usuario. Si hubiéramos hecho un wireframe, el diseñador se encontraría con límites de antemano y con menos espacio para su creatividad.

## Bajando los requerimientos
Una vez que está todo definido, debemos armar un documento que denominaremos *Pitch* y será la antesala del *Kickoff*. El pitch debe contener:
- el problema, explicando por qué debemos trabajar en esto,
- el tiempo estimado para resolver este problema (idealmente coincide con el ciclo, pues es lo que estás dispuesto a invertir para solucionar el problema),
- la solución, presentada en un formato que sea sencillo de entender para las personas pero sin limitar sus tareas,
- los detalles que valga la pena remarcar sobre la solución, para evitar futuros problemas,
- lo que queda excluido, si hubiera algo que específicamente se decidió dejar fuera porque no es prioritario o para no comprometer los plazos,

Notar que el pitch no incluye ningún wireframe ni mockup. Esto es a propósito, ya que, en caso de ser necesarios, deben realizarse como parte del ciclo. Eso permitirá que haya mucho más trabajo en equipo entre diseñadores y desarrolladores, lo que vemos como muy positivo.

Por otro lado, presenta el desafío de tener que hacer trabajos visuales en un plazo más acotado de tiempo que también le permita llegar al dev a maquetarlo. Si bien esto es cierto, creemos que el tiempo más profundo que dediquemos al análisis nos permitirá adaptarnos para llegar a trabajos logrados dentro de las 3 semanas que duran los ciclos. *No se trata de llegar a tener X, sino de llegar a la mejor versión de X en un tiempo predefinido*.

El pitch se debe crear en paralelo con el ciclo actual. Es decir, mientras se está desarrollando un ciclo, otra persona (o la misma) debe ir realizando el análisis de las funcionalidades a atacar a futuro.

Una vez que culmina el ciclo actual, hay que escoger un Pitch. Decimos escoger uno, porque podríamos tener varios. Esto es porque quedaron pitches de análisis anteriores o porque una o varias personas realizaron el análisis de diferentes funcionalidades.

![Kickoffeando](/images/kickoffeando.png)

En resumen, las nuevas metodologías plantean trabajar con diferentes niveles de abstracción. En primer lugar, centrarse en el problema y entender qué es lo que queremos solucionar. Luego, trabajar sobre posibles soluciones de una forma rápida, que permita avanzar y retroceder ágilmente, sin caer en detalles que no aportan para la solución del problema. Para ello, tenemos dos alternativas: los diagramas de entidades e interacciones y los bocetos de brocha gorda. Finalmente, la bajada de todo el análisis en un Pitch que explique por qué es importante dedicar tiempo en ello.

En líneas generales, sería algo así:

![Proceso](/images/proceso.png)

