---
title: 'UML Component Diagrams: Guidelines | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML diagrams, component
- diagrams - modeling, component
- diagrams - modeling, UML component
- UML, component diagrams
- component diagrams
ms.assetid: 6c1bdd60-369e-477e-83ed-7f6fe75c9f0b
caps.latest.revision: 37
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 99f2b67d264edcaab5272d0224d4450ee2e8a6f6
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297164"
---
# <a name="uml-component-diagrams-guidelines"></a>Diagramas de componentes de UML: Instrucciones
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio, you can draw a *component diagram* to show the structure a software system. For a video demonstration, see [Designing the Physical Structure by using Component Diagrams](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-6-designing-a-projects-physical-structure).

 Para ver qué versiones de Visual Studio admiten esta característica, vea [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 To create a UML component diagram, on the **Architecture** menu, click **New UML or Layer Diagram**.

 Un componente es una unidad modular que puede reemplazarse en su propio entorno. Its internals are hidden, but it has one or more well-defined *provided interfaces* through which its functions can be accessed. A component can also have *required interfaces*. En una interfaz necesaria, se definen las funciones o servicios de otros componentes que son necesarios. Mediante la conexión de las interfaces proporcionadas y las interfaces necesarias de distintos componentes, puede construirse un componente mayor. Un sistema de software completo se puede concebir como un componente.

 El uso de diagramas de componentes tiene algunas ventajas:

- Concebir el diseño atendiendo a los bloques principales ayuda al equipo de desarrollo a entender un diseño existente y a crear uno nuevo.

- Al pensar en el sistema como una colección de componentes con interfaces proporcionadas y necesarias bien definidas, se mejora la separación entre los componentes. Esto, a su vez, facilita la comprensión y los cambios cuando se modifican los requisitos.

  Puede utilizar un diagrama de componentes para representar el diseño con independencia del lenguaje o plataforma que el diseño utiliza o va a utilizar.

## <a name="OtherDiagrams"></a> Relationship to Other Diagrams
 Puede utilizar un diagrama de componentes junto con otros diagramas.

|Otro diagrama|Ayuda a debatir y transmitir los siguientes aspectos del diseño|
|-------------------|--------------------------------------------------------------------|
|Diagrama de secuencia UML|-   Interactions between a system's components<br />-   Interactions and between the parts inside a component.<br /><br /> For more information, see [UML Sequence Diagrams: Guidelines](../modeling/uml-sequence-diagrams-guidelines.md).|
|Diagrama de clases de UML|-   The interfaces of a component. El diagrama de clases permite detallar los métodos de la interfaz.<br />-   The data sent in parameters across the components' interfaces.<br /><br /> For more information, see [UML Class Diagrams: Guidelines](../modeling/uml-class-diagrams-guidelines.md).|
|Diagramas de actividades|-   The internal processing performed by a component in response to incoming messages.<br /><br /> For more information, see [UML Activity Diagrams: Guidelines](../modeling/uml-activity-diagrams-guidelines.md).|
|Diagramas de capas|-   Logical architectural tiers for your components.<br /><br /> For more information, see [Layer Diagrams: Reference](../modeling/layer-diagrams-reference.md).|

## <a name="Basics"></a> Basic Steps for Drawing Component Diagrams
 For reference information about the elements on component diagrams, see [UML Component Diagrams: Reference](../modeling/uml-component-diagrams-reference.md).

 For more information about how to use component diagrams in the process of design, see [Model your app's architecture](../modeling/model-your-app-s-architecture.md).

> [!NOTE]
> Detailed steps for creating any of the modeling diagrams are described in [Edit UML models and diagrams](../modeling/edit-uml-models-and-diagrams.md).

#### <a name="to-create-a-component-diagram"></a>Para crear un diagrama de componentes

1. On the **Architecture** menu, click **New UML or Layer Diagram**.

2. Under **Templates**, click **UML Component Diagram**.

3. Especifique un nombre para el diagrama.

4. In **Add to Modeling Project**, select an existing modeling project in your solution, or **Create a New Modeling Project**, and then click **OK**..

     A new component diagram appears with the UML **Component Diagram** toolbox. El cuadro de herramientas contiene las relaciones y elementos necesarios.

### <a name="drawing-components"></a>Dibujar componentes
 ![Components with interfaces](../modeling/media/uml-compdrawing.png "UML_CompDrawing")

 Create a *component* (1) for each major functional unit in your system or application.

 Algunos ejemplos pueden ser una aplicación, un dispositivo de hardware, un servicio Web, un ensamblado .NET, una clase o un grupo de clases de programa o cualquier segmento de un programa que se pueda separar.

##### <a name="to-create-components"></a>Para crear componentes

1. Click **Component** in the toolbox, and then click a blank part of the diagram.

     \- o -

     Copie y pegue un componente existente.

    1. Find an existing component in a diagram or in **UML Model Explorer**.

    2. Right-click the component and then click **Copy**.

    3. Abra el diagrama en el que desea que aparezca el componente copiado.

    4. Right-click a blank part of the diagram and then click **Paste**.

         Aparece una copia del componente con un nombre nuevo.

2. Haga clic en el nombre del componente para cambiarlo.

3. Haga clic en el botón de contenido adicional 5) si desea ver exclusivamente el encabezado del componente.

### <a name="showing-the-ports-of-a-component"></a>Mostrar los puertos de un componente
 A *port* (2, 3) represents a group of messages or operation calls that pass either into or out of a component. El grupo se describe mediante una interfaz, que define el tipo de puerto. Un puerto puede proporcionar o necesitar una interfaz.

 A port with a *provided interface* (2) supplies operations that are implemented by the component, and that can be used by other components.

 Algunos ejemplos serían una interfaz de usuario, un servicio Web, una interfaz de .NET o una colección de funciones de cualquier lenguaje de programación.

 A port with a *required interface* (3) represents a component's requirement for a group of operations or services to be provided by other components or external systems.

 Por ejemplo, un explorador web necesita servidores web o un complemento de la aplicación necesita los servicios de la aplicación.

 Un componente puede tener cualquier número de puertos.

##### <a name="to-add-ports-to-a-component"></a>Para agregar puertos a un componente

1. In the toolbox, click **Provided Interface** or **Required Interface**.

2. Haga clic en el componente al que desea agregar los puertos.

    Aparecerá un puerto en el límite del componente.

    Se crea una nueva interfaz como el tipo del puerto. This interface appears in **UML Model Explorer**.

3. Arrastre el puerto situado en torno al límite del componente hasta situarlo donde desee.

4. Arrastre la etiqueta del puerto hasta ajustar su posición.

5. Haga clic en la etiqueta para cambiarla. En la etiqueta se muestra el nombre de la interfaz. Si la modifica, cambiará el nombre de la interfaz.

   Si desea enumerar los atributos y las operaciones de la interfaz, puede hacerlo agregándolos a la interfaz en el Explorador de modelos UML. O bien, puede arrastrar la interfaz del Explorador de modelos UML a un diagrama de clases, y agregar las operaciones y atributos allí.

### <a name="linking-between-components"></a>Establecer vínculos entre componentes
 Utilice una dependencia 4) para mostrar que el requisito de un componente puede satisfacerse a través de las operaciones o servicios proporcionados por otro componente.

