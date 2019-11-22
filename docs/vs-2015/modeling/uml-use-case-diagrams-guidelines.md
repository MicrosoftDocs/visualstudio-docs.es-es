---
title: 'UML Use Case Diagrams: Guidelines | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- diagrams - modeling, use case
- UML, use case diagrams
- diagrams - modeling, UML use case
- use case diagrams
- UML diagrams, use case
ms.assetid: b1ae8ed0-d00b-4f9b-8e23-733e09e81e9b
caps.latest.revision: 38
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7c9ccd5285f9a2744704c0ee13094a1dac31c53b
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302839"
---
# <a name="uml-use-case-diagrams-guidelines"></a>Diagramas de casos de uso de UML: Instrucciones
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio, you can draw a *use case diagram* to summarize who uses your application or system, and what they can do with it. To create a UML use case diagram, on the **Architecture** menu, click **New UML or Layer Diagram**.

 For a video demonstration, see [Organizing Features into Use Cases](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-2-organizing-features-into-use-cases).

 Para ver qué versiones de Visual Studio admiten esta característica, vea [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Con la ayuda de un diagrama de casos de uso, puede analizar y comunicar:

- Los escenarios en los que el sistema o aplicación interactúa con personas, organizaciones o sistemas externos.

- Los objetivos que el sistema o aplicación contribuye a lograr.

- El ámbito del sistema.

  En un diagrama de casos de uso no se muestran los casos de uso en detalle; solamente se resumen algunas de las relaciones entre los casos de uso, los actores y los sistemas. En concreto, en el diagrama no se muestra el orden en que se llevan a cabo los pasos para lograr los objetivos de cada caso de uso. Esos detalles pueden describirse en otros diagramas y documentos, que pueden vincularse a cada caso de uso. For more information, see [Describing Use Cases in Detail](#Details) in this topic.

  En las descripciones que se proporcionen de los casos de uso se usarán diversos términos relacionados con el dominio en el que trabaja el sistema, como Ventas, Menú, Cliente, etc. Es importante definir de manera clara estos términos y sus relaciones y, para ello, puede resultar útil un diagrama de clases de UML. For more information, see [UML Class Diagrams: Guidelines](../modeling/uml-class-diagrams-guidelines.md).

  Los casos de uso solamente se usan para los requisitos funcionales de un sistema. Otros requisitos, como las reglas de negocio, los requisitos de calidad del servicio y las restricciones de implementación, deben representarse por separado. La arquitectura y los detalles internos también deben describirse por separado. For more information about how to define user requirements, see [Model user requirements](../modeling/model-user-requirements.md).

  Los ejemplos que se usan en este tema están relacionados con un sitio web en el que los clientes pueden hacer pedidos de comida de restaurantes locales.

  ![Elements in a use case diagram](../modeling/media/uml-ucovactor.png "UML_UCOvActor")

- An *actor* (1) is a class of person, organization, device, or external software component that interacts with your system. Example actors are **Customer**, **Restaurant**, **Temperature Sensor**, **Credit Card Authorizer.**

- A *use case* (2) represents the actions that are performed by one or more actors in the pursuit of a particular goal. Example use cases are **Order Meal**, **Update Menu**, **Process Payment**.

   En un diagrama de casos de uso, casos de uso están asociados (3) a los actores que los realizan.

- Your *system (4)* is whatever you are developing. Puede ser un pequeño componente de software cuyos actores simplemente son otros componentes de software; puede ser una aplicación completa; o puede ser un gran conjunto de aplicaciones distribuidas que se implementan en muchos equipos y dispositivos. Example subsystems are **Meal Ordering Website**, **Meal Delivery Business**, **Website Version 2**.

   En un diagrama de casos de uso pueden mostrarse los casos de uso que el sistema o sus subsistemas admiten.

## <a name="BasicSteps"></a> Basic Steps for Drawing Use Case Diagrams

> [!NOTE]
> Detailed steps for creating any of the modeling diagrams are described in [Edit UML models and diagrams](../modeling/edit-uml-models-and-diagrams.md).

#### <a name="to-create-a-new-use-case-diagram"></a>Para crear un nuevo diagrama de casos de uso

1. On the **Architecture** menu, click **New UML or Layer Diagram**.

2. Under **Templates**, click **UMLUse Case Diagram**.

3. Especifique un nombre para el diagrama.

4. In **Add to Modeling Project**, select an existing modeling project in your solution, or **Create a New Modeling Project**, and then click **OK**.

#### <a name="to-draw-a-use-case-diagram"></a>Para dibujar un diagrama de casos de uso

1. Drag **Subsystem** boundaries from the toolbox onto the diagram, to represent either your whole system or its major components.

    - Si no desea describir los casos de uso que el sistema o sus componentes admiten, puede dibujar un diagrama de casos de uso sin límites de sistema.

    - Si es necesario, arrastre la esquina de un sistema para hacerlo más grande.

    - Cambie su nombre como corresponda.

2. Drag **Actors** from the toolbox onto the diagram (placing them outside any system boundary).

    - Los actores representan las clases de usuarios, organizaciones y sistemas externos que interactúan con el sistema.

    - Cámbieles el nombre. For example: **Customer, Restaurant, Credit card agency.**

3. Drag **Use Cases** from the toolbox onto the appropriate systems.

    - Los casos de uso representan las actividades que los actores realizan con la ayuda del sistema.

    - Asígneles títulos que los propios actores puedan reconocer. No use títulos que tengan relación con el código. For example: **Order Meal, Pay for Meal, Deliver Meal**.

    - Begin with major transactions such as **Order Meal**, leaving until later smaller interactions such as **Select Menu Item**.

    - Sitúe cada caso de uso en el sistema o el subsistema principal compatible (omita los elementos de fachada o los componentes que solamente están implicados en la conexión con el usuario).

    - Puede dibujar un caso de uso fuera del límite de sistema para mostrar que dicho caso de uso no es compatible con el sistema en una determinada versión.

4. Click **Association** on the toolbox, then a use case, and then an actor that participates in the use case. Vincule los actores con sus casos de uso de la misma manera.

5. Structure the use cases with the **Include**, **Extend** and **Generalization** relationships. Para crear cada uno de estos vínculos, haga clic en la herramienta, luego en el caso de uso de origen y por último en el destino. See the following section titled [Structuring Use Cases](#Structuring).

6. Describa los casos de uso con más detalle. See the following section titled [Describing Use Cases in Detail](#Details).

7. Dibuje otros diagramas para hacer hincapié en diferentes subsistemas o grupos de casos de uso relacionados. Todos los diagramas de un proyecto de modelado son vistas del mismo modelo.

## <a name="Actors"></a> Drawing Actors and Use Cases
 El propósito principal de un diagrama de casos de uso es mostrar quién interactúa con el sistema y los principales objetivos que se logran con él.

- Create **Actors** to represent classes of people, organizations, other systems, software or devices that interact with your system or subsystem.

  - To learn how to draw actors and other elements, see [Edit UML models and diagrams](../modeling/edit-uml-models-and-diagrams.md).

  - En cada uno de los conjuntos de objetivos, identifique los actores en función de su tipo o rol, aun cuando las entidades o personas físicas sean las mismas. Por ejemplo, “Restaurante” y “Cliente” son actores diferentes, aunque un empleado del restaurante podría ocasionalmente actuar como cliente.

- Create **Use Cases** for each of the goals that each actor seeks to achieve with the system.

  - Asigne un nombre y una descripción para los casos de uso; use palabras que el actor pueda entender y no emplee términos relacionados con la implementación.

- Use **Associations** to link actors to use cases.

### <a name="inheritance-between-actors"></a>Herencia entre actores
 ![Use case diagram showing inheritance](../modeling/media/uml-ucguideinherit.png "UML_UCGuideInherit")

 You can draw a **Generalization** link between Actors. El actor especializado (“Cliente de club” en el ejemplo) hereda los casos de uso del actor general (“Cliente” en el ejemplo). La punta de flecha debe apuntar al actor más general, como “Cliente”. Cuando cree el vínculo, apunte primero al actor más especializado.

 El actor especializado puede tener otros casos de uso propios que no están disponibles para el resto de actores.

> [!CAUTION]
> No genere bucles de relaciones de generalización en los que, como resultado, un actor se generalice a sí mismo. Los bucles pueden producir errores.

### <a name="alternative-actor-icons"></a>Iconos de actores alternativos
 Puede usar iconos personalizados para representar a un actor en lugar del dibujo estándar. Por ejemplo, puede cambiar el icono para que tenga un aspecto similar a un dispositivo, restaurante, banco, etc.

##### <a name="to-change-the-appearance-of-an-actor"></a>Para cambiar la apariencia de un actor

1. Right-click the actor and then click **Properties**.

     Se muestra la ventana **Propiedades** .

2. Set the **Image Path** property to the location of an image file.

    - Puede usar cualquiera de los diversos formatos de imagen, como .bmp, .jpg y .gif.

    - Use un archivo que esté incluido en el control de código fuente de la solución o proyecto para que siga disponible cuando la solución se mueva o copie.

3. Para replicar esta apariencia en otros diagramas de casos de uso, copie al actor y péguelo en otro diagrama.

    - El cambio de imagen solo se aplica a la vista de un diagrama determinado, pero no al elemento del modelo subyacente. Si arrastra el actor desde el Explorador de modelos UML a otro diagrama, aparecerá como el dibujo estándar.

### <a name="multiplicities-between-actors-and-use-cases"></a>Multiplicidades entre actores y casos de uso
 The association between an actor and a use case can show a *multiplicity* at each end.

 ![Use case one to one with actor](../modeling/media/uml-ucguidemulti1.png "UML_UCGuideMulti1")

> [!NOTE]
> The multiplicities of an association on a use case diagram are hidden if they are both **1**.

 By default, each multiplicity is **1**. En una interpretación estricta del modelo, una multiplicidad de 1 significa que, por ejemplo, solo un cliente está implicado en el pedido de comida y que cada cliente pide exclusivamente un menú cada vez.

 Estas multiplicidades se pueden cambiar.

 Por ejemplo:

 ![Use case showing many to many multiplicity](../modeling/media/uml-ucguidemulti2.png "UML_UCGuideMulti2")

- To state that several actors of the same class can take part in a single occurrence of a use case, set the multiplicity at the actor end of the association to **1..\*** .

   En la ilustración, uno o varios restaurantes pueden participar en la elaboración del mismo pedido de menú.

- To show that each actor can participate at the same time in several occurrences of a use case, set the multiplicity at the use case end of the association to **\*** .

   En la ilustración, cada restaurante puede trabajar en la realización de más de un pedido a la vez.

##### <a name="to-set-multiplicities-on-an-association"></a>Para establecer las multiplicidades de una asociación

1. Right-click the association and then click **Properties**.

2. Expand either **First Role** or **Second Role**.

    *Role* means the element at one end of the association.

3. Elija en la lista uno de los valores siguientes para la propiedad de multiplicidad:

   - **1** to state that exactly one instance of this role participates in each link.

   - **1..\*** to state that one or more instance of this role participate in each link.

   - **0..1** to state that participation is optional.

   - **\*** to state that zero or more instances of this role participate in the link.

> [!NOTE]
> Muchos equipos no incluyen información de multiplicidad en los diagramas de casos de uso, dejando las multiplicidades con el valor predeterminado de 1. En su lugar, proporcionan la información en descripciones independientes de los casos de uso. En este caso, se ocultarán todas las multiplicidades de los diagramas de casos de uso.

### <a name="using-an-actor-or-use-case-on-multiple-diagrams"></a>Usar un actor o un caso de uso en varios diagramas
 Puede mostrar los mismos actores y casos de uso en varios diagramas. Por ejemplo:

- Los distintos casos de uso en los que está involucrado un actor se pueden describir en diagramas diferentes.

- Se puede usar un diagrama para mostrar los actores y subsistemas a los que un caso de uso está asociado y usar otro diagrama para mostrar cómo se estructura el caso de uso con la inclusión y ampliación de casos de uso.

##### <a name="to-show-the-same-actor-or-use-case-on-different-diagrams"></a>Para mostrar el mismo actor o caso de uso en diagramas diferentes

1. Crear el actor o el caso de uso en un diagrama.

2. Cree otro diagrama de casos de uso.

3. Drag an actor or use case off **Model Explorer** onto the new diagram.

    > [!NOTE]
    > Si en el nuevo diagrama se coloca un actor y un caso de uso que ya están asociados, la asociación entre ellos aparecerá automáticamente en el nuevo diagrama.

## <a name="Details"></a> Describing use cases in detail
 Un caso de uso representa:

- A goal of an actor in using the system, such as **Buy a Meal**; and

- One or more *scenarios*, that is, sequences of steps performed in pursuing the goal, such as: {**Order Meal, Pay, Deliver**}. In addition to success scenarios, there might be several exception or failure scenarios, such as **Credit Card Rejected**.

  Un caso de uso se puede describir con diferentes niveles de detalle. En una fase inicial del diseño, basta con indicar el nombre en el diagrama de casos de uso.  Posteriormente, se pueden incluir descripciones más detalladas de los escenarios.

  En Visual Studio Ultimate, un caso de uso puede describirse de varias maneras, que pueden usarse por separado o de forma conjunta:

- Puede vincular el caso de uso a otro diagrama o diagramas del proyecto.

  - Un diagrama de actividades ayuda a explicar un proceso más complejo que presenta bucles, bifurcaciones y subprocesos paralelos. También puede mostrar el flujo de datos entre elementos del proceso. For more information, see [UML Activity Diagrams: Guidelines](../modeling/uml-activity-diagrams-guidelines.md).

  - Un diagrama de secuencia ayuda a explicar una serie compleja de interacciones entre diferentes actores. También se puede usar para mostrar la respuesta del sistema ante cada caso de uso. For more information, see [UML Sequence Diagrams: Guidelines](../modeling/uml-sequence-diagrams-guidelines.md).

- Vincule el caso de uso a una página, sección o párrafo de OneNote que describa el caso de uso en detalle.

- Vincule el caso de uso a un documento de Word en el que use texto, capturas de pantalla, etc. para describir los escenarios del caso de uso. For more information, see [Model user requirements](../modeling/model-user-requirements.md).

#### <a name="to-link-a-use-case-to-a-diagram-or-file-in-the-same-solution"></a>Para vincular un caso de uso a un diagrama o a un archivo en la misma solución

1. Dibuje un diagrama, por ejemplo un diagrama de secuencia o de actividades, para mostrar un escenario del caso de uso.

2. Vuelva al diagrama de casos de uso.

3. Arrastre el diagrama o el archivo desde el Explorador de soluciones a una zona vacía del diagrama de casos de uso.

4. Connect from the artifact to the use case using a **Dependency**.

#### <a name="to-link-to-a-solution-file-such-as-a-word-document-or-powerpoint-presentation"></a>Para vincular a un archivo de solución, por ejemplo a un documento de Word o a una presentación de PowerPoint

1. Cree un documento que use texto, capturas de pantalla, etc. para describir el escenario del caso de uso.

2. Agregue el documento a la solución.

    1. Mueva el documento de Word a la misma carpeta de Windows que la solución.

    2. In Solution Explorer, right-click the solution, point to **Add**, and then click **Existing Item**.

    3. Navigate to the Word document and click **Add**.

         El documento de Word aparece en una carpeta de la solución en el Explorador de soluciones.

3. Arrastre el documento de Word desde el Explorador de soluciones a una parte en blanco del diagrama de casos de uso.

     Aparece un nuevo artefacto.

4. Connect from the artifact to the use case using a **Dependency**.

#### <a name="to-link-to-a-shared-document-onenote-element-or-web-page"></a>Para vincular un documento compartido, elemento de OneNote o página web

1. Obtenga la dirección URL del elemento compartido. This can be, for example, a network file path beginning '\\\\', or a web page or Sharepoint URL beginning 'http://', or a link to a OneNote section, page, or paragraph beginning 'onenote:'.

2. In the Toolbox, click **Artifact** and then click in the use case diagram.

3. With the new artifact selected, type or paste the URL into the **Hyperlink** property.

> [!NOTE]
> Haga doble clic en un artefacto para abrir el diagrama o documento al que está vinculado.

### <a name="linking-use-cases-to-work-items"></a>Vincular casos de uso a elementos de trabajo
 If your project uses [!INCLUDE[vstsTfsRosarioLong](../includes/vststfsrosariolong-md.md)] and you have [!INCLUDE[esprtfc](../includes/esprtfc-md.md)], you can link each use case to a work item in [!INCLUDE[esprfound](../includes/esprfound-md.md)]. To learn how to make these links, see [Link model elements and work items](../modeling/link-model-elements-and-work-items.md).

 Esto le permite:

- Describir el caso de uso en el elemento de trabajo vinculado. En concreto, si en el proyecto usa la plantilla de procesos formales de Visual Studio, puede establecer vínculos con un elemento de trabajo de casos de uso. Este tipo de elemento de trabajo proporciona campos para describir los objetivos y escenarios del caso de uso.

- Vincular casos de prueba al caso de uso para obtener informes sobre hasta qué punto el código que se está desarrollando implementa el caso de uso.

- Vincular tareas al caso de uso para que pueda hacer un seguimiento del progreso de desarrollo.

## <a name="Structuring"></a> Structuring Use Cases
 Es conveniente que intente describir el comportamiento del sistema con solo unos pocos casos de uso principales. En cada caso de uso grande se define un objetivo principal que un actor logra, como comprar un producto o, desde el punto de vista del proveedor, ofrecer productos para su venta.

 Una vez que haya presentado estos objetivos con claridad, puede proporcionar más detalles sobre cómo se consigue cada objetivo y sobre las variaciones de los objetivos básicos.

 Evite detallar en demasía los casos de uso. Los casos de uso hacen referencia a la experiencia de los usuarios en su sistema y no a sus mecanismos internos. Además, normalmente le resultará más eficaz crear versiones de trabajo del código en lugar de invertir tiempo en estructurar casos de uso con mucho detalle.

 Puede usar un diagrama de casos de uso para resumir las relaciones entre los casos de uso principales y los casos de uso más detallados. En las secciones siguientes se describe cómo:

- [Showing the details of a use case with Include](#Include)

- [Sharing goals with Generalization](#Inheritance)

- [Separating out variant cases with Extend](#Extend)

### <a name="Include"></a> Showing the details of a use case with Include
 Use an **Include** relation to show that one use case describes some of the detail of another. In the illustration, **Order a Meal** includes **Pay**, **Choose Menu**, and **Choose Menu Item**. Cada uno de los casos de uso incluidos y más detallados constituye un paso que probablemente el actor o actores tendrán que llevar a cabo para conseguir el objetivo global del caso de uso incluyente. La flecha debe apuntar al caso de uso incluido más detallado.

> [!CAUTION]
> No cree bucles de relaciones de inclusión en los que un caso de uso se incluya a sí mismo. Los bucles pueden producir errores.

 Los casos de uso incluidos se pueden compartir. In the example, the **Order a Meal** and **Subscribe to Reviews** use cases both include **Pay**.

 ![Use cases decomposed with include](../modeling/media/uml-ucguideinclude.png "UML_UCGuideInclude")

 El objetivo y los escenarios de un caso de uso incluido deben tener sentido por sí mismos, de modo que puedan incluirse en casos de uso que se diseñen posteriormente.

 La descomposición de los casos de uso en elementos incluyentes y elementos incluidos resulta útil para lograr los siguientes objetivos:

- Estructurar las descripciones del caso de uso en diferentes niveles de detalle.

- Evitar repetir escenarios compartidos en distintos casos de uso.

#### <a name="Steps"></a> Defining the order of the detailed steps
 En el diagrama de casos de uso no aparece ninguna información sobre el orden en que deben realizarse los pasos más detallados, ni sobre si son siempre todos necesarios.

 To make the order of the steps clear, you can use an **Artifact** to attach a separate document to the including use case. En el ejemplo siguiente, se muestra un diagrama de actividades asociado al caso de uso “Pedir un menú”. Si lo desea, también puede usar un documento de texto que contenga una lista de pasos o una secuencia de capturas de pantalla. For more information, see [Describing Use Cases in Detail](#Details).

 Tenga en cuenta estas convenciones de nomenclatura cuando use un diagrama de actividades:

- El nombre de la actividad global es el mismo que el caso de uso incluyente.

- Las acciones del diagrama de actividades tienen los mismos nombres que los casos de uso incluidos.

  For more information, see [UML Activity Diagrams: Guidelines](../modeling/uml-activity-diagrams-guidelines.md).

  ![Use case steps shown in linked activity diagram](../modeling/media/uml-ucguidesteps.png "UML_UCGuideSteps")

### <a name="Inheritance"></a> Sharing goals with Generalization
 Use a Generalization relation to show that a *specialized* use case is a particular way to achieve the goals expressed by another *general* use case. La punta de flecha abierta debe apuntar al caso de uso más general.

 ![Use cases showing the generalization relation](../modeling/media/uml-ucguidegeneral.png "UML_UCGuideGeneral")

 For example, **Pay** generalizes **Pay by Credit Card** and **Pay by Cash**.

> [!CAUTION]
> No genere bucles de relaciones de generalización en los que, como resultado, un actor se generalice a sí mismo. Los bucles pueden producir errores.

 Los casos de uso especializados pueden ayudarle a representar mecanismos distintos a través de los cuales el sistema puede conseguir el mismo objetivo.

 Se supone que los casos de uso especializados heredan los objetivos y los actores del caso de uso general. El caso de uso general no tiene que tener escenarios propios; en sus especializaciones se describen diferentes mecanismos para conseguir los objetivos.

##### <a name="to-refactor-common-goals-from-two-or-more-use-cases"></a>Para refactorizar los objetivos comunes de dos o más casos de uso

1. Cree el nuevo caso de uso general y asígnele un nombre.

2. Create a **Generalization** relation with the large arrow pointing at the new general use case.

    1. Click **Generalization** in the toolbox.

    2. Click a specialized use case (**Pay by Credit Card** in the example).

    3. Click the general use case (**Pay** in the example).

3. Si ha descrito los objetivos de los casos de uso especializados, transfiera las partes comunes a la descripción del caso de uso general.

4. Los actores que se comparten entre los casos de uso especializados pueden transferirse al caso de uso general.

### <a name="Extend"></a> Separating variant cases with Extend
 Use un vínculo de extensión para mostrar que, en determinadas circunstancias, un caso de uso puede agregar funcionalidad a otro caso de uso. La flecha debe apuntar al caso de uso principal extendido.

 ![One use case extending another](../modeling/media/uml-ucguideextend.png "UML_UCGuideExtend")

> [!CAUTION]
> No genere bucles de relaciones de extensión en los que, como resultado, un actor se generalice a sí mismo. Los bucles pueden producir errores.

 For example, the **Login** use case of a typical Web site can include **Register New User** - but only when the user does not already have an account.

##### <a name="to-separate-a-use-case-into-main-and-extending-parts"></a>Para descomponer un caso de uso en elementos principales y elementos de extensión

1. Cree el nuevo caso de uso de extensión y asígnele un nombre.

2. Create an **Extend** relation with the arrow pointing at the extended use case.

   1. Click **Extend** in the toolbox.

   2. Click the extending use case (**Register New User** in the example).

   3. Click the extended use case (**Login** in the example).

       > [!NOTE]
       > Evite crear un bucle de relaciones de extensión en el diagrama. No es correcto que un caso de uso sea una extensión de sí mismo.

3. Si ya ha creado los escenarios del caso de uso extendido, transfiera los pasos pertinentes al escenario de la extensión.

4. The description of the extension (**Register New User** in the example) should include details of where in the main use case scenarios it will occur, and under what circumstances. Debe concebirse como una modificación de la descripción del caso principal.

   El caso de uso de extensión representa los pasos del escenario que, de otro modo, formarían parte de los escenarios del caso de uso principal. El escenario y el objetivo de la extensión siempre se interpretarán en el contexto del caso de uso principal y, por tanto, no es necesario que resulten útiles por separado.

   Descomponer las extensiones puede resultar útil para describir estas situaciones:

- Hay actores adicionales que solamente están implicados en el caso de uso de extensión. Por ejemplo, es necesario que un administrador apruebe el registro de un cliente en el sitio web.

- Un subsistema independiente se ocupará del caso de uso de extensión.

- Esta extensión tan solo estará disponible en versiones específicas del sistema. Puede mostrar cada versión como un subsistema independiente en el diagrama de casos de uso.

## <a name="Subsystems"></a> Using Subsystem Boundaries
 Use un límite de subsistema para mostrar qué casos de uso están dentro del ámbito del sistema.

#### <a name="to-draw-a-subsystem-boundary"></a>Para dibujar un límite de subsistema

1. In the toolbox, click **Subsystem**, then click the diagram.

    Un subsistema aparece en el diagrama.

2. Arrastre las esquinas del subsistema para ajustar su tamaño.

3. Arrastre los casos de uso existentes dentro o fuera del subsistema hasta ajustar su contenido.

   \- o -

   To create a new use case directly in a subsystem, click **Use Case** in the toolbox, then click inside the subsystem.

> [!NOTE]
> The **Subjects** property of a use case indicates what subsystem it is contained within.

### <a name="use-cases-outside-the-system-scope"></a>Casos de uso fuera del ámbito del sistema
 Normalmente, resulta útil incluir en el diagrama casos de uso que forman parte del negocio pero que no tienen relación con el sistema que se está desarrollando. Esto ayuda a los desarrolladores a entender el contexto de su trabajo. Por ejemplo, “Entregar menú” podría presentarse como un caso de uso en el que están implicados los actores “Restaurante” y “Cliente”, pero podría quedar fuera de la responsabilidad del sitio web de pedidos de menús.

### <a name="multiple-subsystems"></a>Varios subsistemas
 Puede crear diversos límites de subsistema para representar el modo en que los distintos componentes del sistema se ocupan de los diferentes casos de uso. For example, **Add Restaurant Appraisal** may be dealt with on a separate forum Web site. Recuerde que un diagrama de casos de uso debe ocuparse de aquello que es visible para el usuario. Si desea describir la división interna del trabajo en el sistema, considere la posibilidad de usar un diagrama de componentes.

### <a name="system-versions"></a>Versiones del sistema
 Puede usar diferentes límites de subsistema para mostrar distintas versiones del sistema. Por ejemplo, el caso de uso “Pagar” podría estar incluido en la versión 2 del sitio web, pero no en la versión 1. Esto significa que el sistema ayuda a los clientes a realizar sus pedidos. Sin embargo, los clientes tienen que pagar al restaurante directamente.

 Use **Dependency** relations to link subsystems representing different versions or variants.

 ![Subsystems show different versions of a system](../modeling/media/uml-ucguidesystem.png "UML_UCGuideSystem")

## <a name="see-also"></a>Vea también
 [Model user requirements](../modeling/model-user-requirements.md) [UML Sequence Diagrams: Guidelines](../modeling/uml-sequence-diagrams-guidelines.md) [Edit UML models and diagrams](../modeling/edit-uml-models-and-diagrams.md) [UML Use Case Diagrams: Reference](../modeling/uml-use-case-diagrams-reference.md) [UML Class Diagrams: Reference](../modeling/uml-class-diagrams-reference.md) [UML Component Diagrams: Reference](../modeling/uml-component-diagrams-reference.md) [UML Activity Diagrams: Guidelines](../modeling/uml-activity-diagrams-guidelines.md) [Video: Organizing Features into Use Cases](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-2-organizing-features-into-use-cases)
