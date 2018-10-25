---
title: Modelar los requisitos de usuario | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- requirements
- stories
- UML, modeling requirements
ms.assetid: 359900f8-6d69-493d-bfdf-2c9069c74a26
caps.latest.revision: 30
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: bc0620c06b6fa5b4018b6e027e30a18216454b29
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49863963"
---
# <a name="model-user-requirements"></a>Requisitos del usuario de modelos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Con Visual Studio, es más fácil entender, analizar y comunicar las necesidades de los usuarios a través de diagramas sobre sus actividades, así como la importancia del sistema para ayudarles a lograr sus objetivos. Un modelo de requisitos es un conjunto de estos diagramas, cada uno de los cuales se centra en un aspecto diferente de las necesidades de los usuarios. Para ver una demostración en vídeo, consulte [Modeling the Business Domain](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-3-Modeling-the-Business-Domain/)(Crear modelos del ámbito empresarial).  
  
 Para ver qué versiones de Visual Studio admite cada tipo de modelo, consulte [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Un modelo de requisitos le ayuda a:  
  
- Centrarse en el comportamiento externo del sistema, independientemente de su diseño interno.  
  
- Describir las necesidades de los usuarios y otras partes interesadas con mucha menos ambigüedad que con el lenguaje natural.  
  
- Definir un glosario de términos coherente que puedan usar los usuarios, los desarrolladores y los evaluadores.  
  
- Reducir los vacíos y las incoherencias de los requisitos.  
  
- Reducir el trabajo necesario para responder a los cambios de los requisitos.  
  
- Planear el orden en el que se van a desarrollar las características.  
  
- Usar los modelos como base para las pruebas del sistema, estableciendo una relación inequívoca entre las pruebas y los requisitos. Si cambian los requisitos, esta relación le ayudará a actualizar las pruebas correctamente. Esto garantiza que el sistema cumple los requisitos nuevos.  
  
  Un modelo de requisitos proporciona el máximo beneficio si lo usa para centrar las conversaciones con los usuarios o sus representantes y vuelve a visitarlo al principio de cada iteración. No es necesario completarlo detalladamente antes de escribir el código. Una aplicación parcialmente operativa, aunque esté muy simplificada, suele constituir la base más estimulante para tratar los requisitos con los usuarios. El modelo es un método eficaz para resumir los resultados de estas conversaciones. Para obtener más información, consulte [usar modelos en el proceso de desarrollo](../modeling/use-models-in-your-development-process.md).  
  
> [!NOTE]
>  En estos temas, "sistema" hace referencia al sistema o la aplicación que está desarrollando. Podría ser una colección grande de muchos componentes de hardware y software, una sola aplicación o un componente de software incluido en un sistema de mayor tamaño. En cada caso, el modelo de requisitos describe el comportamiento que es visible desde fuera del sistema, ya sea a través de una API o interfaz de usuario.  
  
## <a name="common-tasks"></a>Tareas comunes  
 Puede crear varias vistas diferentes de los requisitos de los usuarios.  Cada vista proporciona un tipo determinado de información.  Al crear estas vistas, es mejor pasar con frecuencia de una a otra. Puede empezar desde cualquier vista.  
  
|Diagrama o documento|Qué se describe en un modelo de requisitos|Sección|  
|-------------------------|-----------------------------------------------|-------------|  
|Diagrama de casos de uso|Quién usa el sistema y para qué lo usa.|[Que describe cómo se usa el sistema](#UseCases)|  
|Diagrama de clases conceptuales|Glosario de los tipos que se usan para describir los requisitos; los tipos visibles en la interfaz del sistema.|[Definir los términos usados para describir los requisitos](#RequirementsClasses)|  
|Diagrama de actividades|Flujo de trabajo e información que existe entre las actividades realizadas por los usuarios y el sistema o partes del sistema.|[Que muestra el flujo de trabajo entre los usuarios y el sistema](#Workflow)|  
|Diagrama de secuencia|Secuencia de interacciones que existen entre los usuarios y el sistema o partes del sistema. Vista alternativa al diagrama de actividades.|[Mostrar las interacciones entre usuarios y el sistema](#Sequences)|  
|Otros documentos o elementos de trabajo|Criterios de rendimiento, seguridad, facilidad de uso y confiabilidad.|[Describir los requisitos de calidad de servicio](#QoSRequirements)|  
|Otros documentos o elementos de trabajo|Restricciones y reglas no específicas para un determinado caso de uso|[Mostrar reglas de negocio](#BusinessRules)|  
  
 Observe que la mayoría de los tipos de diagramas se pueden usar para otros fines. Para obtener información general de los tipos de diagramas, vea [crear modelos para la aplicación](../modeling/create-models-for-your-app.md). Para obtener información básica sobre cómo dibujar diagramas, vea [modelos y diagramas UML editar](../modeling/edit-uml-models-and-diagrams.md).  
  
##  <a name="UseCases"></a> Que describe cómo se usa el sistema  
 Cree diagramas de casos de uso para describir quién usa el sistema y para qué lo usa. Un caso de uso representa un objetivo de un usuario del sistema y el procedimiento que realiza para lograr el objetivo.  
  
 Por ejemplo, un sistema de venta de comida en línea debe permitir a los clientes elegir platos de un menú, y a los restaurantes correspondientes actualizar dicho menú. Esto se puede resumir en un diagrama de casos de uso:  
  
 ![Casos de uso para cliente y restaurante](../modeling/media/uml-reqmuc1.png "UML_ReqmUC1")  
  
 También puede mostrar cómo un caso de uso se compone de casos más pequeños. Por ejemplo, pedir un menú forma parte de la compra de comida, que también incluye el pago y el envío:  
  
 ![El sistema participa en el pago pero no en la entrega. ](../modeling/media/uml-reqmuc2.png "UML_ReqmUC2")  
  
 También puede mostrar los casos de uso que se incluyen en el ámbito del sistema que está desarrollando. Por ejemplo, el sistema de la ilustración no interviene en el caso de uso de reparto de comida. Esto ayuda a establecer el contexto para el trabajo de desarrollo. (En un diagrama de casos de uso, se pueden usar los contenedores del subsistema para representar el sistema o sus componentes).  
  
 También ayuda al equipo a analizar lo que se incluirá en las versiones posteriores. Por ejemplo, puede discutir si, en la versión inicial del sistema, el pago de la comida se situará directamente entre el restaurante y el cliente, en lugar de pasar por el sistema. En ese caso, podría sacar el pago de la comida fuera del rectángulo del sistema de Dinner Now.  
  
 Un diagrama de casos de uso solo proporciona un resumen de los casos de uso. Para proporcionar descripciones más detalladas, puede vincular los casos de uso del diagrama a documentos independientes y a otros diagramas. Para obtener información sobre cómo hacerlo, consulte [vincular un caso de uso a documentos y diagramas](../modeling/link-a-use-case-to-documents-and-diagrams.md).  
  
 Dibujar un diagrama de casos de uso ayuda a su equipo a:  
  
- Centrarse en lo que los usuarios esperan hacer con el sistema, sin necesidad de detenerse en los detalles de la implementación.  
  
- Analizar el ámbito del sistema o de versiones específicas del sistema.  
  
  Para más información, vea los temas siguientes:  
  
|Más información|Leer|  
|--------------------|----------|  
|Información más detallada sobre cómo crear casos de uso|[Diagramas de casos de uso de UML: instrucciones](../modeling/uml-use-case-diagrams-guidelines.md)|  
|Elementos de un diagrama de casos de uso|[Diagramas de casos de uso de UML: referencia](../modeling/uml-use-case-diagrams-reference.md)|  
|Cómo desarrollar código a partir de casos de uso|[Modelar la arquitectura de la aplicación](../modeling/model-your-app-s-architecture.md)|  
  
##  <a name="RequirementsClasses"></a> Definir los términos usados para describir los requisitos  
 Puede usar diagramas de clases de UML para desarrollar un vocabulario coherente de los conceptos de negocio usados para los siguientes fines:  
  
- Analizar el negocio en el que funciona el sistema con los propios usuarios.  
  
- Describir las necesidades de los usuarios como, por ejemplo, en las descripciones de los casos de uso, las reglas de negocios y los casos de usuario.  
  
- Los tipos de información que se intercambian en la API del sistema o a través de la interfaz de usuario.  
  
- Descripciones de las pruebas del sistema o de aceptación.  
  
  Cuando se usan para este fin, el contenido de un diagrama de clases de UML se denomina "diagrama de clases conceptuales". (También conocido como *modelo de dominio* o *modelo de clase de análisis*).  
  
  En un diagrama de clases conceptuales, solo se muestran las clases necesarias en las descripciones de los requisitos; no se muestra ningún detalle del diseño interno del sistema. El diagrama no muestra ningún detalle del diseño interno del sistema. Normalmente no se muestran operaciones ni interfaces en las clases conceptuales.  
  
  Por ejemplo, puede dibujar las siguientes clases conceptuales para el sistema de Dinner Now:  
  
  ![Clases de menú, pedido, elemento de menú, elemento de pedido. ](../modeling/media/uml-reqmcd1.png "UML_ReqMCD1")  
  
  Un diagrama de clases conceptuales proporciona el vocabulario que se usa en el modelo de requisitos. Por ejemplo, en la descripción detallada del caso de uso para pedir un menú, puede escribir:  
  
  El cliente elige un *menú* para iniciar un *pedido*y, después, crea *elementos del pedido* en el *pedido* mediante la selección de *elementos de menú* en el *menú*.  
  
  Observe cómo los términos usados en esta descripción son los nombres de las clases del modelo. El diagrama elimina las ambigüedades de las relaciones entre esas clases. Por ejemplo, muestra claramente que cada pedido está asociado a un solo menú.  
  
  Los malentendidos sobre los requisitos de los usuarios suelen deberse a malentendidos relacionados con el significado exacto de las palabras. Por ejemplo, la mayoría de los restaurantes compartirán la visión de los términos "menú" y "pedido", pero la diferencia entre un elemento de un pedido y un elemento de un menú es menos clara. Cuando se tratan los requisitos con las partes interesadas del negocio, es importante exponer estas diferencias. El diagrama de clases es una herramienta útil para ayudar a aclarar los términos y sus relaciones.  
  
  El modelo de clases conceptuales puede formar el vocabulario básico con el que describir la lógica de negocios de su sistema. Pero las clases del software suelen ser mucho más complejas que el modelo conceptual, ya que la implementación debe tener en cuenta aspectos como el rendimiento, la distribución, la flexibilidad y otros factores. Con frecuencia, en un sistema se encuentran varias implementaciones diferentes de una clase conceptual.  
  
  Por ejemplo, los pedidos pueden representarse en XML, SQL, HTML y C# en diferentes partes del sistema y en distintas interfaces entre las partes. La asociación entre un pedido y un menú se puede representar de muchas formas diferentes, por ejemplo, como referencias en código de C#, relaciones en una base de datos o identificadores con referencias cruzadas en XML. Pero, a pesar de estas variaciones, el modelo conceptual proporciona información importante que es verdadera en todas las partes del software. El diagrama de clases del ejemplo nos indica que, en cada implementación, habrá un único menú asociado a cada pedido.  
  
  Dibujar un diagrama de clases de requisitos ayuda a su equipo a:  
  
- Definir y estandarizar los términos básicos que se usan en el análisis de las necesidades de los usuarios.  
  
- Aclarar las relaciones entre dichos términos.  
  
  Para más información, vea los temas siguientes:  
  
|Más información|Leer|  
|--------------------|----------|  
|Información más detallada sobre cómo buscar clases de requisitos|[Diagramas de clases de UML: instrucciones](../modeling/uml-class-diagrams-guidelines.md)|  
|Elementos de un diagrama de clases conceptuales|[Diagramas de clases de UML: referencia](../modeling/uml-class-diagrams-reference.md)|  
|Cómo desarrollar código a partir de clases conceptuales|[Modelar la arquitectura de la aplicación](../modeling/model-your-app-s-architecture.md)|  
  
 En un diagrama de clases conceptuales, normalmente no resulta útil colocar las flechas en las asociaciones para representar la navegabilidad. Esto es porque el diagrama no representa una implementación. Las asociaciones representan las relaciones entre objetos del mundo real. La siguiente extensión de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] convierte las flechas no direccionales en los valores predeterminados: [ejemplo de características de modelado de dominio UML](http://go.microsoft.com/fwlink/?LinkId=213849).  
  
##  <a name="BusinessRules"></a> Showing Business Rules  
 Una regla de negocio es un requisito que no está asociado a ningún caso de uso determinado y que se debe observar en todo el sistema.  
  
 Muchas reglas de negocio son restricciones en las relaciones entre las clases conceptuales. Puede escribir estas *reglas de negocio estáticas* como comentarios asociados con las clases pertinentes en un diagrama de clases conceptuales. Por ejemplo:  
  
 ![Regla en comentario adjunto a la clase Order. ](../modeling/media/uml-reqmcd2.png "UML_ReqmCD2")  
  
 Las*reglas de negocio dinámicas* restringen las secuencias de eventos permitidas. Por ejemplo, puede usar un diagrama de secuencia o actividades para mostrar que un usuario debe iniciar sesión antes de realizar otras operaciones en el sistema.  
  
 Pero muchas reglas dinámicas se pueden aplicar de una forma más eficaz y genérica al reemplazarlas por reglas estáticas. Por ejemplo, puede agregar un atributo booleano "Logged In" a una clase en el modelo de clases conceptuales. Agregaría "Logged In" como condición posterior del caso de uso de inicio de sesión y lo agregaría como condición previa de la mayoría de los demás casos de uso. Este enfoque le permite evitar definir todas las combinaciones de secuencias de eventos posibles. También es más flexible cuando necesita agregar nuevos casos de uso al modelo.  
  
 Observe que la opción es sobre la definición de los requisitos, y que esto es independiente de la implementación de los requisitos en el código del programa.  
  
 Para obtener más información, consulte los temas siguientes:  
  
|Más información|Leer|  
|--------------------|----------|  
|Información más detallada sobre cómo buscar y registrar reglas de negocio estáticas|[Diagramas de clases de UML: instrucciones](../modeling/uml-class-diagrams-guidelines.md)|  
|Elementos de un diagrama de clases conceptuales|[Diagramas de clases de UML: referencia](../modeling/uml-class-diagrams-reference.md)|  
|Cómo desarrollar código que cumple las reglas de negocio|[Modelar la arquitectura de la aplicación](../modeling/model-your-app-s-architecture.md)|  
  
##  <a name="QoSRequirements"></a> Describing Quality of Service Requirements  
 Existen varias categorías de requisito de calidad de servicio. Entre esos tipos se incluyen los siguientes:  
  
- Rendimiento  
  
- Seguridad  
  
- Facilidad de uso  
  
- Confiabilidad  
  
- Solidez  
  
  Puede incluir algunos de estos requisitos en las descripciones de casos de uso concretos. Otros requisitos no son específicos de los casos de uso y resulta más eficaz incluirlos en un documento independiente. Cuando sea posible, resulta útil ajustarse al vocabulario definido en el modelo de requisitos. En el ejemplo siguiente, observe que las principales palabras que se usan en el requisito son los títulos de los actores, los casos de uso y las clases de las ilustraciones anteriores:  
  
  Si un restaurante elimina un elemento del menú mientras un cliente pide un menú, cualquier elemento del pedido que haga referencia a ese elemento del menú se mostrará de color rojo.  
  
  Para obtener más información, consulte los temas siguientes:  
  
|Más información|Leer|  
|--------------------|----------|  
|Información más detallada sobre el registro de los requisitos de calidad de servicio|[Instrucciones para definir los requisitos de calidad de servicio](http://msdn.microsoft.com/en-us/9677a437-c2cb-4ac4-8c2d-4e3350005f06)|  
|Asociar documentos adicionales a los casos de uso|[Vincular un caso de uso a documentos y diagramas](../modeling/link-a-use-case-to-documents-and-diagrams.md)|  
|Cómo desarrollar código que cumpla los requisitos de calidad de servicio|[Modelar la arquitectura de la aplicación](../modeling/model-your-app-s-architecture.md)|  
  
##  <a name="Workflow"></a> Que muestra el flujo de trabajo entre los usuarios y el sistema  
 Puede usar un diagrama de actividades para mostrar el flujo de trabajo existente entre los distintos casos de uso. A menudo, resulta útil empezar un modelo de requisitos con el dibujo de un diagrama de actividades que muestre las principales tareas que realizan los usuarios, tanto en el sistema como fuera de él.  
  
 Por ejemplo:  
  
 ![Actividad con tres acciones y un bucle. ](../modeling/media/uc-reqmwfact.png "UC_ReqmWFAct")  
  
 Puede dibujar diagramas de casos de uso y diagramas de actividades para mostrar distintas vistas de la misma información.  El diagrama de casos de uso es más eficaz a la hora de mostrar el anidamiento de las acciones más pequeñas dentro de una actividad mayor, pero no muestra el flujo de trabajo. Por ejemplo:  
  
 ![Casos de uso de las acciones anteriores](../modeling/media/uml-reqmwfuc.png "UML_ReqmWFUC")  
  
 Observe que también puede usar diagramas de actividades para describir los algoritmos en el software, pero cuando use los diagramas para el proceso de negocio, debe centrarse en las acciones que son visibles fuera del sistema.  
  
 Para más información, vea los temas siguientes:  
  
|Más información|Leer|  
|--------------------|----------|  
|Más información sobre cómo definir los flujos de trabajo empresariales|[Diagramas de actividades UML: instrucciones](../modeling/uml-activity-diagrams-guidelines.md)|  
|Elementos de un diagrama de actividades|[Diagramas de actividades UML: referencia](../modeling/uml-activity-diagrams-reference.md)|  
|Cómo desarrollar código a partir de diagramas de actividades|[Modelar la arquitectura de la aplicación](../modeling/model-your-app-s-architecture.md)|  
  
##  <a name="Sequences"></a> Mostrar las interacciones entre usuarios y el sistema  
 Puede usar un diagrama de secuencia para mostrar el intercambio de mensajes entre el sistema y los actores externos, o bien entre las partes del sistema. Esto proporciona una vista de los pasos de un caso de uso que muestra claramente la secuencia de interacciones. Los diagramas de secuencia resultan especialmente útiles cuando hay varias partes que interactúan en un caso de uso y también cuando el sistema tiene una API.  
  
 Por ejemplo:  
  
 ![Diagrama de secuencia con sistema y actores. ](../modeling/media/uml-reqmseq.png "UML_ReqmSeq")  
  
 Una ventaja de los diagramas de secuencia es que resulta fácil ver qué mensajes entran en el sistema que se está desarrollando. Para diseñar el sistema, puede reemplazar la única línea de vida del sistema por una línea de vida diferente para cada uno de sus componentes y, después, mostrar las interacciones entre ellos en respuesta a cada mensaje entrante.  
  
 Para más información, vea los temas siguientes:  
  
|Más información|Leer|  
|--------------------|----------|  
|Más información sobre cómo definir las interacciones|[Diagramas de secuencia de UML: instrucciones](../modeling/uml-sequence-diagrams-guidelines.md)|  
|Elementos de un diagrama de secuencia|[Diagramas de secuencia UML: referencia](../modeling/uml-sequence-diagrams-reference.md)|  
|Cómo desarrollar código a partir de diagramas de secuencia|[Modelar la arquitectura de la aplicación](../modeling/model-your-app-s-architecture.md)|  
  
## <a name="using-a-model-to-reduce-inconsistencies"></a>Usar un modelo para reducir las incoherencias  
 La creación de un modelo suele reducir significativamente las incoherencias y las ambigüedades de los requisitos de los usuarios. Las diferentes partes interesadas suelen tener concepciones distintas del mundo empresarial en el que funciona el sistema. Por lo tanto, la primera tarea consiste en resolver estas diferencias entre los clientes.  
  
 Comprobará que muchas preguntas sobre el ámbito empresarial surgen de forma natural durante la creación de un modelo. Al formular estas preguntas a los usuarios, reducirá la necesidad de realizar cambios en una fase posterior del proyecto. Estas son algunas preguntas específicas que puede hacerse al principio y, después, preguntar a las partes interesadas del negocio si no tiene clara la respuesta:  
  
- Para cada clase del modelo de requisitos, pregunte: ¿Qué caso de uso crea instancias de esta clase? Por ejemplo, en un servicio de pedidos de comida en línea, puede preguntar: ¿Qué caso de uso crea instancias de la clase de menú del restaurante? Esto daría lugar a un análisis sobre cómo un restaurante nuevo se adhiere al servicio y contribuye con su menú. Puede plantearse preguntas similares sobre qué elementos crean o modifican atributos y asociaciones.  
  
- Para cada caso de uso del modelo de requisitos, intente describir el resultado o la condición posterior de cada caso de uso con las palabras proporcionadas por los diagramas de clases. A menudo, resulta útil mostrar el efecto de un caso de uso con la realización de bocetos de instancias de las clases antes y después de una ocurrencia del caso de uso. Por ejemplo, si la condición posterior del caso de uso dice "se agrega un elemento del menú al pedido del cliente", cree bocetos de las instancias de las clases de pedido y elemento del menú. Muestre los efectos del caso de uso como, por ejemplo, un nuevo vínculo o un nuevo objeto, con un color diferente o en un dibujo nuevo. Esto suele dar lugar a análisis sobre qué información es necesaria en el modelo. Aunque las clases de requisitos no están relacionadas directamente con la implementación, describen la información que el sistema necesitará almacenar y transmitir.  
  
- Formule preguntas sobre las restricciones en los atributos y las asociaciones, especialmente sobre las restricciones que implican más de un atributo o una asociación.  
  
- Pregunte sobre secuencias válidas y no válidas de casos de uso. Para ello, dibuje diagramas de secuencia o de actividades para representarlas.  
  
  Al examinar las relaciones entre las vistas que proporcionan los diferentes diagramas, podrá reconocer fácilmente los principales conceptos con los que trabajan los usuarios y ayudarles a entender lo que necesitan del sistema. También podrá conocer mejor los requisitos que las partes interesadas tienen menos claros. Puede planear el desarrollo de esas características, al menos de forma simplificada, en una fase temprana del proyecto para que los usuarios puedan experimentar con ellas.  
  
## <a name="see-also"></a>Vea también  
 [Editar modelos y diagramas UML](../modeling/edit-uml-models-and-diagrams.md)   
 [Desarrollar pruebas en un modelo](../modeling/develop-tests-from-a-model.md)   
 [Usar modelos en el proceso de desarrollo](../modeling/use-models-in-your-development-process.md)   
 [Modelar la arquitectura de la aplicación](../modeling/model-your-app-s-architecture.md)   
 [Extensión de VS de ejemplo: Características de modelado de dominio UML](http://go.microsoft.com/fwlink/?LinkId=213849)   
 [Extensión de VS de ejemplo: Elementos UML de Color por estereotipo](http://go.microsoft.com/fwlink/?LinkID=213841)   
 [Extensión de VS de ejemplo: Vinculan elementos UML a diagramas, archivos y otros elementos](http://go.microsoft.com/fwlink/?LinkID=213813)   
 [Extensión de VS de ejemplo: Alinear formas en un diagrama de UML](http://go.microsoft.com/fwlink/?LinkID=213809)   
 [Vídeo: Modelar el dominio de negocio](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-3-Modeling-the-Business-Domain/)



