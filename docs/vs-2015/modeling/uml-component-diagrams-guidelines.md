---
title: 'Diagramas de componentes UML: Instrucciones | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML diagrams, component
- diagrams - modeling, component
- diagrams - modeling, UML component
- UML, component diagrams
- component diagrams
ms.assetid: 6c1bdd60-369e-477e-83ed-7f6fe75c9f0b
caps.latest.revision: 37
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 2a01e81b54f5ee4a581cff4705d3751dd370bc0e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47566627"
---
# <a name="uml-component-diagrams-guidelines"></a>Diagramas de componentes de UML: Instrucciones
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [diagramas de componentes UML: instrucciones](https://docs.microsoft.com/visualstudio/modeling/uml-component-diagrams-guidelines).  
  
En Visual Studio, puede dibujar un *diagrama de componentes* para mostrar la estructura de un sistema de software. Para una demostración en vídeo, consulte [diseñar la estructura física mediante diagramas de componentes](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-6-Designing-a-Projects-Physical-Structure/).  
  
 Para ver qué versiones de Visual Studio admiten esta característica, vea [Compatibilidad de versiones con las herramientas de arquitectura y modelado](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Para crear un diagrama de componentes UML, en el **arquitectura** menú, haga clic en **nuevo UML o diagrama de capas**.  
  
 Un componente es una unidad modular que puede reemplazarse en su propio entorno. Sus elementos internos quedan ocultos, pero tiene uno o más bien definidos *interfaces proporcionadas* a través de que se pueden obtener acceso a sus funciones. También puede tener un componente *interfaces necesarias*. En una interfaz necesaria, se definen las funciones o servicios de otros componentes que son necesarios. Mediante la conexión de las interfaces proporcionadas y las interfaces necesarias de distintos componentes, puede construirse un componente mayor. Un sistema de software completo se puede concebir como un componente.  
  
 El uso de diagramas de componentes tiene algunas ventajas:  
  
-   Concebir el diseño atendiendo a los bloques principales ayuda al equipo de desarrollo a entender un diseño existente y a crear uno nuevo.  
  
-   Al pensar en el sistema como una colección de componentes con interfaces proporcionadas y necesarias bien definidas, se mejora la separación entre los componentes. Esto, a su vez, facilita la comprensión y los cambios cuando se modifican los requisitos.  
  
 Puede utilizar un diagrama de componentes para representar el diseño con independencia del lenguaje o plataforma que el diseño utiliza o va a utilizar.  
  
##  <a name="OtherDiagrams"></a> Relación con otros diagramas  
 Puede utilizar un diagrama de componentes junto con otros diagramas.  
  
|Otro diagrama|Ayuda a debatir y transmitir los siguientes aspectos del diseño|  
|-------------------|--------------------------------------------------------------------|  
|Diagrama de secuencia UML|-Las interacciones entre los componentes del sistema<br />-Las interacciones entre los elementos dentro de un componente.<br /><br /> Para obtener más información, consulte [diagramas de secuencia UML: instrucciones](../modeling/uml-sequence-diagrams-guidelines.md).|  
|Diagrama de clases de UML|-Las interfaces de un componente. El diagrama de clases permite detallar los métodos de la interfaz.<br />-Los datos enviados en los parámetros a través de interfaces de los componentes.<br /><br /> Para obtener más información, consulte [diagramas de clases UML: instrucciones](../modeling/uml-class-diagrams-guidelines.md).|  
|Diagramas de actividades|-El procesamiento interno efectuado por un componente en respuesta a los mensajes entrantes.<br /><br /> Para obtener más información, consulte [diagramas de actividades UML: instrucciones](../modeling/uml-activity-diagrams-guidelines.md).|  
|Diagramas de capas|-Los niveles arquitectónicos lógicos para los componentes.<br /><br /> Para obtener más información, consulte [diagramas de capas: referencia](../modeling/layer-diagrams-reference.md).|  
  
##  <a name="Basics"></a> Pasos básicos para dibujar diagramas de componentes  
 Para obtener información de referencia sobre los elementos de diagramas de componentes, consulte [diagramas de componentes UML: referencia](../modeling/uml-component-diagrams-reference.md).  
  
 Para obtener más información sobre cómo usar diagramas de componentes en el proceso de diseño, vea [modelar la arquitectura de la aplicación](../modeling/model-your-app-s-architecture.md).  
  
> [!NOTE]
>  Se describen los pasos detallados para crear cualquiera de los diagramas de modelado en [modelos y diagramas UML editar](../modeling/edit-uml-models-and-diagrams.md).  
  
#### <a name="to-create-a-component-diagram"></a>Para crear un diagrama de componentes  
  
1.  En el **arquitectura** menú, haga clic en **nuevo UML o diagrama de capas**.  
  
2.  En **plantillas**, haga clic en **diagrama de componentes UML**.  
  
3.  Especifique un nombre para el diagrama.  
  
4.  En **agregar a proyecto de modelado**, seleccione un proyecto de modelado existente de la solución, o **crear un nuevo proyecto de modelado**y, a continuación, haga clic en **Aceptar**...  
  
     Aparece un nuevo diagrama de componentes con UML **diagrama de componentes** cuadro de herramientas. El cuadro de herramientas contiene las relaciones y elementos necesarios.  
  
### <a name="drawing-components"></a>Dibujar componentes  
 ![Componentes con interfaces](../modeling/media/uml-compdrawing.png "UML_CompDrawing")  
  
 Crear un *componente* (1) para cada unidad funcional principal del sistema o aplicación.  
  
 Algunos ejemplos pueden ser una aplicación, un dispositivo de hardware, un servicio Web, un ensamblado .NET, una clase o un grupo de clases de programa o cualquier segmento de un programa que se pueda separar.  
  
##### <a name="to-create-components"></a>Para crear componentes  
  
1.  Haga clic en **componente** en el cuadro de herramientas y, a continuación, haga clic en una parte en blanco del diagrama.  
  
     \- o -  
  
     Copie y pegue un componente existente.  
  
    1.  Busque un componente existente en un diagrama o en **Explorador de modelos UML**.  
  
    2.  Haga clic en el componente y, a continuación, haga clic en **copia**.  
  
    3.  Abra el diagrama en el que desea que aparezca el componente copiado.  
  
    4.  Haga clic en una parte en blanco del diagrama y, a continuación, haga clic en **pegar**.  
  
         Aparece una copia del componente con un nombre nuevo.  
  
2.  Haga clic en el nombre del componente para cambiarlo.  
  
3.  Haga clic en el botón de contenido adicional 5) si desea ver exclusivamente el encabezado del componente.  
  
### <a name="showing-the-ports-of-a-component"></a>Mostrar los puertos de un componente  
 Un *puerto* (2, 3) representa un grupo de mensajes o llamadas de operación que tienen como origen o destino un componente. El grupo se describe mediante una interfaz, que define el tipo de puerto. Un puerto puede proporcionar o necesitar una interfaz.  
  
 Un puerto con un *proporciona la interfaz* (2) suministra operaciones que se implementan en el componente y que puede usarse por otros componentes.  
  
 Algunos ejemplos serían una interfaz de usuario, un servicio Web, una interfaz de .NET o una colección de funciones de cualquier lenguaje de programación.  
  
 Un puerto con un *interfaz necesaria* (3) representa el requisito de un componente de un grupo de operaciones o servicios que se proporcione por otros componentes o sistemas externos.  
  
 Por ejemplo, un explorador web necesita servidores web o un complemento de la aplicación necesita los servicios de la aplicación.  
  
 Un componente puede tener cualquier número de puertos.  
  
##### <a name="to-add-ports-to-a-component"></a>Para agregar puertos a un componente  
  
1.  En el cuadro de herramientas, haga clic en **Provided Interface** o **Required Interface**.  
  
2.  Haga clic en el componente al que desea agregar los puertos.  
  
     Aparecerá un puerto en el límite del componente.  
  
     Se crea una nueva interfaz como el tipo del puerto. Esta interfaz aparece en **Explorador de modelos UML**.  
  
3.  Arrastre el puerto situado en torno al límite del componente hasta situarlo donde desee.  
  
4.  Arrastre la etiqueta del puerto hasta ajustar su posición.  
  
5.  Haga clic en la etiqueta para cambiarla. En la etiqueta se muestra el nombre de la interfaz. Si la modifica, cambiará el nombre de la interfaz.  
  
 Si desea enumerar los atributos y las operaciones de la interfaz, puede hacerlo agregándolos a la interfaz en el Explorador de modelos UML. O bien, puede arrastrar la interfaz del Explorador de modelos UML a un diagrama de clases, y agregar las operaciones y atributos allí.  
  
### <a name="linking-between-components"></a>Establecer vínculos entre componentes  
 Utilice una dependencia 4) para mostrar que el requisito de un componente puede satisfacerse a través de las operaciones o servicios proporcionados por otro componente.  
  
