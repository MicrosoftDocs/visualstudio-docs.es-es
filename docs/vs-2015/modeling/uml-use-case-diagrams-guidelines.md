---
title: 'Diagramas de casos de uso de UML: instrucciones | Microsoft Docs'
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

En Visual Studio, puede dibujar un *Diagrama de casos de uso* para resumir quién usa la aplicación o el sistema y qué pueden hacer con él. Para crear un diagrama de casos de uso de UML, en el menú **arquitectura** , haga clic en **nuevo diagrama de UML o de capas**.

 Para ver una demostración en vídeo, vea [organizar características en casos de uso](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-2-organizing-features-into-use-cases).

 Para ver qué versiones de Visual Studio admiten esta característica, vea [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Con la ayuda de un diagrama de casos de uso, puede analizar y comunicar:

- Los escenarios en los que el sistema o aplicación interactúa con personas, organizaciones o sistemas externos.

- Los objetivos que el sistema o aplicación contribuye a lograr.

- El ámbito del sistema.

  En un diagrama de casos de uso no se muestran los casos de uso en detalle; solamente se resumen algunas de las relaciones entre los casos de uso, los actores y los sistemas. En concreto, en el diagrama no se muestra el orden en que se llevan a cabo los pasos para lograr los objetivos de cada caso de uso. Esos detalles pueden describirse en otros diagramas y documentos, que pueden vincularse a cada caso de uso. Para obtener más información, vea [Descripción de los casos de uso en](#Details) este tema.

  En las descripciones que se proporcionen de los casos de uso se usarán diversos términos relacionados con el dominio en el que trabaja el sistema, como Ventas, Menú, Cliente, etc. Es importante definir de manera clara estos términos y sus relaciones y, para ello, puede resultar útil un diagrama de clases de UML. Para obtener más información, vea [diagramas de clases de UML: instrucciones](../modeling/uml-class-diagrams-guidelines.md).

  Los casos de uso solamente se usan para los requisitos funcionales de un sistema. Otros requisitos, como las reglas de negocio, los requisitos de calidad del servicio y las restricciones de implementación, deben representarse por separado. La arquitectura y los detalles internos también deben describirse por separado. Para obtener más información acerca de cómo definir los requisitos de usuario, vea [requisitos de usuario de modelo](../modeling/model-user-requirements.md).

  Los ejemplos que se usan en este tema están relacionados con un sitio web en el que los clientes pueden hacer pedidos de comida de restaurantes locales.

  ![Elementos de un diagrama de casos de uso](../modeling/media/uml-ucovactor.png "UML_UCOvActor")

- Un *actor* (1) es una clase de persona, organización, dispositivo o componente de software externo que interactúa con el sistema. Los actores de ejemplo son **cliente**, **restaurante**, **sensor de temperatura**, **autorizador de tarjeta de crédito.**

- Un *caso de uso* (2) representa las acciones realizadas por uno o más actores en la realización de un objetivo determinado. Los casos de uso de ejemplo son el **pedido de comida**, el **menú actualizar**y el **proceso de pago**.

   En un diagrama de casos de uso, casos de uso están asociados (3) a los actores que los realizan.

- Su *sistema (4)* es todo lo que está desarrollando. Puede ser un pequeño componente de software cuyos actores simplemente son otros componentes de software; puede ser una aplicación completa; o puede ser un gran conjunto de aplicaciones distribuidas que se implementan en muchos equipos y dispositivos. Los subsistemas de ejemplo son un **sitio web de pedidos de comidas**, una **empresa de entrega de comidas**, la **versión 2 del sitio web**.

   En un diagrama de casos de uso pueden mostrarse los casos de uso que el sistema o sus subsistemas admiten.

## <a name="BasicSteps"></a>Pasos básicos para dibujar diagramas de casos de uso

> [!NOTE]
> En [Editar modelos y diagramas UML,](../modeling/edit-uml-models-and-diagrams.md)se describen los pasos detallados para crear cualquiera de los diagramas de modelado.

#### <a name="to-create-a-new-use-case-diagram"></a>Para crear un nuevo diagrama de casos de uso

1. En el menú **arquitectura** , haga clic en **nuevo diagrama de UML o de capas**.

2. En **plantillas**, haga clic en **Diagrama de casos UMLUse**.

3. Especifique un nombre para el diagrama.

4. En **Agregar a proyecto de modelado**, seleccione un proyecto de modelado existente en la solución o **cree un nuevo proyecto de modelado**y, a continuación, haga clic en **Aceptar**.

#### <a name="to-draw-a-use-case-diagram"></a>Para dibujar un diagrama de casos de uso

1. Arrastre los límites del **subsistema** desde el cuadro de herramientas hasta el diagrama para representar el sistema completo o sus componentes principales.

    - Si no desea describir los casos de uso que el sistema o sus componentes admiten, puede dibujar un diagrama de casos de uso sin límites de sistema.

    - Si es necesario, arrastre la esquina de un sistema para hacerlo más grande.

    - Cambie su nombre como corresponda.

2. Arrastre **actores** desde el cuadro de herramientas hasta el diagrama (colóquelos fuera de los límites del sistema).

    - Los actores representan las clases de usuarios, organizaciones y sistemas externos que interactúan con el sistema.

    - Cámbieles el nombre. Por ejemplo: **cliente, restaurante, Agencia de tarjetas de crédito.**

3. Arrastre los **casos de uso** del cuadro de herramientas a los sistemas adecuados.

    - Los casos de uso representan las actividades que los actores realizan con la ayuda del sistema.

    - Asígneles títulos que los propios actores puedan reconocer. No use títulos que tengan relación con el código. Por ejemplo: **pedido de comida, pago por comida, entrega de comida**.

    - Comience con las transacciones principales como el **pedido de comida**, y permanezca hasta más interacciones más pequeñas, como **Seleccionar elemento de menú**.

    - Sitúe cada caso de uso en el sistema o el subsistema principal compatible (omita los elementos de fachada o los componentes que solamente están implicados en la conexión con el usuario).

    - Puede dibujar un caso de uso fuera del límite de sistema para mostrar que dicho caso de uso no es compatible con el sistema en una determinada versión.

4. Haga clic en **Asociación** en el cuadro de herramientas, en un caso de uso y, a continuación, en un actor que participa en el caso de uso. Vincule los actores con sus casos de uso de la misma manera.

5. Estructure los casos de uso con las relaciones de **inclusión**, **extensión** y **generalización** . Para crear cada uno de estos vínculos, haga clic en la herramienta, luego en el caso de uso de origen y por último en el destino. Vea la sección siguiente titulada [estructurar casos de uso](#Structuring).

6. Describa los casos de uso con más detalle. Vea la sección siguiente titulada [Descripción de los casos de uso en detalle](#Details).

7. Dibuje otros diagramas para hacer hincapié en diferentes subsistemas o grupos de casos de uso relacionados. Todos los diagramas de un proyecto de modelado son vistas del mismo modelo.

## <a name="Actors"></a>Dibujar actores y casos de uso
 El propósito principal de un diagrama de casos de uso es mostrar quién interactúa con el sistema y los principales objetivos que se logran con él.

- Cree **actores** para representar clases de personas, organizaciones, otros sistemas, software o dispositivos que interactúen con el sistema o el subsistema.

  - Para obtener información sobre cómo dibujar actores y otros elementos, vea [Editar modelos y diagramas UML](../modeling/edit-uml-models-and-diagrams.md).

  - En cada uno de los conjuntos de objetivos, identifique los actores en función de su tipo o rol, aun cuando las entidades o personas físicas sean las mismas. Por ejemplo, “Restaurante” y “Cliente” son actores diferentes, aunque un empleado del restaurante podría ocasionalmente actuar como cliente.

- Cree **casos de uso** para cada uno de los objetivos que cada actor pretenda lograr con el sistema.

  - Asigne un nombre y una descripción para los casos de uso; use palabras que el actor pueda entender y no emplee términos relacionados con la implementación.

- Use **asociaciones** para vincular actores a casos de uso.

### <a name="inheritance-between-actors"></a>Herencia entre actores
 ![Diagrama de casos de uso que muestra herencia](../modeling/media/uml-ucguideinherit.png "UML_UCGuideInherit")

 Puede dibujar un vínculo de **generalización** entre actores. El actor especializado (“Cliente de club” en el ejemplo) hereda los casos de uso del actor general (“Cliente” en el ejemplo). La punta de flecha debe apuntar al actor más general, como “Cliente”. Cuando cree el vínculo, apunte primero al actor más especializado.

 El actor especializado puede tener otros casos de uso propios que no están disponibles para el resto de actores.

> [!CAUTION]
> No genere bucles de relaciones de generalización en los que, como resultado, un actor se generalice a sí mismo. Los bucles pueden producir errores.

### <a name="alternative-actor-icons"></a>Iconos de actores alternativos
 Puede usar iconos personalizados para representar a un actor en lugar del dibujo estándar. Por ejemplo, puede cambiar el icono para que tenga un aspecto similar a un dispositivo, restaurante, banco, etc.

##### <a name="to-change-the-appearance-of-an-actor"></a>Para cambiar la apariencia de un actor

1. Haga clic con el botón secundario en el actor y después haga clic en **propiedades**.

     Aparece la ventana **Propiedades**.

2. Establezca la propiedad **ruta de acceso** de la imagen en la ubicación de un archivo de imagen.

    - Puede usar cualquiera de los diversos formatos de imagen, como .bmp, .jpg y .gif.

    - Use un archivo que esté incluido en el control de código fuente de la solución o proyecto para que siga disponible cuando la solución se mueva o copie.

3. Para replicar esta apariencia en otros diagramas de casos de uso, copie al actor y péguelo en otro diagrama.

    - El cambio de imagen solo se aplica a la vista de un diagrama determinado, pero no al elemento del modelo subyacente. Si arrastra el actor desde el Explorador de modelos UML a otro diagrama, aparecerá como el dibujo estándar.

### <a name="multiplicities-between-actors-and-use-cases"></a>Multiplicidades entre actores y casos de uso
 La asociación entre un actor y un caso de uso puede mostrar una *multiplicidad* en cada extremo.

 ![Caso de uso uno a uno con actor](../modeling/media/uml-ucguidemulti1.png "UML_UCGuideMulti1")

> [!NOTE]
> Las multiplicidades de una asociación en un diagrama de casos de uso están ocultas si ambos son **1**.

 De forma predeterminada, cada multiplicidad es **1**. En una interpretación estricta del modelo, una multiplicidad de 1 significa que, por ejemplo, solo un cliente está implicado en el pedido de comida y que cada cliente pide exclusivamente un menú cada vez.

 Estas multiplicidades se pueden cambiar.

 Por ejemplo:

 ![Caso de uso que muestra una multiplicidad de varios a varios](../modeling/media/uml-ucguidemulti2.png "UML_UCGuideMulti2")

- Para indicar que varios actores de la misma clase pueden participar en una única repetición de un caso de uso, establezca la multiplicidad en el extremo del actor de la asociación en **1..\*** .

   En la ilustración, uno o varios restaurantes pueden participar en la elaboración del mismo pedido de menú.

- Para mostrar que cada actor puede participar al mismo tiempo en varias repeticiones de un caso de uso, establezca la multiplicidad en el extremo de caso de uso de la asociación en **\*** .

   En la ilustración, cada restaurante puede trabajar en la realización de más de un pedido a la vez.

##### <a name="to-set-multiplicities-on-an-association"></a>Para establecer las multiplicidades de una asociación

1. Haga clic con el botón secundario en la asociación y, a continuación, haga clic en **propiedades**.

2. Expanda el **primer rol** o el **segundo rol**.

    *Role* significa el elemento situado en un extremo de la asociación.

3. Elija en la lista uno de los valores siguientes para la propiedad de multiplicidad:

   - **1** para indicar que exactamente una instancia de este rol participa en cada vínculo.

   - **1..\*** para indicar que una o más instancias de este rol participan en cada vínculo.

   - **0.. 1** para indicar que la participación es opcional.

   - **\*** para indicar que cero o más instancias de este rol participan en el vínculo.

> [!NOTE]
> Muchos equipos no incluyen información de multiplicidad en los diagramas de casos de uso, dejando las multiplicidades con el valor predeterminado de 1. En su lugar, proporcionan la información en descripciones independientes de los casos de uso. En este caso, se ocultarán todas las multiplicidades de los diagramas de casos de uso.

### <a name="using-an-actor-or-use-case-on-multiple-diagrams"></a>Usar un actor o un caso de uso en varios diagramas
 Puede mostrar los mismos actores y casos de uso en varios diagramas. Por ejemplo:

- Los distintos casos de uso en los que está involucrado un actor se pueden describir en diagramas diferentes.

- Se puede usar un diagrama para mostrar los actores y subsistemas a los que un caso de uso está asociado y usar otro diagrama para mostrar cómo se estructura el caso de uso con la inclusión y ampliación de casos de uso.

##### <a name="to-show-the-same-actor-or-use-case-on-different-diagrams"></a>Para mostrar el mismo actor o caso de uso en diagramas diferentes

1. Crear el actor o el caso de uso en un diagrama.

2. Cree otro diagrama de casos de uso.

3. Arrastre un actor o caso de uso en el **Explorador de modelos** al nuevo diagrama.

    > [!NOTE]
    > Si en el nuevo diagrama se coloca un actor y un caso de uso que ya están asociados, la asociación entre ellos aparecerá automáticamente en el nuevo diagrama.

## <a name="Details"></a>Describir los casos de uso en detalle
 Un caso de uso representa:

- Un objetivo de un actor en el uso del sistema, como **comprar una comida**; etc

- Uno o varios *escenarios*, es decir, secuencias de pasos que se llevan a cabo para alcanzar el objetivo, como: {**pedido de comida, pago, entrega**}. Además de los escenarios de éxito, puede haber varios escenarios de excepción o error, como la **tarjeta de crédito rechazada**.

  Un caso de uso se puede describir con diferentes niveles de detalle. En una fase inicial del diseño, basta con indicar el nombre en el diagrama de casos de uso.  Posteriormente, se pueden incluir descripciones más detalladas de los escenarios.

  En Visual Studio Ultimate, un caso de uso puede describirse de varias maneras, que pueden usarse por separado o de forma conjunta:

- Puede vincular el caso de uso a otro diagrama o diagramas del proyecto.

  - Un diagrama de actividades ayuda a explicar un proceso más complejo que presenta bucles, bifurcaciones y subprocesos paralelos. También puede mostrar el flujo de datos entre elementos del proceso. Para obtener más información, vea [diagramas de actividades UML: instrucciones](../modeling/uml-activity-diagrams-guidelines.md).

  - Un diagrama de secuencia ayuda a explicar una serie compleja de interacciones entre diferentes actores. También se puede usar para mostrar la respuesta del sistema ante cada caso de uso. Para obtener más información, vea [diagramas de secuencia UML: instrucciones](../modeling/uml-sequence-diagrams-guidelines.md).

- Vincule el caso de uso a una página, sección o párrafo de OneNote que describa el caso de uso en detalle.

- Vincule el caso de uso a un documento de Word en el que use texto, capturas de pantalla, etc. para describir los escenarios del caso de uso. Para obtener más información, vea [requisitos de usuario de modelo](../modeling/model-user-requirements.md).

#### <a name="to-link-a-use-case-to-a-diagram-or-file-in-the-same-solution"></a>Para vincular un caso de uso a un diagrama o a un archivo en la misma solución

1. Dibuje un diagrama, por ejemplo un diagrama de secuencia o de actividades, para mostrar un escenario del caso de uso.

2. Vuelva al diagrama de casos de uso.

3. Arrastre el diagrama o el archivo desde el Explorador de soluciones a una zona vacía del diagrama de casos de uso.

4. Conecte desde el artefacto al caso de uso mediante una **dependencia**.

#### <a name="to-link-to-a-solution-file-such-as-a-word-document-or-powerpoint-presentation"></a>Para vincular a un archivo de solución, por ejemplo a un documento de Word o a una presentación de PowerPoint

1. Cree un documento que use texto, capturas de pantalla, etc. para describir el escenario del caso de uso.

2. Agregue el documento a la solución.

    1. Mueva el documento de Word a la misma carpeta de Windows que la solución.

    2. En Explorador de soluciones, haga clic con el botón secundario en la solución, seleccione **Agregar**y, a continuación, haga clic en **elemento existente**.

    3. Navegue hasta el documento de Word y haga clic en **Agregar**.

         El documento de Word aparece en una carpeta de la solución en el Explorador de soluciones.

3. Arrastre el documento de Word desde el Explorador de soluciones a una parte en blanco del diagrama de casos de uso.

     Aparece un nuevo artefacto.

4. Conecte desde el artefacto al caso de uso mediante una **dependencia**.

#### <a name="to-link-to-a-shared-document-onenote-element-or-web-page"></a>Para vincular un documento compartido, elemento de OneNote o página web

1. Obtenga la dirección URL del elemento compartido. Esto puede ser, por ejemplo, una ruta de acceso de archivo de red que empieza por '\\\\', o una página web o una dirección URL de SharePoint que empieza por ' http://', o un vínculo a una sección, página o párrafo de OneNote que empieza por ' OneNote: '.

2. En el cuadro de herramientas, haga clic en **artefacto** y, a continuación, haga clic en el diagrama de casos de uso.

3. Con el nuevo artefacto seleccionado, escriba o pegue la dirección URL en la propiedad de **hipervínculo** .

> [!NOTE]
> Haga doble clic en un artefacto para abrir el diagrama o documento al que está vinculado.

### <a name="linking-use-cases-to-work-items"></a>Vincular casos de uso a elementos de trabajo
 Si el proyecto usa [!INCLUDE[vstsTfsRosarioLong](../includes/vststfsrosariolong-md.md)] y tiene [!INCLUDE[esprtfc](../includes/esprtfc-md.md)], puede vincular cada caso de uso a un elemento de trabajo en [!INCLUDE[esprfound](../includes/esprfound-md.md)]. Para obtener información sobre cómo crear estos vínculos, vea [vincular elementos de modelo y elementos de trabajo](../modeling/link-model-elements-and-work-items.md).

 Esto le permite:

- Describir el caso de uso en el elemento de trabajo vinculado. En concreto, si en el proyecto usa la plantilla de procesos formales de Visual Studio, puede establecer vínculos con un elemento de trabajo de casos de uso. Este tipo de elemento de trabajo proporciona campos para describir los objetivos y escenarios del caso de uso.

- Vincular casos de prueba al caso de uso para obtener informes sobre hasta qué punto el código que se está desarrollando implementa el caso de uso.

- Vincular tareas al caso de uso para que pueda hacer un seguimiento del progreso de desarrollo.

## <a name="Structuring"></a>Estructurar casos de uso
 Es conveniente que intente describir el comportamiento del sistema con solo unos pocos casos de uso principales. En cada caso de uso grande se define un objetivo principal que un actor logra, como comprar un producto o, desde el punto de vista del proveedor, ofrecer productos para su venta.

 Una vez que haya presentado estos objetivos con claridad, puede proporcionar más detalles sobre cómo se consigue cada objetivo y sobre las variaciones de los objetivos básicos.

 Evite detallar en demasía los casos de uso. Los casos de uso hacen referencia a la experiencia de los usuarios en su sistema y no a sus mecanismos internos. Además, normalmente le resultará más eficaz crear versiones de trabajo del código en lugar de invertir tiempo en estructurar casos de uso con mucho detalle.

 Puede usar un diagrama de casos de uso para resumir las relaciones entre los casos de uso principales y los casos de uso más detallados. En las secciones siguientes se describe cómo:

- [Mostrar los detalles de un caso de uso con include](#Include)

- [Uso compartido de objetivos con generalización](#Inheritance)

- [Separar casos variantes con Extend](#Extend)

### <a name="Include"></a>Mostrar los detalles de un caso de uso con include
 Use una relación de **inclusión** para mostrar que un caso de uso describe algunos de los detalles de otro. En la ilustración, **pedir una comida** incluye **pago**, **Elegir menú**y **elegir elemento de menú**. Cada uno de los casos de uso incluidos y más detallados constituye un paso que probablemente el actor o actores tendrán que llevar a cabo para conseguir el objetivo global del caso de uso incluyente. La flecha debe apuntar al caso de uso incluido más detallado.

> [!CAUTION]
> No cree bucles de relaciones de inclusión en los que un caso de uso se incluya a sí mismo. Los bucles pueden producir errores.

 Los casos de uso incluidos se pueden compartir. En el ejemplo, los casos de uso **pedir una comida** y **suscribirse a las revisiones** incluyen el **pago**.

 ![Casos de uso que se descomponen con include](../modeling/media/uml-ucguideinclude.png "UML_UCGuideInclude")

 El objetivo y los escenarios de un caso de uso incluido deben tener sentido por sí mismos, de modo que puedan incluirse en casos de uso que se diseñen posteriormente.

 La descomposición de los casos de uso en elementos incluyentes y elementos incluidos resulta útil para lograr los siguientes objetivos:

- Estructurar las descripciones del caso de uso en diferentes niveles de detalle.

- Evitar repetir escenarios compartidos en distintos casos de uso.

#### <a name="Steps"></a>Definir el orden de los pasos detallados
 En el diagrama de casos de uso no aparece ninguna información sobre el orden en que deben realizarse los pasos más detallados, ni sobre si son siempre todos necesarios.

 Para que el orden de los pasos sea claro, puede usar un **artefacto** para adjuntar un documento independiente al caso de uso incluido. En el ejemplo siguiente, se muestra un diagrama de actividades asociado al caso de uso “Pedir un menú”. Si lo desea, también puede usar un documento de texto que contenga una lista de pasos o una secuencia de capturas de pantalla. Para obtener más información, consulte [Descripción de los casos de uso en detalle](#Details).

 Tenga en cuenta estas convenciones de nomenclatura cuando use un diagrama de actividades:

- El nombre de la actividad global es el mismo que el caso de uso incluyente.

- Las acciones del diagrama de actividades tienen los mismos nombres que los casos de uso incluidos.

  Para obtener más información, vea [diagramas de actividades UML: instrucciones](../modeling/uml-activity-diagrams-guidelines.md).

  ![Pasos de casos de uso mostrados en el diagrama de actividades vinculadas](../modeling/media/uml-ucguidesteps.png "UML_UCGuideSteps")

### <a name="Inheritance"></a>Uso compartido de objetivos con generalización
 Use una relación de generalización para mostrar que un caso de uso *especializado* es una manera determinada de lograr los objetivos que se expresan en otro caso de uso *General* . La punta de flecha abierta debe apuntar al caso de uso más general.

 ![Casos de uso que muestran la relación de generalización](../modeling/media/uml-ucguidegeneral.png "UML_UCGuideGeneral")

 Por ejemplo, el **pago** generaliza el **pago con tarjeta de crédito** y **paga por efectivo**.

> [!CAUTION]
> No genere bucles de relaciones de generalización en los que, como resultado, un actor se generalice a sí mismo. Los bucles pueden producir errores.

 Los casos de uso especializados pueden ayudarle a representar mecanismos distintos a través de los cuales el sistema puede conseguir el mismo objetivo.

 Se supone que los casos de uso especializados heredan los objetivos y los actores del caso de uso general. El caso de uso general no tiene que tener escenarios propios; en sus especializaciones se describen diferentes mecanismos para conseguir los objetivos.

##### <a name="to-refactor-common-goals-from-two-or-more-use-cases"></a>Para refactorizar los objetivos comunes de dos o más casos de uso

1. Cree el nuevo caso de uso general y asígnele un nombre.

2. Cree una relación de **generalización** con la flecha grande que apunta al nuevo caso de uso general.

    1. Haga clic en **generalización** en el cuadro de herramientas.

    2. Haga clic en un caso de uso especializado (**pague con la tarjeta de crédito** en el ejemplo).

    3. Haga clic en el caso de uso general (**pague** en el ejemplo).

3. Si ha descrito los objetivos de los casos de uso especializados, transfiera las partes comunes a la descripción del caso de uso general.

4. Los actores que se comparten entre los casos de uso especializados pueden transferirse al caso de uso general.

### <a name="Extend"></a>Separar casos de variante con Extend
 Use un vínculo de extensión para mostrar que, en determinadas circunstancias, un caso de uso puede agregar funcionalidad a otro caso de uso. La flecha debe apuntar al caso de uso principal extendido.

 ![Un caso de uso que extiende otro](../modeling/media/uml-ucguideextend.png "UML_UCGuideExtend")

> [!CAUTION]
> No genere bucles de relaciones de extensión en los que, como resultado, un actor se generalice a sí mismo. Los bucles pueden producir errores.

 Por ejemplo, el caso de uso de **Inicio de sesión** de un sitio web típico puede incluir **registrar nuevo usuario** , pero solo cuando el usuario todavía no tiene una cuenta.

##### <a name="to-separate-a-use-case-into-main-and-extending-parts"></a>Para descomponer un caso de uso en elementos principales y elementos de extensión

1. Cree el nuevo caso de uso de extensión y asígnele un nombre.

2. Cree una relación de **extensión** con la flecha que apunta al caso de uso extendido.

   1. En el cuadro de herramientas, haga clic en **extender** .

   2. Haga clic en el caso de uso de extensión (**registrar nuevo usuario** en el ejemplo).

   3. Haga clic en el caso de uso extendido (**Inicio de sesión** en el ejemplo).

       > [!NOTE]
       > Evite crear un bucle de relaciones de extensión en el diagrama. No es correcto que un caso de uso sea una extensión de sí mismo.

3. Si ya ha creado los escenarios del caso de uso extendido, transfiera los pasos pertinentes al escenario de la extensión.

4. La descripción de la extensión (**registrar un nuevo usuario** en el ejemplo) debe incluir detalles sobre dónde se producirán los escenarios de casos de uso principales y en qué circunstancias. Debe concebirse como una modificación de la descripción del caso principal.

   El caso de uso de extensión representa los pasos del escenario que, de otro modo, formarían parte de los escenarios del caso de uso principal. El escenario y el objetivo de la extensión siempre se interpretarán en el contexto del caso de uso principal y, por tanto, no es necesario que resulten útiles por separado.

   Descomponer las extensiones puede resultar útil para describir estas situaciones:

- Hay actores adicionales que solamente están implicados en el caso de uso de extensión. Por ejemplo, es necesario que un administrador apruebe el registro de un cliente en el sitio web.

- Un subsistema independiente se ocupará del caso de uso de extensión.

- Esta extensión tan solo estará disponible en versiones específicas del sistema. Puede mostrar cada versión como un subsistema independiente en el diagrama de casos de uso.

## <a name="Subsystems"></a>Usar límites de subsistema
 Use un límite de subsistema para mostrar qué casos de uso están dentro del ámbito del sistema.

#### <a name="to-draw-a-subsystem-boundary"></a>Para dibujar un límite de subsistema

1. En el cuadro de herramientas, haga clic en **subsistema**y, a continuación, haga clic en el diagrama.

    Un subsistema aparece en el diagrama.

2. Arrastre las esquinas del subsistema para ajustar su tamaño.

3. Arrastre los casos de uso existentes dentro o fuera del subsistema hasta ajustar su contenido.

   \- o -

   Para crear un nuevo caso de uso directamente en un subsistema, haga clic en **caso de uso** en el cuadro de herramientas y, a continuación, haga clic dentro del subsistema.

> [!NOTE]
> La propiedad **sujetos** de un caso de uso indica en qué subsistema está incluido.

### <a name="use-cases-outside-the-system-scope"></a>Casos de uso fuera del ámbito del sistema
 Normalmente, resulta útil incluir en el diagrama casos de uso que forman parte del negocio pero que no tienen relación con el sistema que se está desarrollando. Esto ayuda a los desarrolladores a entender el contexto de su trabajo. Por ejemplo, “Entregar menú” podría presentarse como un caso de uso en el que están implicados los actores “Restaurante” y “Cliente”, pero podría quedar fuera de la responsabilidad del sitio web de pedidos de menús.

### <a name="multiple-subsystems"></a>Varios subsistemas
 Puede crear diversos límites de subsistema para representar el modo en que los distintos componentes del sistema se ocupan de los diferentes casos de uso. Por ejemplo, **Agregar la valoración del restaurante** puede tratarse en un sitio web del foro independiente. Recuerde que un diagrama de casos de uso debe ocuparse de aquello que es visible para el usuario. Si desea describir la división interna del trabajo en el sistema, considere la posibilidad de usar un diagrama de componentes.

### <a name="system-versions"></a>Versiones del sistema
 Puede usar diferentes límites de subsistema para mostrar distintas versiones del sistema. Por ejemplo, el caso de uso “Pagar” podría estar incluido en la versión 2 del sitio web, pero no en la versión 1. Esto significa que el sistema ayuda a los clientes a realizar sus pedidos. Sin embargo, los clientes tienen que pagar al restaurante directamente.

 Usar relaciones de **dependencia** para vincular subsistemas que representan versiones o variantes diferentes.

 ![Los subsistemas muestran versiones diferentes de un sistema](../modeling/media/uml-ucguidesystem.png "UML_UCGuideSystem")

## <a name="see-also"></a>Vea también
 [Requisitos de usuario de modelo](../modeling/model-user-requirements.md) [diagramas de secuencia UML: instrucciones](../modeling/uml-sequence-diagrams-guidelines.md) [Editar modelos y diagramas UML](../modeling/edit-uml-models-and-diagrams.md) [diagramas de casos de uso de UML: referencia](../modeling/uml-use-case-diagrams-reference.md) [diagramas de clases de UML: referencia](../modeling/uml-class-diagrams-reference.md) diagramas de componentes de UML [: referencia](../modeling/uml-component-diagrams-reference.md) [diagramas de actividades UML: instrucciones](../modeling/uml-activity-diagrams-guidelines.md) [vídeo: organizar características en casos de uso](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-2-organizing-features-into-use-cases)