##### <a name="to-show-that-a-provided-interface-can-satisfy-a-required-interface"></a>Para mostrar que una interfaz proporcionada puede satisfacer una interfaz necesaria

1. In the toolbox, click **Dependency**.

2. Haga clic en el puerto con la interfaz necesaria de un componente y, a continuación, haga clic en el puerto con la interfaz proporcionada de otro componente.

   En la fase de diseño, intente evitar los bucles de dependencia en los que todos los componentes de un grupo dependen de todos los demás componentes.

##### <a name="to-add-a-port-for-an-existing-interface-to-a-component"></a>Para agregar un puerto de una interfaz existente a un componente

- Find the interface in **UML Model Explorer** and then drag it from there onto the component.

     o bien

- Copie y pegue una referencia a una interfaz desde un diagrama.

    1. On a class diagram or a component diagram, right-click the interface and then click **Copy**.

    2. On the component diagram, right-click the component, and then click **Paste Reference**.

         En el componente aparece una interfaz proporcionada. Cerca aparece una etiqueta de acción.

        > [!NOTE]
        > If you use **Paste** instead of **Paste Reference**, a new interface that has a new name will be created.

    3. If you wanted to create a required interface, click the Action tag and then click **Convert to Required Interface**.

## <a name="Parts"></a> Showing the Internal Parts of a Component
 ![Component diagram showing internal parts](../modeling/media/uml-compshowing.png "UML_CompShowing")

 Puede incluir elementos (3) en un componente (1) para mostrar que está formado de componentes más pequeños que interactúan entre sí.

 En el diagrama de la ilustración se muestra que todas las instancias del servicio Web Cenar ahora contienen una instancia del Servidor de cliente y una instancia del Servidor de cocina.

 Un elemento es una propiedad de su componente primario, al igual que un atributo pertenece a una clase ordinaria. Los elementos tienen su propio tipo, que suele ser también un componente. La etiqueta del elemento tiene el mismo formato que un atributo ordinario:

 `+ partName : TypeName`

 Dentro del componente primario, en cada elemento se muestran las interfaces proporcionadas y necesarias que se definieron para su tipo (4, 5). Las operaciones o servicios que necesita un elemento puede proporcionárselos otro. You can use **Part Assembly** connectors to show how parts are connected with one another (6).

 También puede mostrar que una interfaz del componente primario es una interfaz que uno de sus elementos proporciona o necesita. You can connect a port of the parent to a port of an internal part using a **Delegation** relation (9). Los dos puertos tienen que ser del mismo tipo (proporcionados o necesarios) y sus tipos de interfaz tienen que ser compatibles.

 Puede crear un nuevo elemento con un nuevo tipo o a partir de un tipo existente.

