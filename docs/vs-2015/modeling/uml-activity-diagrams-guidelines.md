---
title: 'UML Activity Diagrams: Guidelines | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML diagrams, activity
- diagrams - modeling, activity
- diagrams - modeling, UML activity
- activity diagrams
- UML, activity diagrams
ms.assetid: fe5dbe96-79ab-483a-b9bc-44d0d1d3efc2
caps.latest.revision: 50
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 692859008891439e4af3d751306bfd3ee6d351e8
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298991"
---
# <a name="uml-activity-diagrams-guidelines"></a>Diagramas de actividades UML: Instrucciones
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En Visual Studio, puede dibujar un diagrama de actividades para describir un proceso de negocio o un algoritmo de software como un flujo de trabajo a través de una serie de acciones. Las personas, los componentes de software o los dispositivos pueden realizar estas acciones. For a video demonstration, see: [Capture Business Workflows by using Activity Diagrams](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-4-capture-business-workflows).

 Para ver qué versiones de Visual Studio admiten esta característica, vea [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 To create a UML activity diagram, on the **Architecture** menu, click **New UML or Layer Diagram**.

 Puede usar un diagrama de actividades para muchos fines:

- Para describir un proceso de negocio o un flujo de trabajo entre los usuarios y el sistema. For more information, see [Model user requirements](../modeling/model-user-requirements.md).

- Para describir los pasos que se realizan en un caso de uso. For more information, see [UML Use Case Diagrams: Guidelines](../modeling/uml-use-case-diagrams-guidelines.md).

- Para describir un método, una función o una operación en el software. For more information, see [Model your app's architecture](../modeling/model-your-app-s-architecture.md).

  Dibujar un diagrama de actividades puede ayudarle a mejorar un proceso. Si el diagrama de un proceso existente resulta muy complejo, puede considerar cómo se podría simplificar el proceso.

  For reference information about the elements on activity diagrams, see [UML Activity Diagrams: Reference](../modeling/uml-activity-diagrams-reference.md).

## <a name="Relationships"></a> Relationship to Other Diagrams
 Si dibuja un diagrama de actividades para describir un proceso de negocio o la manera en que los usuarios usan el sistema, puede dibujar un diagrama de casos de uso para mostrar una vista diferente de la misma información. En el diagrama de casos de uso, las acciones se dibujan como casos de uso. Asigne a los casos de uso los mismos nombres que las acciones correspondientes. Las ventajas de la vista de casos de uso son las siguientes:

- Puede mostrar en un diagrama la manera en que las acciones y los casos de uso más grandes se componen de otros más pequeños, mediante la relación Includes.

- Puede conectar cada acción o caso de uso explícitamente a los usuarios o a los sistemas externos implicados en su ejecución.

- Puede dibujar límites alrededor de las acciones y los casos de uso admitidos por el sistema o alrededor de cada componente importante.

  También puede dibujar un diagrama de actividades para describir el diseño detallado de una operación de software.

  En un diagrama de actividades, puede mostrar el flujo de datos que se pasan entre las acciones. See the section on [Describing Data Flow](#DataFlows). Sin embargo, un diagrama de actividades no describe la estructura de los datos. Para ello, puede dibujar un diagrama de clases UML. For information see [UML Class Diagrams: Guidelines](../modeling/uml-class-diagrams-guidelines.md).

## <a name="BasicSteps"></a> Basic Steps for Drawing Activity Diagrams
 Detailed steps for creating any of the modeling diagrams are described in [Edit UML models and diagrams](../modeling/edit-uml-models-and-diagrams.md).

#### <a name="to-draw-an-activity-diagram"></a>Para dibujar un diagrama de actividades

1. On the **Architecture** menu, click **New UML or Layer Diagram**.

2. Under **Templates**, click **UML Activity Diagram**.

3. Especifique un nombre para el diagrama.

4. In **Add to Modeling Project**, select an existing modeling project in your solution, or **Create a New Modeling Project**.

#### <a name="to-draw-elements-on-an-activity-diagram"></a>Para dibujar elementos en un diagrama de actividades

1. Arrastre elementos desde el cuadro de herramientas al diagrama.

     Comience colocando las actividades principales en el diagrama, conéctelas e incorpore los últimos detalles, como los nodos iniciales y finales.

    > [!NOTE]
    > No puede arrastrar elementos existentes al diagrama desde el Explorador de modelos UML.

2. Para conectar los elementos, siga estos pasos:

    1. In the **Activity Diagram** toolbox, click **Connector**.

    2. En el diagrama, haga clic en el elemento de origen.

    3. Haga clic en el elemento de destino.

        > [!NOTE]
        > Para usar una herramienta varias veces, haga doble clic en la herramienta en el cuadro de herramientas.

#### <a name="to-move-an-activity-to-another-package"></a>Para mover una actividad a otro paquete

- In **UML Model Explorer**, drag the activity into a package.

     \- o -

- In **UML Model Explorer**, right-click the activity and click **Cut**. Then right-click the package and click **Paste**.

    > [!NOTE]
    > La actividad aparecerá en el Explorador de modelos UML solo cuando se agregue el primer elemento al diagrama.

## <a name="SimpleControlFlow"></a> Describing Control Flow
 Un diagrama de actividades describe un proceso de negocio o un algoritmo de software como una serie de acciones. Las flechas de conector muestran cómo el control pasa secuencialmente de una acción a la siguiente. Normalmente, una acción solo se puede iniciar una vez completada la acción anterior.

 La ilustración siguiente es un ejemplo de cómo se puede mostrar una secuencia de acciones mediante acciones, conectores, bifurcaciones y bucles. Cada elemento se explica con más detalle en las secciones siguientes.

 ![A simple activity diagram](../modeling/media/uml-actguidectrl.png "UML_ActGuideCtrl")

 Activity diagrams use **Actions** and **Connectors** to describe your system or application as a series of actions with the control flowing sequentially from one action to the next.

- Create an **Action** (1) for each major task that is performed by a user, the system, or both in collaboration.

  > [!NOTE]
  > Intente describir su proceso o algoritmo con unas pocas acciones. You can use **Call Behavior Actions** to define each action in more detail in a separate diagram, as described in [Describing Sub-activities with Call Behavior Actions](#Subactivities).

- Asegúrese de que el título de cada acción indica claramente lo que suele hacer.

- Link the actions in sequence with **Connectors** (2).

- Cada acción finaliza antes de que comience la acción siguiente del flujo de control. If you want to describe actions that overlap, use a **Fork Node** as described in the section [Concurrent Flows](#Concurrent).

  Aunque el diagrama describe la secuencia de acciones, no describe cómo se ejecutan las acciones o cómo se pasa el control de una acción a la siguiente. Si usa el diagrama para representar un proceso de negocio, el control podría pasarse, por ejemplo, cuando una persona envía un mensaje de correo electrónico. Si usa el diagrama para representar un diseño de software, el flujo de ejecución normal podría pasar el control de una instrucción a la siguiente.

### <a name="describing-decisions-and-loops"></a>Describir decisiones y bucles

- Use a **Decision Node** (3) to indicate a point where the outcome of a decision dictates the next step. Puede dibujar tantas rutas de acceso de salida como desee.

- Si usa el diagrama de actividades para definir parte de una aplicación, debe definir las restricciones (4) para que quede claro cuándo se debe tomar cada ruta de acceso. Right-click the connector, click **Properties**, and in the **Properties** window, type a value for the **Guard** field.

- No siempre es necesario definir las restricciones. Por ejemplo, si usa el diagrama de actividades para describir un proceso de negocio o un protocolo de interacción, una bifurcación define el intervalo de opciones disponibles para el usuario o para los componentes que interactúan.

- Use a **Merge Node** (5) to bring together two or more alternative flows that branched at a **Decision Node**.

    > [!NOTE]
    > You should use a **Merge Node** to bring together alternative flows, instead of bringing the flows together at an action. In the example, it would not be correct to connect from the decision node directly back to **Choose Menu Item**. Esto se debe a que una acción no se inicia hasta que los subprocesos de control llegan a todos sus conectores de entrada. Por lo tanto, en una acción solo debe reunir flujos simultáneos. For more information, see [Concurrent Flows](#Concurrent).

- Use las bifurcaciones para describir bucles, tal como se muestra en el ejemplo.

    > [!NOTE]
    > Intente anidar los bucles de forma bien estructurada, tal como lo haría en el código del programa. Si está describiendo un proceso de negocio existente, esto podría ofrecer oportunidades para mejorarlo.

### <a name="starting-the-activity"></a>Iniciar la actividad
 Existen dos maneras de indicar los puntos de entrada en una actividad:

- **Initial Node**

     Create one **Initial Node** (6) to indicate the first action of the activity.

     Este método es muy útil cuando se describe una actividad secundaria o cuando no es necesario indicar explícitamente qué inicia la actividad. Por ejemplo, no cabe duda de que la actividad Pedir un menú se inicia cuando un cliente tiene hambre.

- **Accept Event Node**

     Create **Accept Event Nodes**, as described in the section [Concurrent Flows](#Concurrent), to indicate the start of a thread that responds to a particular event, such as a user input. No proporcione un flujo de entrada al nodo. Al omitir el flujo de entrada, se indica que se iniciará un subproceso cada vez que se produzca el evento.

     Este método es muy útil cuando se describe una respuesta a un evento externo concreto.

### <a name="ending-the-activity"></a>Finalizar la actividad
 Use an **Activity Final Node** (7) to indicate the end of an activity.

- When a thread of control reaches an **Activity Final Node**, all the activity's concurrent actions and sub-activities terminate.

- Puede usar más de un nodo de final de actividad para reducir la cantidad de conectores adicionales.

### <a name="interrupting-the-activity"></a>Interrumpir la actividad
 Para describir cómo se puede interrumpir el flujo normal de una actividad, por ejemplo, si el usuario decide cancelar el proceso, puede crear un nodo de aceptación de evento que escuche ese evento. For more information, see the section [Concurrent Flows](#Concurrent). Cree un flujo de control desde ese nodo hasta un nodo de final de actividad (7).

### <a name="swimlanes"></a>Calles
 A veces resulta útil organizar las acciones de una actividad en áreas que se corresponden con distintos objetos o roles de negocio que realizan las acciones. These areas are conventionally arranged in columns and are called *swimlanes*.

- Use lines or rectangles from the **Simple Shapes** section of the Toolbox to draw swimlanes or other areas.

- To label each swimlane, create a comment and set its **Transparent** property to **True**.

  Las formas simples no forman parte del modelo UML y no aparecen en el Explorador de modelos UML.

## <a name="DataFlows"></a> Describing Data Flow
 Puede describir los datos que entran y salen de una actividad de dos maneras:

- Use an **Object Node**. Este es el método más sencillo para describir la información que fluye entre las actividades. Un nodo de objeto es como una variable de un programa. Representa algo que almacena uno o varios valores que se pasan de una acción a otra.

- Use an **Output Pin** and an **Input Pin**. Este método permite describir por separado las salidas de una acción y las entradas en otra. Los terminales son como los parámetros de un programa. Los terminales representan puertos donde pueden entrar los objetos y dejar una acción.

    > [!NOTE]
    > For an overview of the elements used in this section, see the Data Flows section of the topic see [UML Activity Diagrams: Reference](../modeling/uml-activity-diagrams-reference.md).

### <a name="describing-data-flow-with-object-nodes"></a>Describir el flujo de datos con nodos de objeto
 La mayoría de los flujos de control transportan datos. Por ejemplo, el flujo de salida de la acción "El cliente proporciona detalles" lleva una referencia a la dirección de envío.

 Si desea describir esos datos en el diagrama, puede reemplazar un conector con un nodo de objeto y dos conectores, tal como se muestra en la ilustración siguiente.

 ![Object nodes can show data passed between actions](../modeling/media/uml-actguidedata.png "UML_ActGuideData")

 Observe que los rectángulos redondeados, como Despachar mercancía, representan acciones en las que tiene lugar el procesamiento. Los rectángulos cuadrados, como Dirección de envío, representan un flujo de objetos de una acción a otra.

 Asigne al nodo de objeto un nombre que refleje el rol del nodo como canalización o búfer de los objetos que fluyen entre las acciones.

 You can set the **Type** of the object node in the Properties window. El tipo puede ser un tipo primitivo, como un entero, o una clase, interfaz o enumeración que definiese en un diagrama de clases. Por ejemplo, podría crear una clase Dirección de envío, con atributos como Dirección, Ciudad, etcétera, junto con una asociación con otra clase denominada Cliente. For more information, see [UML Class Diagrams: Guidelines](../modeling/uml-class-diagrams-guidelines.md).

> [!NOTE]
> If you type the name of a type that has not yet been defined, an item will be added under **Unspecified Types** in UML Model Explorer. Si posteriormente define un tipo con ese nombre en un diagrama de clases, deberá restablecer el tipo del nodo de objeto para que haga referencia al nuevo tipo.

#### <a name="buffering-data-in-object-nodes"></a>Almacenar en búfer los datos de los nodos de objeto
 Un nodo de objeto puede actuar como búfer de varios objetos. En la ilustración siguiente, el flujo de control muestra que el usuario puede recorrer el bucle [elegir más] (1) muchas veces, mientras el nodo de objeto Elementos del menú seleccionados (2) acumula las selecciones del usuario. Por último, cuando el usuario finaliza su selección, el control pasa a la acción Confirmar pedido (3), que acepta la lista completa de selecciones del búfer Elementos de menú seleccionados.

 ![Buffering data in object nodes](../modeling/media/uml-actguidebuffer.png "UML_ActGuideBuffer")

 Puede especificar cómo se almacenan los elementos de un búfer estableciendo las propiedades del nodo de objeto:

- Set the **Ordering** property:

  - **Unordered** to specify a random or unspecified order. (Valor predeterminado).

  - **Ordered** to specify an order according to a specific key.

  - **Fifo** to specify an order of first-in, first-out.

  - **Lifo** to specify an order of last-in, first-out.

- Set the **Upper Bound** property to specify the maximum number of objects that can be contained in the buffer. El valor predeterminado es *. Esto significa que no hay límite.

### <a name="describing-data-flow-with-input-and-output-pins"></a>Describir el flujo de datos con terminales de entrada y salida
 Use an **Output Pin** and an **Input Pin** to separately describe the outputs from one action and the inputs to another.

 ![Input and output pins are action parameters](../modeling/media/uml-actguidepins.png "UML_ActGuidePins")

 To create a pin, click **Input Pin** or **Output Pin** on the toolbox and then click an action. A continuación, puede mover el terminal alrededor del perímetro de la acción y cambiarle el nombre. You can create input and output pins on any kind of action, including **Call Behavior Actions**, **Call Operation Actions**, **Send Signal Actions**, and **Accept Event Actions**.

 Un conector entre dos terminales representa un flujo de objetos, al igual que los flujos de entrada y salida de un nodo de objeto.

 Asigne a cada terminal un nombre que indique el rol de los objetos que genera o acepta, como un nombre de parámetro.

 You can set the type of objects transmitted in the **Type** property. Debe tratarse de un tipo creado en un diagrama de clases UML.

 Los objetos que fluyen entre los terminales conectados deben ser compatibles de alguna manera. La razón es que los objetos generados por el terminal de salida pertenecen a un tipo derivado del tipo del terminal de entrada.

 También puede especificar que el flujo de objetos incluye una transformación que convierte los datos entre el tipo del terminal de salida y el tipo del terminal de entrada. La transformación más común de este tipo solamente extrae la parte adecuada de un tipo mayor. El ejemplo de la ilustración implica la existencia de una transformación que extrae la dirección de envío de los detalles del pedido.

## <a name="Details"></a> Defining an Action in More Detail
 Además de usar el nombre de la acción para indicar claramente el resultado que normalmente se debe conseguir, existen otras maneras de agregar más detalles a una acción:

- Write a more detailed description in the **Body** property. Por ejemplo, puede escribir un fragmento de código o seudocódigo de programa o una descripción completa de los resultados obtenidos.

- Reemplace la acción con una acción de llamada a comportamiento y describa su comportamiento detallado en un diagrama de actividades independiente. See [Describing Sub-activities with Call Behavior Actions](#Subactivities).

- Set the action's **Local Postconditions** and **Local Preconditions** properties to describe its outcome in more specific detail. For more information, see [Defining Postconditions and Preconditions](#Postcondition).

### <a name="Subactivities"></a> Describing Sub-activities with Call Behavior Actions
 Puede describir el comportamiento detallado de una acción usando un diagrama de actividades independiente. Un comportamiento llamado es un diagrama de actividades que se representa en el diagrama de actividades principal mediante una acción de llamada a comportamiento. También puede usar la acción de llamada a comportamiento para describir el comportamiento que se comparte entre las diferentes actividades, de modo que no tenga que dibujar varias veces la actividad secundaria.

 En la ilustración siguiente, el diagrama 1 muestra una actividad que tiene una acción de llamada a comportamiento, mientras que el diagrama 2 muestra el diagrama de actividad secundaria donde puede verse el comportamiento llamado.

 ![A separate activity diagram shows detailed actions](../modeling/media/uml-actguidedetail.png "UML_ActGuideDetail")

##### <a name="to-describe-a-sub-activity-with-a-call-behavior-action"></a>Para describir una actividad secundaria con una acción de llamada a comportamiento

1. To create the diagram for the sub-activity, in **Solution Explorer**, right-click your modeling project, point to **Add**, and then click **New Item**.

2. In the **Add New Item** dialog box, under **Templates** click **Activity Diagram** and in the **Name** box type the name that you plan to give your **Call Behavior Action**.

3. Dibuje el flujo de trabajo detallado de la actividad secundaria. Este es el comportamiento llamado.

    - In the called sub-activity diagram, the **Initial Node** indicates where control starts when the called behavior is invoked. The **Activity Final Node** shows where control should return to the parent activity.

4. Set the **Behavior** property of the **Call Behavior Action** to refer to the called behavior diagram.

    > [!NOTE]
    > The sub-activity diagram must have some elements on it or the diagram will not be available in the drop-down list for the **Behavior** property. Also, the trident icon will not appear on your **Call Behavior Action** shape until you set its **Behavior** property.

5. Set the **Is Synchronous** property of the action to indicate whether your activity waits for the called activity to complete.

    - If you set **Is Synchronous** to false, you are indicating that the flow can continue to the next action before the called activity finishes. No debe definir terminales de salida o flujos de datos salientes desde la acción.

### <a name="describing-data-flow-in-and-out-of-sub-activities"></a>Describir el flujo de datos dentro y fuera de las actividades secundarias
 Puede describir los datos que fluyen dentro y fuera de las actividades secundarias de la misma manera que usa los parámetros en el software.

- Cree terminales de entrada y salida (1) en la acción de llamada a comportamiento para cada elemento de datos que fluya dentro o fuera de la acción. Asigne a cada uno un nombre apropiado.

- In the sub-activity diagram, create an **Activity Parameter Node** (2) for each input and output pin on the calling action. Asigne a cada nodo el mismo nombre que el de su terminal correspondiente.

  > [!NOTE]
  > Un nodo de parámetros de actividad se parece a un nodo de objeto. To check what type of node that you are looking at, right-click the node and then click **Properties**. El tipo de nodo se muestra en el encabezado de la ventana Propiedades.

- En el diagrama de actividad secundaria, dibuje conectores que muestren el flujo de objetos dentro o fuera de cada nodo de parámetros de actividad.

  ![Pins on Call Behavior map to activity parameters](../modeling/media/uml-actguidesub.png "UML_ActGuideSub")

### <a name="Postcondition"></a> Defining Postconditions and Preconditions
 You can use the **Local Postconditions** and **Local Preconditions** properties to specify in detail the outcome of an action. Estas propiedades describen el efecto de la acción sin describir cómo se consigue el efecto.

 To set these properties, right-click the action and then click **Properties**. Escriba los valores de las propiedades en la ventana Propiedades.

#### <a name="local-postconditions"></a>Local Postconditions
 Una condición posterior es una condición que debe cumplirse antes de que la acción pueda considerarse completada. En el ejemplo, en la acción Confirmar pedido, la condición posterior puede ser:

 El cliente proporcionó detalles completos y válidos que son necesarios para procesar su tarjeta de crédito.

 Una condición posterior puede expresar una relación entre los estados antes y después de que se produzca la acción. Por ejemplo:

 El tipo de interés es el doble de antes.

 Puede escribir condiciones posteriores con un estilo más formal, haciendo referencia a atributos específicos de los datos implicados en las acciones. Por ejemplo:

 `InvoiceTotal == Sum(OrderItem.MenuItem.Price)`

#### <a name="local-preconditions"></a>Local Preconditions
 Una condición previa es una condición que debe ser true cuando la acción está a punto de comenzar. Por ejemplo, la acción Confirmar pedido podría tener la condición previa siguiente:

 El cliente eligió al menos un elemento del menú.

### <a name="describing-calls-to-operations"></a>Describir las llamadas a operaciones
 Por lo general, una acción describe el trabajo que lleva a cabo una combinación de personas, software o equipos. Sin embargo, puede usar una acción de llamada a operación para describir una llamada a un determinado método o función de software.

- Establezca el nombre de la acción de llamada a operación para indicar a qué operación se llama y en qué objeto o componente.

- Agregue terminales de entrada y salida a la acción de llamada a operación para describir los parámetros y los valores devueltos.

- You can set the **Is Synchronous** property of the action to indicate whether your activity waits for the operation to complete.

  - If you set **Is Synchronous** to false, you are indicating that the flow can continue to the next action before the called operation is complete. No debe definir terminales de salida o flujos de datos salientes desde la acción.

## <a name="Concurrent"></a> Concurrent Flows
 You can use the **Fork Node** and the **Join Node** to describe two or more threads of activities that can execute at the same time.

 ![The fork and join nodes show concurrent flows](../modeling/media/uml-actguideconcurrent.png "UML_ActGuideConcurrent")

 The effect of the **Fork Node** (1) is to divide the thread of control into two or more threads. Cuando finalice la acción anterior, podrán iniciarse todas las acciones del lado de salida de la bifurcación.

 A **Join Node** (2) brings concurrent threads together. The action after the **Join Node** may not start until all the actions leading to the **Join Node** are complete.

### <a name="describing-signals-and-events"></a>Describir señales y eventos
 Puede mostrar un paso en un proceso que envía una señal como una acción de envío de señal de una actividad. Puede mostrar un paso que espera una señal específica o un evento antes de que el paso pueda continuar como una acción de aceptación de evento.

 Por ejemplo, puede mostrar un paso que envía un pedido y, a continuación, otro paso que debe recibir el pedido antes de procesarlo.

#### <a name="sending-a-signal"></a>Enviar una señal
 Use una acción de envío de señal (3) para indicar que se envía una señal o un mensaje de algún tipo a otras actividades o procesos. Use el nombre de la acción para indicar qué tipo de mensaje se envía.

- El control pasa inmediatamente a la acción siguiente del flujo de control, si la hay.

- No puede usar una acción de envío de señal para describir cómo responde el proceso a una información devuelta. Para ello, use una acción de aceptación de evento independiente.

- Puede mostrar el flujo de datos entrante en una acción de envío de señal para indicar qué datos pueden enviarse con el mensaje saliente. For more information, see [Describing Data Flow](#DataFlows).

#### <a name="waiting-for-a-signal-or-event"></a>Esperar una señal o evento
 Use una acción de aceptación de evento (4) para indicar que esta actividad espera algún evento externo o mensaje entrante. Use el nombre de la acción para indicar el tipo de evento que espera.

- Para mostrar que la actividad espera un mensaje o evento externo en un punto concreto de su flujo, dibuje una acción de aceptación de evento con un flujo de entrada en el lugar adecuado de la actividad.

- Para mostrar que la actividad puede responder a un mensaje o evento externo en cualquier momento, dibuje una acción de aceptación de evento sin flujo de entrada. Cuando se produce el evento externo con nombre, se iniciará un nuevo subproceso en la actividad a partir de la acción de aceptación de evento.

- No puede usar una acción de aceptación de evento para describir el valor devuelto al remitente de la señal. Use una acción de envío de señal diferente para ese propósito.

- Puede mostrar flujos de datos salientes de la acción para indicar cómo procesa la actividad los datos que se reciben en la señal. If you want to show more than one output flow, you should set the **IsUnmarshall** property of the Accept Event Action, which indicates that the action parses the incoming signal into its separate components. For more information, see [Describing Data Flow](#DataFlows).

### <a name="describing-multiple-data-flows"></a>Describir varios flujos de datos
 Puede dibujar más de un flujo de control o flujo de objeto saliendo de una acción para indicar que varios subprocesos emergen cuando finaliza la acción. El efecto es similar al de una bifurcación, salvo que se puede usar una combinación de flujos de control y objeto.

 El ejemplo siguiente muestra varios flujos que entran y salen de acciones.

 ![Parallel object flows](../modeling/media/uml-actguidemulti.png "UML_ActGuideMulti")

 Cuando se completa la acción "El cliente proporciona detalles", se generan dos objetos: "Dirección de envío" y "Detalles de la tarjeta de crédito". Los dos objetos avanzan en el procesamiento mediante acciones diferentes.

 Dado que una acción requiere que todas sus entradas estén disponibles antes de iniciarse, la última acción no se inicia hasta que se completen todas las acciones anteriores.

### <a name="streams"></a>Secuencias
 Puede usar un diagrama de actividades para describir una canalización o una serie de acciones que se ejecutan al mismo tiempo y pasan datos continuamente de una acción a otra.

 La finalidad del ejemplo siguiente es que cada acción genere objetos y siga funcionando. Dado que no hay flujos de control, cada acción se puede iniciar en cuanto recibe sus primero objetos.

 Observe que los conectores de este ejemplo son flujos de objeto, ya que todos tienen al menos un extremo en un nodo de parámetros de actividad, un nodo de objeto o un terminal de entrada o salida.

 ![A data flow](../modeling/media/uml-actguidestream.png "UML_ActGuideStream")

 1. El ejemplo tiene tres nodos de parámetros de actividad, que representan sus entradas y salidas.

 2. Los nodos de objeto, los terminales de entrada y los terminales de salida pueden representar búferes. Puede establecer la propiedad Upper Bound de un nodo de objeto para indicar cuántos objetos puede haber en el búfer al mismo tiempo.

 3. Puede usar los nodos de decisión para mostrar que una secuencia se divide y envía objetos diferentes por bifurcaciones diferentes. Puede usar los comentarios o los títulos de los nodos para explicar cuál es el criterio de división.

 4. Puede usar los nodos de bifurcación para mostrar que se realizan dos o más copias de los objetos, que se envían para el procesamiento simultáneo.

 5. Puede usar los nodos de unión para mostrar que dos secuencias de procesamiento se combinan en una sola.

### <a name="selection-and-transformation"></a>Selección y transformación
 Puede especificar que los objetos de un flujo de objeto se transforman, se seleccionan o ambas cosas. Un flujo de objeto es un flujo que sale o entra de un terminal o un nodo de objeto.

- Una transformación describe la manera en que los objetos que entran en un flujo se convierten en otro tipo.

- Una selección describe cómo solo algunos de los objetos que entran en un flujo se transmiten a la acción receptora.

  En el ejemplo se muestra una transformación. La primera acción del diagrama 1 genera un código postal en un terminal de salida. Este se conecta a un terminal de entrada de la segunda acción. Sin embargo, la segunda acción espera una dirección completa. La conversión de un tipo a otro se especifica en una segunda actividad, denominada Búsqueda de direcciones, a la que se hace referencia en la propiedad Transformation del flujo de objeto. La actividad Búsqueda de direcciones contiene un nodo de parámetros de actividad para el código postal de entrada y otro nodo de parámetros de actividad para la dirección completa de salida.

  ![Object transformation defined in another diagram](../modeling/media/uml-actguidetransform.png "UML_ActGuideTransform")

  Puede especificar una transformación o selección de dos maneras:

- Adjunte un comentario al terminal de entrada o salida.

  - To distinguish this description from a general comment, you can begin the comment with <\<**transformation**>> or <\<**selection**>>.

- Especifique con detalle la transformación o selección en un diagrama de actividades independiente.

  - Si usa este método, adjunte también un comentario para dejar claro a los lectores que se definió la transformación.

##### <a name="to-specify-a-transformation-or-selection-in-a-separate-activity-diagram"></a>Para especificar una transformación o selección en un diagrama de actividades independiente

1. Cree un nuevo diagrama de actividades en el que se describa el flujo de transformación o selección.

   - In **Solution Explorer**, right-click your project, point to **Add**, click **New Item**, and then click **Activity Diagram**. Asigne al diagrama un nombre adecuado para el flujo de transformación o selección. Haga clic en **Agregar**.

2. En el nuevo diagrama:

   1. Cree dos nodos de parámetros de actividad, uno para el flujo de entrada y otro para el de salida.

   2. Cree acciones interconectadas con los flujos de objeto. De esta manera se muestra cómo funciona la transformación o la selección.

3. En los diagramas en los que desee usar la transformación o la selección:

   1. Cree un flujo de objeto, es decir, un conector que entre o salga de un terminal de entrada o salida, un nodo de objeto o un nodo de parámetros de actividad.

   2. Right-click the object flow and then click **Properties**.

   3. In the **Transformation** or **Selection** property, select the diagram where you specified the transformation or selection flow.

   También puede definir una selección en un nodo de objeto y en terminales de entrada y salida individuales. Define a selection activity as in the previous procedure, and then set the **Selection** property of the object node, or input or output pin.

## <a name="see-also"></a>Vea también
 [Edit UML models and diagrams](../modeling/edit-uml-models-and-diagrams.md) [UML Sequence Diagrams: Reference](../modeling/uml-sequence-diagrams-reference.md) [UML Component Diagrams: Reference](../modeling/uml-component-diagrams-reference.md) [UML Use Case Diagrams: Reference](../modeling/uml-use-case-diagrams-reference.md) [UML Class Diagrams: Reference](../modeling/uml-class-diagrams-reference.md) [UML Component Diagrams: Reference](../modeling/uml-component-diagrams-reference.md) [Video: Capture Business Workflows by using Activity Diagrams](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-4-capture-business-workflows)