##### <a name="to-show-that-a-provided-interface-can-satisfy-a-required-interface"></a>Para mostrar que una interfaz proporcionada puede satisfacer una interfaz necesaria  
  
1.  En el cuadro de herramientas, haga clic en **dependencia**.  
  
2.  Haga clic en el puerto con la interfaz necesaria de un componente y, a continuación, haga clic en el puerto con la interfaz proporcionada de otro componente.  
  
 En la fase de diseño, intente evitar los bucles de dependencia en los que todos los componentes de un grupo dependen de todos los demás componentes.  
  
##### <a name="to-add-a-port-for-an-existing-interface-to-a-component"></a>Para agregar un puerto de una interfaz existente a un componente  
  
-   Busque la interfaz en **Explorador de modelos UML** y, a continuación, arrástrelo hasta el componente.  
  
     O bien  
  
-   Copie y pegue una referencia a una interfaz desde un diagrama.  
  
    1.  En un diagrama de clases o un diagrama de componentes, haga clic en la interfaz y, a continuación, haga clic en **copia**.  
  
    2.  En el diagrama de componentes, haga clic en el componente y, a continuación, haga clic en **Pegar referencia**.  
  
         En el componente aparece una interfaz proporcionada. Cerca aparece una etiqueta de acción.  
  
        > [!NOTE]
        >  Si usas **pegar** en lugar de **Pegar referencia**, se creará una nueva interfaz que tiene un nombre nuevo.  
  
    3.  Si desea crear una interfaz necesaria, haga clic en la etiqueta de acción y, a continuación, haga clic en **convertir en Required Interface**.  
  