#### <a name="to-add-parts-to-a-component"></a>Para agregar elementos a un componente

1. Cree un elemento para cada unidad funcional principal que cree que forma parte del componente primario.

    1. Click **Component** in the toolbox, and then click inside the parent component (1).

         Aparece un nuevo elemento (3) dentro del componente primario.

         A new component is created in **UML Model Explorer**. Este es el nuevo tipo del elemento.

         \- o -

         Arrastre un componente existente del Explorador de modelos UML al componente primario.

         Aparece un nuevo elemento (3) dentro del componente primario. Su tipo es el componente que arrastró desde el Explorador de modelos UML.

         \- o -

         Right-click a component, either in a diagram or in UML Model Explorer, and then click **Copy**.

         Right-click on the parent component, and then click **Paste Reference**.

         Aparece un nuevo elemento (3) dentro del componente primario. Su tipo es el componente que copió.

    2. Haga clic en el nombre del nuevo componente para cambiarlo. Su tipo no se puede modificar.

    3. Puede agregar interfaces proporcionadas y necesarias (4, 5) al nuevo elemento. Click the **Provided Interface** or **Required Interface** tool, and then click in the part.

         \- o -

         Drag an existing interface from **UML Model Explorer** onto the part.

         Las interfaces se agregan al tipo del elemento y aparecen en el propio elemento. El componente primario ajusta su tamaño, si es necesario.

2. Conecte los elementos entre sí.

    - Use the **Dependency** tool to connect the ports of different parts (6).

