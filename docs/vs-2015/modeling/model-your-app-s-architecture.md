---
title: Modelar la aplicación&#39;arquitectura s | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML, modeling architecture
ms.assetid: aedce746-9df5-49e1-9662-67eb1b83d313
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0a6e551dd2f045684168947d2c5a4e63089928c1
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60098446"
---
# <a name="model-your-app39s-architecture"></a>Modelar la aplicación&#39;arquitectura s
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para ayudar a garantizar que el sistema de software o la aplicación cumple sus usuarios necesidades, puede crear modelos en Visual Studio como parte de la descripción de la estructura general y el comportamiento de su aplicación o sistema de software. A través de los modelos, también puede describir los patrones que se usan a lo largo de todo el proceso de diseño. Estos modelos le ayudan a entender la arquitectura existente, a analizar los cambios y a comunicar sus intenciones con claridad.  
  
 Para ver qué versiones de Visual Studio admiten esta característica, vea [Compatibilidad de versiones con las herramientas de arquitectura y modelado](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 El propósito de un modelo es reducir las ambigüedades que se producen en las descripciones con el lenguaje natural y ayudarle a usted y a sus colegas a visualizar el diseño y a analizar diseños alternativos. El modelo debe usarse conjuntamente con otros documentos o explicaciones. Por sí mismo, un modelo no constituye una especificación completa de la arquitectura.  
  
> [!NOTE]
>  A lo largo de este tema, el término “sistema” hace referencia al software que se está desarrollando. Puede ser una colección grande de muchos componentes de hardware y software, una única aplicación o una parte de una aplicación.  
  
 La arquitectura de un sistema puede dividirse en dos áreas:  
  
- [Diseño de alto nivel](#Structure). Aquí se describen los componentes principales y el modo en que interactúan entre sí para satisfacer cada uno de los requisitos. Si el sistema es grande, cada componente puede tener su propio diseño de alto nivel donde se muestra su composición a partir de componentes más pequeños.  
  
- [Patrones de diseño](#Patterns) y convenciones que se usan a lo largo de los diseños de los componentes. Un modelo describe un determinado enfoque para lograr un objetivo de programación. Si se usan los mismos modelos a lo largo de un diseño completo, el equipo puede reducir el costo que suponen los cambios y el desarrollo de nuevo software.  
  
## <a name="Structure"></a> Diseño de alto nivel  
 En un diseño de alto nivel se describen los componentes principales del sistema y el modo en que interactúan entre sí para lograr los objetivos del diseño. En el desarrollo del diseño de alto nivel están implicadas las actividades de la lista siguiente, aunque no necesariamente en un orden determinado.  
  
 Si está actualizando código existente, puede comenzar por describir los componentes principales. Asegúrese de que comprende los cambios que deben realizarse en los requisitos de los usuarios y, a continuación, agregue o modifique las interacciones entre los componentes. Si está desarrollando un sistema nuevo, comience por identificar las características principales de las necesidades de los usuarios. A continuación, puede analizar las secuencias de interacciones de los casos de uso principales y, posteriormente, consolidar las secuencias en un diseño de componentes.  
  
 En cualquier caso, resulta útil desarrollar en paralelo las diferentes actividades y desarrollar el código y las pruebas en una fase inicial. No intente completar uno de estos aspectos antes de comenzar con otro. Normalmente, a medida que escriba y pruebe el código, irán cambiando los requisitos y su concepción sobre la mejor manera de diseñar el sistema. Por tanto, debe empezar por concebir y codificar las características principales de los requisitos y el diseño. Ocúpese de los detalles en posteriores iteraciones del proyecto.  
  
- [Descripción de los requisitos](#Requirements). El punto inicial de cualquier diseño es describir claramente las necesidades de los usuarios.  
  
- [Modelos arquitectónicos](#BigDecisions). Son las elecciones que hace respecto a las tecnologías y elementos arquitectónicos básicos del sistema.  
  
- [Componentes y sus Interfaces](#Components). Puede dibujar diagramas de componentes en los que se muestren los elementos principales del sistema y las interfaces a través de las que interactúan entre sí. Las interfaces de cada componente incluyen todos los mensajes que se identificaron en los diagramas de secuencia.  
  
- [Interacciones entre componentes](#Interactions). Para cada caso de uso, evento o mensaje entrante, puede dibujar un diagrama de secuencia en el que se muestre cómo interactúan los componentes principales del sistema para lograr la respuesta necesaria.  
  
- [Modelo de datos de los componentes e Interfaces](#Data). Puede dibujar diagramas de clases para describir la información que se pasa entre los componentes y que se almacena en los componentes.  
  
## <a name="Requirements"></a> Descripción de los requisitos  
 La forma más eficaz de desarrollar el diseño de alto nivel de una aplicación completa es hacerlo junto con un modelo de requisitos y otra descripción de las necesidades de los usuarios. Para obtener más información acerca de los modelos de requisitos, consulte [modelar los requisitos del usuario](../modeling/model-user-requirements.md).  
  
 Si el sistema que está desarrollando es un componente de un sistema más grande, es posible que parte de los requisitos, o todos ellos, puedan expresarse en interfaces programáticas.   
  
 El modelo de requisitos proporciona estos elementos de información esenciales:  
  
- Interfaces proporcionadas. En una interfaz proporcionada aparecen los servicios u operaciones que el sistema o componente debe proporcionar a los usuarios, ya se trate de individuos o de otros componentes de software.  
  
- Interfaces necesarias. En una interfaz necesaria se muestran los servicios u operaciones que el sistema o componente puede usar. En algunos casos, podrá diseñar todos estos servicios como parte de su propio sistema. En otros casos, sobre todo si está diseñando un componente que se puede combinar con otros componentes en numerosas configuraciones, la interfaz necesaria se establecerá en función de consideraciones externas.  
  
- Requisitos de calidad del servicio. Rendimiento, seguridad, solidez y otros objetivos y restricciones que el sistema debe satisfacer.  
  
  El modelo de requisitos se escribe desde la perspectiva de los usuarios del sistema, ya se trate de individuos u otros componentes de software. Ellos no saben nada sobre el funcionamiento interno del sistema. En cambio, el objetivo de un modelo arquitectónico es describir los mecanismos internos y mostrar cómo satisfacen las necesidades de los usuarios.  
  
  Resulta útil mantener por separado los requisitos y los modelos arquitectónicos porque así es más fácil analizar los requisitos con los usuarios. También ayuda a refactorizar el diseño y a considerar arquitecturas alternativas mientras los requisitos se mantienen sin cambios.  
  
  Puede separar los requisitos y los modelos arquitectónicos de dos maneras alternativas:  
  
- Manteniéndolos en la misma solución, pero en proyectos diferentes. Aparecerán como modelos independientes en el Explorador de modelos UML. Varios miembros del equipo podrán trabajar en paralelo con los modelos. Pueden crearse tipos limitados de trazas entre los modelos.  
  
- Situándolos en el mismo modelo UML, pero en paquetes diferentes. De este modo, resulta más fácil realizar el seguimiento de las dependencias entre los modelos, aunque impide que varias personas trabajen en el modelo a la vez. Además, un modelo muy grande tardará mucho más tiempo en cargarse en Visual Studio. Este enfoque resulta, por tanto, menos apropiado para proyectos grandes.  
  
  El nivel de detalle que debe usarse en los requisitos o en un modelo arquitectónico dependerá de la escala del proyecto y del tamaño y distribución del equipo. Un equipo reducido que trabaje en un proyecto pequeño podría simplemente trazar un diagrama de clases de los conceptos de negocio y algunos modelos de diseño; un proyecto grande distribuido en varias regiones necesitaría mucho más detalle.  
  
## <a name="BigDecisions"></a> Patrones de arquitectura  
  En una fase inicial de desarrollo, tendrá que elegir las principales tecnologías y elementos en los que se va a basar el diseño. Las áreas en las que deben tomarse estas decisiones son, entre otras:  
  
- Las tecnologías de base; por ejemplo, la elección entre una base de datos y un sistema de archivos, la elección entre una aplicación de red y un cliente web, etc.  
  
- Los marcos; por ejemplo, la elección entre Windows Workflow Foundation o ADO.NET Entity Framework.  
  
- El método de integración; por ejemplo, la elección entre un bus de servicio de empresa o un canal punto a punto.  
  
  Estas opciones a menudo están determinadas por los requisitos de calidad del servicio, como la escala y la flexibilidad, y pueden hacerse antes de que se conozcan los detalles de los requisitos. En un sistema grande, la configuración del hardware y la configuración del software están estrechamente relacionadas.  
  
  Las elecciones que haga afectarán al modo en que se usa e interpreta el modelo arquitectónico. Por ejemplo, en un sistema que usa una base de datos, las asociaciones de un diagrama de clases pueden representar las relaciones o claves externas de la base de datos, mientras que en un sistema basado en archivos XML, las asociaciones pueden indicar las referencias cruzadas que usan XPath. En un sistema distribuido, los mensajes de un diagrama de secuencia pueden representar los mensajes de una conexión; en una aplicación independiente, pueden representar las llamadas de función.  
  
## <a name="Components"></a> Componentes y sus Interfaces  
 Las principales recomendaciones de esta sección son las siguientes:  
  
- Cree diagramas de componentes para mostrar los elementos principales del sistema.  
  
- Dibuje dependencias entre los componentes o sus interfaces para mostrar la estructura del sistema.  
  
- Use las interfaces de los componentes para mostrar los servicios que cada componente proporciona o requiere.  
  
- En un diseño grande, puede dibujar diagramas independientes para descomponer cada componente en elementos más pequeños.  
  
  Estos aspectos se desarrollan en el resto de esta sección.  
  
### <a name="components"></a>Componentes  
 Las vistas centrales de un modelo arquitectónico son los diagramas de componentes, donde se muestran los elementos primarios del sistema y cómo dependen unos de otros. Para obtener más información acerca de los diagramas de componentes, consulte [diagramas de componentes UML: referencia](../modeling/uml-component-diagrams-reference.md).  
  
 ![Diagrama de componentes UML que muestra las partes](../modeling/media/uml-barecomponent.png "UML_BareComponent")  
  
 Un diagrama de componentes típico de un sistema grande podría incluir componentes como estos:  
  
- Presentación. Es el componente que proporciona acceso al usuario, normalmente mediante la ejecución en un explorador web.  
  
- Componentes del servicio web. Proporcionan conexiones entre clientes y servidores.  
  
- Controladores de casos de uso. Dirige al usuario a través de los pasos de cada escenario.  
  
- Núcleo del negocio. Contiene clases que se basan en las clases del modelo de requisitos, implementa las operaciones clave e impone las restricciones del negocio.  
  
- Base de datos. Almacena los objetos de negocio.  
  
- Componentes de registro y control de errores.  
  
### <a name="dependencies-between-components"></a>Dependencias entre componentes  
 Además de los propios componentes, puede mostrar las dependencias entre ellos. Una flecha de dependencia entre dos componentes indica que los cambios que se realicen en el diseño de uno de ellos pueden afectar al diseño del otro. Esto normalmente ocurre porque uno de los componentes usa los servicios o funciones proporcionados por el otro componente, ya sea de forma directa o indirecta.  
  
 Una arquitectura bien estructurada tiene una organización clara de dependencias en las que su cumplen estas condiciones:  
  
- El mapa de código no incluye bucles.  
  
- Los componentes pueden organizarse en capas en las que cada dependencia sale de un componente de una capa hacia un componente de la siguiente capa. Todas las dependencias entre dos capas van en la misma dirección.  
  
  Puede mostrar las dependencias directamente entre los componentes o puede mostrar las dependencias entre las interfaces necesarias y proporcionadas que se asocian a los componentes. Mediante las interfaces, puede definir qué operaciones se usan en cada dependencia. Normalmente, las dependencias entre componentes se muestran cuando los diagramas se dibujan por primera vez. Posteriormente, a medida que se agrega más información, se sustituyen por dependencias entre interfaces. Las dos versiones son descripciones correctas del software, pero la versión con interfaces proporciona más detalles que la versión anterior.  
  
  La administración de dependencias es muy importante para la generación de un software sostenible. Los diagramas de componentes deben reflejar todas las dependencias del código. Si el código ya existe, asegúrese de que todas las dependencias aparecen en los diagramas. Si el código se está desarrollando, asegúrese de que no contiene dependencias que no estén planeadas en el diagrama de componentes. Para ayudarle a detectar las dependencias del código, puede generar diagramas de capas. Para asegurarse de que se cumplen las restricciones de dependencia planeadas, puede validar el código con los diagramas de capas. Para obtener más información, consulte [diagramas de capas: referencia](../modeling/layer-diagrams-reference.md).  
  
### <a name="interfaces"></a>Interfaces  
 Mediante las interfaces de sus componentes, puede separar los grupos principales de operaciones que proporciona cada componente y asignarles un nombre. Por ejemplo, los componentes de un sistema de ventas basado en web podrían tener una interfaz a través de la cual los clientes compran artículos, una interfaz a través de la cual los proveedores actualizan sus catálogos y una tercera interfaz a través de la cual se administra el sistema.  
  
 Un componente puede tener cualquier número de interfaces proporcionadas y necesarias. En las interfaces proporcionadas se muestran los servicios que proporciona el componente para que los usen otros componentes. En las interfaces necesarias se muestran los servicios que el componente usa en otros componentes.  
  
 Si define tanto interfaces proporcionadas como interfaces necesarias, le será más fácil separar claramente el componente del resto del diseño de modo que pueda usar estas técnicas:  
  
- Coloque el componente en un agente de prueba en el que se simulen los componentes de alrededor.  
  
- Desarrolle el componente independientemente de los demás componentes.  
  
- Vuelva a usar el componente en otros contextos acoplando las interfaces a diferentes componentes.  
  
  Si desea definir la lista de operaciones de una interfaz, puede crear otra vista de la interfaz en un diagrama de clases UML. Para ello, busque la interfaz en el Explorador de modelos UML y arrástrela hasta un diagrama de clases. A continuación, puede agregar operaciones a la interfaz.  
  
  Una operación de una interfaz UML puede representar cualquier mecanismo para invocar el comportamiento de un componente. Podría representar una solicitud de servicio web, una señal o interacción de algún otro tipo o una llamada ordinaria a una función del programa.  
  
  Para determinar qué operaciones se van a agregar, cree diagramas de secuencia en los que se muestre cómo interactúan unos componentes con otros. Consulte [interacciones entre componentes](#Interactions). En cada uno de estos diagramas de secuencia se muestran las interacciones que se producen en un caso de uso diferente. De esta manera, puede ampliar gradualmente la lista de operaciones de la interfaz de cada componente a medida que explora los casos de uso.  
  
### <a name="decomposing-a-component-into-parts"></a>Descomponer un componente en elementos  
 Puede aplicar el procedimiento que se describe en las secciones anteriores a cada componente.  
  
 Dentro de cada componente, puede mostrar sus componentes secundarios como elementos. Un elemento es en realidad un atributo de su componente primario, que es un tipo de clase. Cada elemento tiene su propio tipo, que puede ser un componente. Puede colocar este componente en un diagrama y mostrar sus elementos. Para obtener más información, consulte [diagramas de componentes UML: Directrices](../modeling/uml-component-diagrams-guidelines.md).  
  
 Es útil aplicar esta técnica a todo el sistema. Dibújelo como un componente único y muestre sus componentes principales como elementos. Esto le ayudará a identificar claramente las interfaces de su sistema en el mundo externo.  
  
 A menudo, cuando el diseño de un componente usa otro componente, tiene que decidir si va a representarlo como un elemento o como un componente independiente al que se obtiene acceso a través de una interfaz necesaria.  
  
 Use elementos en las siguientes situaciones:  
  
- El diseño del componente primario siempre debe usar el tipo de componente del elemento. Por lo tanto, el diseño del elemento es intrínseco al diseño del componente primario.  
  
- El componente primario no tiene una existencia concreta propia. Por ejemplo, puede tener un componente conceptual denominado Capa de presentación que represente una colección de componentes reales que controlan vistas e interacciones con el usuario.  
  
  Use componentes independientes a los que se obtiene acceso a través de las interfaces necesarias en estas situaciones:  
  
- El componente que se necesita puede acoplarse a través de sus interfaces a distintos componentes proveedores en tiempo de ejecución.  
  
- El diseño se ha realizado de modo que sería fácil reemplazar un proveedor por otro.  
  
  El uso de interfaces necesarias normalmente es preferible al uso de elementos. Aunque el diseño puede llevar más tiempo, el sistema resultante es más flexible. También es más fácil probar los componentes por separado. Esto permite un grado de acoplamiento menor en los planes de desarrollo.  
  
## <a name="Interactions"></a> Interacciones entre componentes  
 Las principales recomendaciones de esta sección son las siguientes:  
  
- Identifique los casos de uso del sistema.  
  
- En cada caso de uso, dibuje uno o más diagramas para mostrar el modo en que los componentes del sistema logran el resultado requerido gracias a la colaboración entre ellos y con los usuarios. Normalmente, se tratarán de diagramas de secuencia o de actividades.  
  
- Use las interfaces para especificar los mensajes recibidos por cada componente.  
  
- Describa los efectos de las operaciones en las interfaces.  
  
- Repita el procedimiento con cada componente, mostrando cómo interactúan sus elementos.  
  
  Por ejemplo, en un sistema de ventas basado en web, el modelo de requisitos podría definir la compra de un cliente como un caso de uso. Puede crear un diagrama de secuencia para mostrar las interacciones que el cliente tiene con los componentes en la capa de la presentación y para mostrar las interacciones que tiene con los componentes de contabilidad y almacenamiento.  
  
### <a name="identifying-the-initiating-events"></a>Identificar los eventos de iniciación  
  El trabajo realizado por la mayor parte de los sistemas de software puede dividirse cómodamente en las respuestas que da a diferentes entradas o eventos. El evento de iniciación puede ser uno de los eventos siguientes:  
  
- La primera acción de un caso de uso. Podría aparecer en el modelo de requisitos como un paso de un caso de uso o una acción de un diagrama de actividades. Para obtener más información, [diagramas de casos de uso de UML: Directrices](../modeling/uml-use-case-diagrams-guidelines.md) y [diagramas de actividades UML: Directrices](../modeling/uml-activity-diagrams-guidelines.md).  
  
- Un mensaje en una interfaz programática. Si el sistema que está desarrollando es un componente de un sistema mayor, debería describirse como una operación de una de las interfaces del componente. Consulte [componentes y sus Interfaces](#Components).  
  
- Una determinada condición que el sistema supervisa, o un evento periódico como una hora del día.  
  
### <a name="describe-the-computations"></a>Describir los cálculos  
 Dibuje diagramas de secuencia para mostrar la respuesta de los componentes al evento inicial.  
  
 Dibuje una línea de vida para cada instancia del componente que tome parte en una secuencia normal. En algunos casos, podría haber varias instancias de cada tipo. Si ha descrito todo su sistema como un único componente, deberá haber una línea de vida por cada elemento que contenga.  
  
 Para obtener más información, consulte [diagramas de secuencia UML: Directrices](../modeling/uml-sequence-diagrams-guidelines.md).  
  
 Los diagramas de actividades también resultan útiles en algunos casos. Por ejemplo, si los componentes tienen un flujo de datos continuo, puede describirlo como un flujo de objeto. Si el componente tiene un algoritmo complejo, puede describirlo como un flujo de control. Asegúrese de dejar claro qué componente realiza cada acción, por ejemplo, mediante comentarios. Para obtener más información, consulte [diagramas de actividades UML: Directrices](../modeling/uml-activity-diagrams-guidelines.md).  
  
### <a name="specify-the-operations"></a>Especificar las operaciones  
 En los diagramas se muestran las operaciones que realiza cada componente; estas operaciones se representan como mensajes en un diagrama de secuencia o como acciones en un diagrama de actividades.  
  
 Recopile las operaciones de cada componente. Cree interfaces proporcionadas en el componente y agregue las operaciones a las interfaces. Normalmente, se usa una interfaz diferente para cada tipo de cliente. Las operaciones se agregan más fácilmente a las interfaces de **Explorador de modelos UML**. De la misma manera, recopile las operaciones que usa cada componente de los demás componentes y sitúelas en las interfaces necesarias asociadas al componente.  
  
 Resulta útil agregar comentarios a los diagramas de actividades o a los diagramas de secuencia para dar cuenta de lo que se ha logrado después de cada operación. También puede escribir el efecto de cada operación en su **condición posterior Local** propiedad.  
  
### <a name="Data"></a> Modelo de datos de los componentes e Interfaces  
 Defina los parámetros y los valores devueltos de cada operación de las interfaces de los componentes. Cuando las operaciones representan invocaciones como solicitudes de servicio web, los parámetros son esos fragmentos de información que se envían como parte de la solicitud. Cuando se devuelven varios valores de una operación, puede usar parámetros con el **dirección** propiedad establecida en **Out**.  
  
 Cada parámetro y cada valor devuelto tienen un tipo. Puede definir estos tipos mediante los diagramas de clases UML. No tiene que representar en detalle la implementación en estos diagramas. Por ejemplo, si está describiendo los datos que se transmiten en formato XML, puede usar una asociación para representar cualquier tipo de referencia cruzada entre los nodos del código XML y usar las clases para representar los nodos.  
  
 Use los comentarios para describir las restricciones de negocio que presentan las asociaciones y atributos. Por ejemplo, si todos los elementos del pedido de un cliente deben proceder del mismo proveedor, puede describir esta circunstancia mediante referencias a las asociaciones entre los elementos del pedido y los elementos del catálogo de productos, y entre los elementos del catálogo y su proveedor.  
  
## <a name="Patterns"></a> Patrones de diseño  
 Un modelo de diseño es un esquema del modo en que debe diseñarse un determinado aspecto del software, sobre todo uno que se repita en diferentes elementos del sistema. Si adopta un enfoque uniforme en todo el proyecto, puede reducir el costo de diseño, garantizar la coherencia de la interfaz de usuario y reducir la carga que supone la comprensión y modificación del código.  
  
 Algunos modelos de diseño generales, como el modelo Observador, son bien conocidos y están muy extendidos. Asimismo, hay modelos que únicamente pueden aplicarse a su proyecto. Por ejemplo, en un sistema de ventas web, habrá varias operaciones en el código donde se realicen cambios en el pedido de un cliente. Para asegurarse de que el estado del pedido se muestra con precisión en cada etapa, todas estas operaciones deben seguir un protocolo determinado para actualizar la base de datos.  
  
 La parte del trabajo de la arquitectura de software consiste en determinar qué modelos deben adoptarse en todo el diseño. Normalmente se trata de una tarea continua, porque los nuevos modelos y las mejoras de los modelos existentes se detectarán a medida que avance el proyecto. Resulta útil organizar el plan de desarrollo para que pueda ocuparse de cada uno de los principales modelos de diseño en una etapa inicial.  
  
 La mayoría de los modelos de diseño pueden expresarse parcialmente en el código del marco. Parte del modelo puede reducirse hasta requerir al desarrollador que use determinadas clases o componentes, como una capa de acceso a la base de datos que garantice que la base de datos se está administrando correctamente.  
  
 Un modelo de diseño se describe en un documento y normalmente incluye estos elementos:  
  
- Nombre.  
  
- Descripción del contexto en el que es aplicable. ¿Qué criterios debe tener en cuenta un programador al aplicar este modelo?  
  
- Breve explicación del problema que resuelve.  
  
- Modelo de los elementos primarios y sus relaciones. Pueden tratarse de clases o componentes e interfaces, con asociaciones y dependencias entre ellos. Normalmente, los elementos pertenecen a dos categorías:  
  
    - Elementos que el desarrollador debe reproducir en cada elemento del código en el que se usa el modelo. Puede usar tipos de plantilla para describirlos. Para obtener más información, consulte [diagramas de casos de uso de UML: referencia](../modeling/uml-use-case-diagrams-reference.md).  
  
    - Elementos que describen las clases del marco que debe usar el programador.  
  
- Modelo de las interacciones entre los elementos, mediante diagramas de secuencia o actividades.  
  
- Convenciones de nomenclatura.  
  
- Descripción del modo en que el modelo resuelve el problema.  
  
- Descripción de las variaciones que los desarrolladores podrían adoptar.  
  
## <a name="see-also"></a>Vea también  
 [Editar modelos y diagramas UML](../modeling/edit-uml-models-and-diagrams.md)   
 [Visualizar el código](../modeling/visualize-code.md)   
 [Requisitos de usuario del modelo](../modeling/model-user-requirements.md)   
 [Desarrollar pruebas en un modelo](../modeling/develop-tests-from-a-model.md)   
 [Usar modelos en el proceso de desarrollo](../modeling/use-models-in-your-development-process.md)