##  <a name="Parts"></a> Mostrar los elementos internos de un componente  
 ![Diagrama de componentes mostrando elementos internos](../modeling/media/uml-compshowing.png "UML_CompShowing")  
  
 Puede incluir elementos (3) en un componente (1) para mostrar que está formado de componentes más pequeños que interactúan entre sí.  
  
 En el diagrama de la ilustración se muestra que todas las instancias del servicio Web Cenar ahora contienen una instancia del Servidor de cliente y una instancia del Servidor de cocina.  
  
 Un elemento es una propiedad de su componente primario, al igual que un atributo pertenece a una clase ordinaria. Los elementos tienen su propio tipo, que suele ser también un componente. La etiqueta del elemento tiene el mismo formato que un atributo ordinario:  
  
 `+ partName : TypeName`  
  
 Dentro del componente primario, en cada elemento se muestran las interfaces proporcionadas y necesarias que se definieron para su tipo (4, 5). Las operaciones o servicios que necesita un elemento puede proporcionárselos otro. Puede usar **Part Assembly** conectores para mostrar cómo partes se conectan entre sí (6).  
  
 También puede mostrar que una interfaz del componente primario es una interfaz que uno de sus elementos proporciona o necesita. Puede conectar un puerto del elemento primario a un puerto de un elemento interno mediante una **delegación** relación (9). Los dos puertos tienen que ser del mismo tipo (proporcionados o necesarios) y sus tipos de interfaz tienen que ser compatibles.  
  
 Puede crear un nuevo elemento con un nuevo tipo o a partir de un tipo existente.  
  
#### <a name="to-add-parts-to-a-component"></a>Para agregar elementos a un componente  
  
1.  Cree un elemento para cada unidad funcional principal que cree que forma parte del componente primario.  
  
    1.  Haga clic en **componente** en el cuadro de herramientas y, a continuación, haga clic dentro del componente primario (1).  
  
         Aparece un nuevo elemento (3) dentro del componente primario.  
  
         Se crea un nuevo componente de **Explorador de modelos UML**. Este es el nuevo tipo del elemento.  
  
         \- o -  
  
         Arrastre un componente existente del Explorador de modelos UML al componente primario.  
  
         Aparece un nuevo elemento (3) dentro del componente primario. Su tipo es el componente que arrastró desde el Explorador de modelos UML.  
  
         \- o -  
  
         Haga clic en un componente, en un diagrama o en el Explorador de modelos UML y, a continuación, haga clic en **copia**.  
  
         Haga doble clic en el componente primario y, a continuación, haga clic en **Pegar referencia**.  
  
         Aparece un nuevo elemento (3) dentro del componente primario. Su tipo es el componente que copió.  
  
    2.  Haga clic en el nombre del nuevo componente para cambiarlo. Su tipo no se puede modificar.  
  
    3.  Puede agregar interfaces proporcionadas y necesarias (4, 5) al nuevo elemento. Haga clic en el **Provided Interface** o **Required Interface** herramienta y, a continuación, haga clic en la parte.  
  
         \- o -  
  
         Arrastre una interfaz existente del **Explorador de modelos UML** al elemento.  
  
         Las interfaces se agregan al tipo del elemento y aparecen en el propio elemento. El componente primario ajusta su tamaño, si es necesario.  
  