3. Conecte los puertos a los puertos del componente primario:

    1. Cree uno o varios puertos (7) en el componente primario. Click **Required Interface** or **Provided Interface** on the toolbox, and then click the parent component.

    2. Cree delegados (9) del puerto en uno o varios elementos. Click the **Delegation** tool, then a port on the parent component, and then a port on a part. A través de este mismo mecanismo, puede conectar puertos que proporcionan o necesitan interfaces.

### <a name="showing-the-parts-of-a-part"></a>Mostrar los elementos que conforman un elemento
 Después de descomponer un componente en elementos, puede descomponer cada uno de los tipos de elementos en sus propios elementos internos.

 Resulta más fácil representar cada nivel de la descomposición en un diagrama de componentes diferente. Primero debe buscar el tipo del elemento. Por ejemplo, en la ilustración, uno de los elementos se denomina `DNCustomerServer` y su tipo es un componente que se denomina `CustomerServer`. Puede buscar este tipo en el Explorador de modelos UML y situarlo en otro diagrama. A continuación, puede crear sus propios elementos internos.

##### <a name="to-place-a-parts-type-on-a-diagram"></a>Para situar un tipo de elemento en un diagrama

1. Especifique el nombre completo del tipo de elemento.

     Right-click the part and then click **Properties**.

     The type name appears in the **Type** field of the Properties window.

2. Locate the part's type in **UML Model Explorer**.

     Click **View**, point to **Other Windows**, and then click **UML Model Explorer**.

     Expanda el proyecto y, si es necesario, los paquetes a los que pertenece el tipo.

     The type will be listed as a **Component**.

     Si lo desea, puede cambiar su nombre aquí.

3. Abra o cree otro diagrama de componentes.

4. Arrastre el tipo del Explorador de modelo UML al diagrama.

     En el diagrama aparece una vista del tipo como componente.

     Tiene las mismas interfaces que las que definió para el elemento.

     Ahora puede agregar otros elementos.

## <a name="Designing"></a> Designing the Component

### <a name="describing-how-the-parts-collaborate"></a>Describir cómo colaboran los elementos
 Puede dibujar un diagrama de secuencia para mostrar el modo en que los elementos trabajan juntos en respuesta a un mensaje que llega al componente primario.

 Puede utilizar estos diagramas para explicar un componente existente o diseñar uno nuevo.

 Si todavía está diseñando el componente, puede dibujar diagramas de secuencia antes de decidir qué elementos contendrá. Puede utilizar los diagramas de secuencia para experimentar con distintos elementos, interfaces necesarias y secuencias de mensajes. Dibuje diagramas de secuencia para los mensajes entrantes más frecuentes y más importantes. Puede crear elementos en el componente que se correspondan con las líneas de vida que haya decidido.

 Utilice los diagramas de secuencia para valorar el modo en que los diferentes componentes comparten el trabajo del sistema.

- Si la carga de trabajo es muy grande en un elemento, probablemente resultará más complicado actualizar la aplicación que si el trabajo se distribuye uniformemente.

- Si la carga de trabajo es demasiado escasa y se distribuye en muchas interacciones, el sistema podría tener un mal rendimiento y podría resultar difícil de entender.

  ![Sequence diagram showing collaborating parts](../modeling/media/uml-compdescparts.png "UML_CompDescParts")

##### <a name="to-draw-a-sequence-diagram-that-shows-collaboration-between-parts"></a>Para dibujar un diagrama de secuencia en el que se muestre la colaboración entre los elementos

1. Cree un nuevo diagrama de secuencia.

     For more information, see [UML Sequence Diagrams: Guidelines](../modeling/uml-sequence-diagrams-guidelines.md).

2. Cree una línea de vida en un componente externo, usuario, dispositivo u otro actor (1) que envíe mensajes a este componente.

     You can set the **Actor** property of this lifeline to true, to indicate that it is external to the component under consideration. Sobre la línea de vida aparece un dibujo esquemático.

3. Cree una línea de vida en la interfaz proporcionada (2) de este componente al que el actor seleccionado envía mensajes.

4. Cree una línea de vida en cada elemento (3) del componente.

5. Cree una línea de vida en cada interfaz necesaria (4) del componente.

6. Dibuje mensajes procedentes del actor externo (5). Muestre cómo se pasa el mensaje a los elementos y cómo estos elementos colaboran para responder al mensaje.

7. Siempre que sea necesario, muestre los mensajes enviados a una interfaz necesaria (6). No muestre los detalles de la ejecución del mensaje.

### <a name="is-the-component-more-than-its-parts"></a>¿Es el componente mayor que la suma de sus partes?
 En algunos casos, un componente no es más que un nombre que se asigna a una colección de elementos. Los elementos realizan todo el trabajo y no hay ningún código ni ningún otro artefacto en tiempo de ejecución que represente al componente.

 You can indicate this in the model by setting the **Is Indirectly Instantiated** property of the component. En este caso, todas las interfaces del componente deben estar en los puertos, con delegaciones en los elementos internos.

### <a name="describing-the-process-inside-each-part"></a>Describir el proceso que tiene lugar en cada elemento
 Puede utilizar diagramas de actividades para mostrar cómo un componente procesa cada mensaje entrante. For more information, see [UML Activity Diagrams: Guidelines](../modeling/uml-activity-diagrams-guidelines.md).

 ![Activity diagram with data buffer](../modeling/media/uml-compdescribingproc.png "UML_CompDescribingProc")

 Utilice una acción de evento de aceptación (1) para mostrar que un mensaje entrante inicia un nuevo subproceso.

 Utilice nodos de objeto y pins de entrada y salida para mostrar el flujo de información y dónde se almacena la información. En el ejemplo, se utiliza un nodo de objeto (2) para mostrar los elementos que se están almacenando en búfer entre un subproceso y otro.

### <a name="defining-data-and-classes"></a>Definir datos y clases
 Puede utilizar un diagrama de clases de UML para describir en detalle el contenido de:

- Las interfaces de los componentes. Cuando se agrega un puerto que requiere o proporciona interfaces a un componente, aparece una interfaz en el Explorador de modelos UML. Puede arrastrarla o copiarla en un diagrama de clases UML para mostrar sus atributos y operaciones, y las relaciones con otras interfaces.

- Los datos que se pasan en los parámetros de las operaciones de las interfaces.

- Los datos almacenados en los componentes, por ejemplo, tal y como se muestran en los flujos de objetos de los diagramas de actividades.

### <a name="general-dependencies-between-components"></a>Dependencias generales entre componentes
 Puede utilizar un diagrama de componentes para mostrar exclusivamente los elementos principales del diseño y sus interdependencias.

 ![A dependency between components](../modeling/media/uml-compdepend.png "UML_CompDepend")

 Use the **Dependency** tool to draw a dependency. Así indicará que el diseño de un componente se basa en otro.

 Entre los tipos habituales de dependencia se incluyen los siguientes:

- Un componente llama al código en otro.

- Un componente crea una instancia de una clase que se define en otra clase.

- Un componente usa información creada por otro componente.

  Puede utilizar el nombre de la flecha de dependencia para dar cuenta de un tipo de uso concreto. To set the name, right-click the arrow, then click **Properties**, and set the **Name** field in the properties window.

## <a name="see-also"></a>Vea también
 [Edit UML models and diagrams](../modeling/edit-uml-models-and-diagrams.md) [UML Component Diagrams: Reference](../modeling/uml-component-diagrams-reference.md) [UML Sequence Diagrams: Reference](../modeling/uml-sequence-diagrams-reference.md) [UML Use Case Diagrams: Reference](../modeling/uml-use-case-diagrams-reference.md) [UML Class Diagrams: Reference](../modeling/uml-class-diagrams-reference.md) [UML Component Diagrams: Reference](../modeling/uml-component-diagrams-reference.md) [Video: Designing the Physical Structure by using Component Diagrams](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-6-designing-a-projects-physical-structure)