2.  Conecte los elementos entre sí.  
  
    -   Use la **dependencia** herramienta para conectar los puertos de distintos elementos (6).  
  
3.  Conecte los puertos a los puertos del componente primario:  
  
    1.  Cree uno o varios puertos (7) en el componente primario. Haga clic en **Required Interface** o **Provided Interface** en el cuadro de herramientas y, a continuación, haga clic en el componente primario.  
  
    2.  Cree delegados (9) del puerto en uno o varios elementos. Haga clic en el **delegación** herramienta, a continuación, un puerto en el componente primario y, a continuación, un puerto de un elemento. A través de este mismo mecanismo, puede conectar puertos que proporcionan o necesitan interfaces.  
  
### <a name="showing-the-parts-of-a-part"></a>Mostrar los elementos que conforman un elemento  
 Después de descomponer un componente en elementos, puede descomponer cada uno de los tipos de elementos en sus propios elementos internos.  
  
 Resulta más fácil representar cada nivel de la descomposición en un diagrama de componentes diferente. Primero debe buscar el tipo del elemento. Por ejemplo, en la ilustración, uno de los elementos se denomina `DNCustomerServer` y su tipo es un componente que se denomina `CustomerServer`. Puede buscar este tipo en el Explorador de modelos UML y situarlo en otro diagrama. A continuación, puede crear sus propios elementos internos.  
  
##### <a name="to-place-a-parts-type-on-a-diagram"></a>Para situar un tipo de elemento en un diagrama  
  
1.  Especifique el nombre completo del tipo de elemento.  
  
     Haga clic en el elemento y, a continuación, haga clic en **propiedades**.  
  
     El nombre del tipo aparece en el **tipo** campo de la ventana Propiedades.  
  
2.  Busque el tipo del elemento en **Explorador de modelos UML**.  
  
     Haga clic en **vista**, apunte a **Other Windows**y, a continuación, haga clic en **Explorador de modelos UML**.  
  
     Expanda el proyecto y, si es necesario, los paquetes a los que pertenece el tipo.  
  
     El tipo aparecerá como un **componente**.  
  
     Si lo desea, puede cambiar su nombre aquí.  
  
3.  Abra o cree otro diagrama de componentes.  
  
4.  Arrastre el tipo del Explorador de modelo UML al diagrama.  
  
     En el diagrama aparece una vista del tipo como componente.  
  
     Tiene las mismas interfaces que las que definió para el elemento.  
  
     Ahora puede agregar otros elementos.  
  
##  <a name="Designing"></a> Diseñar el componente  
  
### <a name="describing-how-the-parts-collaborate"></a>Describir cómo colaboran los elementos  
 Puede dibujar un diagrama de secuencia para mostrar el modo en que los elementos trabajan juntos en respuesta a un mensaje que llega al componente primario.  
  
 Puede utilizar estos diagramas para explicar un componente existente o diseñar uno nuevo.  
  
 Si todavía está diseñando el componente, puede dibujar diagramas de secuencia antes de decidir qué elementos contendrá. Puede utilizar los diagramas de secuencia para experimentar con distintos elementos, interfaces necesarias y secuencias de mensajes. Dibuje diagramas de secuencia para los mensajes entrantes más frecuentes y más importantes. Puede crear elementos en el componente que se correspondan con las líneas de vida que haya decidido.  
  
 Utilice los diagramas de secuencia para valorar el modo en que los diferentes componentes comparten el trabajo del sistema.  
  
-   Si la carga de trabajo es muy grande en un elemento, probablemente resultará más complicado actualizar la aplicación que si el trabajo se distribuye uniformemente.  
  
-   Si la carga de trabajo es demasiado escasa y se distribuye en muchas interacciones, el sistema podría tener un mal rendimiento y podría resultar difícil de entender.  
  
 ![Diagrama que muestra elementos colaboración de secuencia](../modeling/media/uml-compdescparts.png "UML_CompDescParts")  
  
##### <a name="to-draw-a-sequence-diagram-that-shows-collaboration-between-parts"></a>Para dibujar un diagrama de secuencia en el que se muestre la colaboración entre los elementos  
  
1.  Cree un nuevo diagrama de secuencia.  
  
     Para obtener más información, consulte [diagramas de secuencia UML: instrucciones](../modeling/uml-sequence-diagrams-guidelines.md).  
  
2.  Cree una línea de vida en un componente externo, usuario, dispositivo u otro actor (1) que envíe mensajes a este componente.  
  
     Puede establecer el **Actor** propiedad de esta línea de vida en true para indicar que es externa al componente en cuestión. Sobre la línea de vida aparece un dibujo esquemático.  
  
3.  Cree una línea de vida en la interfaz proporcionada (2) de este componente al que el actor seleccionado envía mensajes.  
  
4.  Cree una línea de vida en cada elemento (3) del componente.  
  
5.  Cree una línea de vida en cada interfaz necesaria (4) del componente.  
  
6.  Dibuje mensajes procedentes del actor externo (5). Muestre cómo se pasa el mensaje a los elementos y cómo estos elementos colaboran para responder al mensaje.  
  
7.  Siempre que sea necesario, muestre los mensajes enviados a una interfaz necesaria (6). No muestre los detalles de la ejecución del mensaje.  
  
### <a name="is-the-component-more-than-its-parts"></a>¿Es el componente mayor que la suma de sus partes?  
 En algunos casos, un componente no es más que un nombre que se asigna a una colección de elementos. Los elementos realizan todo el trabajo y no hay ningún código ni ningún otro artefacto en tiempo de ejecución que represente al componente.  
  
 Puede indicar en el modelo estableciendo el **Is Indirectly Instantiated** propiedad del componente. En este caso, todas las interfaces del componente deben estar en los puertos, con delegaciones en los elementos internos.  
  
### <a name="describing-the-process-inside-each-part"></a>Describir el proceso que tiene lugar en cada elemento  
 Puede utilizar diagramas de actividades para mostrar cómo un componente procesa cada mensaje entrante. Para obtener más información, consulte [diagramas de actividades UML: instrucciones](../modeling/uml-activity-diagrams-guidelines.md).  
  
 ![Diagrama de actividades con búfer de datos](../modeling/media/uml-compdescribingproc.png "UML_CompDescribingProc")  
  
 Utilice una acción de evento de aceptación (1) para mostrar que un mensaje entrante inicia un nuevo subproceso.  
  
 Utilice nodos de objeto y pins de entrada y salida para mostrar el flujo de información y dónde se almacena la información. En el ejemplo, se utiliza un nodo de objeto (2) para mostrar los elementos que se están almacenando en búfer entre un subproceso y otro.  
  
### <a name="defining-data-and-classes"></a>Definir datos y clases  
 Puede utilizar un diagrama de clases de UML para describir en detalle el contenido de:  
  
-   Las interfaces de los componentes. Cuando se agrega un puerto que requiere o proporciona interfaces a un componente, aparece una interfaz en el Explorador de modelos UML. Puede arrastrarla o copiarla en un diagrama de clases UML para mostrar sus atributos y operaciones, y las relaciones con otras interfaces.  
  
-   Los datos que se pasan en los parámetros de las operaciones de las interfaces.  
  
-   Los datos almacenados en los componentes, por ejemplo, tal y como se muestran en los flujos de objetos de los diagramas de actividades.  
  
### <a name="general-dependencies-between-components"></a>Dependencias generales entre componentes  
 Puede utilizar un diagrama de componentes para mostrar exclusivamente los elementos principales del diseño y sus interdependencias.  
  
 ![Una dependencia entre componentes](../modeling/media/uml-compdepend.png "UML_CompDepend")  
  
 Use la **dependencia** herramienta para dibujar una dependencia. Así indicará que el diseño de un componente se basa en otro.  
  
 Entre los tipos habituales de dependencia se incluyen los siguientes:  
  
-   Un componente llama al código en otro.  
  
-   Un componente crea una instancia de una clase que se define en otra clase.  
  
-   Un componente usa información creada por otro componente.  
  
 Puede utilizar el nombre de la flecha de dependencia para dar cuenta de un tipo de uso concreto. Para establecer el nombre, haga clic en la flecha y, a continuación, haga clic en **propiedades**y establezca el **nombre** campo en la ventana Propiedades.  
  
## <a name="see-also"></a>Vea también  
 [Editar modelos y diagramas UML](../modeling/edit-uml-models-and-diagrams.md)   
 [Diagramas de componentes UML: referencia](../modeling/uml-component-diagrams-reference.md)   
 [Diagramas de secuencia UML: referencia](../modeling/uml-sequence-diagrams-reference.md)   
 [Diagramas de casos de uso UML: referencia](../modeling/uml-use-case-diagrams-reference.md)   
 [Diagramas de clases UML: referencia](../modeling/uml-class-diagrams-reference.md)   
 [Diagramas de componentes UML: referencia](../modeling/uml-component-diagrams-reference.md)   
 [Vídeo: Diseñar la estructura física mediante diagramas de componentes](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-6-Designing-a-Projects-Physical-Structure/)



