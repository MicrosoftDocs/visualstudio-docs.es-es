---
title: 'Diagramas de secuencia UML: instrucciones | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.sequencediagram.linktosequencediagram
- vs.teamarch.logicalclassdiagram.createlifeline
- vs.teamarch.componentdiagram.createlifeline
helpviewer_keywords:
- diagrams - modeling, sequence
- sequence diagrams
- UML diagrams, sequence
- interactions, UML
- diagrams - modeling, UML sequence
- UML interactions
- UML, sequence diagrams
- UML sequence diagrams
- behaviors, UML
ms.assetid: 5990ef7c-ba60-4e20-a36d-e29c1fa6c8bb
caps.latest.revision: 55
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8c5906084fc7db96ddf304e8362bf7692dac62d5
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297147"
---
# <a name="uml-sequence-diagrams-guidelines"></a>Diagramas de secuencia UML: Instrucciones
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En Visual Studio, puede dibujar un *Diagrama de secuencia* para mostrar una interacción. Una interacción es una secuencia de mensajes entre instancias típicas de clases, componentes, subsistemas o actores.

 Los diagramas de secuencia de UML forman parte de un modelo UML y solo existen en los proyectos de modelado UML. Para crear un diagrama de secuencia UML, en el menú **arquitectura** , haga clic en **nuevo diagrama de UML o de capas**. Obtenga más información sobre [los elementos del diagrama de secuencia UML](../modeling/uml-sequence-diagrams-reference.md) o [diagramas de modelado UML](../modeling/edit-uml-models-and-diagrams.md) en general. Para ver una demostración en vídeo, consulte [esbozar interacciones mediante diagramas de secuencia (2010)](https://channel9.msdn.com/Blogs/clinted/UML-with-VS-2010-Part-7-Sketching-Interactions-with-Sequence-Diagrams).

 Para ver qué versiones de Visual Studio admiten esta característica, vea [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="in-this-topic"></a>En este tema
 [Usar diagramas de secuencia UML](#Using)

 [Pasos básicos para dibujar diagramas de secuencia](#BasicSteps)

 [Crear y usar diagramas de secuencia simples](#Simple)

 [Clases y lifelines](#ClassesAndLifelines)

 [Crear secuencias de interacción reutilizables](#Multiple)

 [Contraer grupos de línea de vida](#Collapse)

 [Describir estructuras de control con fragmentos](#Fragments)

## <a name="Using"></a>Usar diagramas de secuencia UML
 Puede usar diagramas de secuencia para una variedad de propósitos en distintos niveles de detalle del programa. Las ocasiones típicas para dibujar un diagrama de secuencia son las siguientes:

- Si tiene un diagrama de casos de uso que resuma los usuarios del sistema y sus objetivos, puede dibujar diagramas de secuencia para describir cómo interactúan los componentes principales del sistema para cumplir el objetivo de cada caso de uso. Para obtener más información, vea [diagramas de casos de uso de UML: instrucciones](../modeling/uml-use-case-diagrams-guidelines.md).

- Si ha identificado mensajes que llegan a una interfaz de un componente, puede dibujar diagramas de secuencia a fin de describir cómo interactúan los elementos internos del componente para lograr el resultado necesario para cada mensaje entrante. Para obtener más información, vea [diagramas de componentes de UML: instrucciones](../modeling/uml-component-diagrams-guidelines.md).

  El uso de diagramas de secuencia tiene algunas ventajas:

- Puede ver fácilmente cómo se distribuyen las tareas entre los componentes.

- Puede identificar patrones de interacción que dificultan la actualización de software.

## <a name="relationship-to-other-diagrams"></a>Relación con otros diagramas
 Puede usar diagramas de secuencia UML junto con otros diagramas de varias maneras.

#### <a name="lifelines-and-types"></a>Líneas de vida y tipos
 Las líneas de vida que dibuja en un diagrama de secuencia pueden representar instancias típicas de los componentes o clases en el sistema. Puede crear líneas de vida a partir de los tipos y tipos a partir de las líneas de vida, así como mostrar los tipos en diagramas de clases UML y diagramas de componentes UML. Para obtener más información, vea [clases y lifelines](#ClassesAndLifelines).

#### <a name="parameter-types"></a>Tipos de parámetros
 También puede describir en un diagrama de clases UML los tipos de parámetros y valores devueltos que se usaron en los mensajes enviados entre las líneas de vida.

#### <a name="use-case-details"></a>Detalles del caso de uso
 Un caso de uso representa el objetivo de un usuario, junto con una secuencia de pasos para lograr el objetivo. La secuencia de pasos se puede describir de varias maneras. Una opción es dibujar un diagrama de secuencia que muestra las interacciones entre los usuarios y los principales componentes del sistema. Para obtener más información, vea [diagramas de casos de uso de UML: instrucciones](../modeling/uml-use-case-diagrams-guidelines.md).

## <a name="BasicSteps"></a>Pasos básicos para dibujar diagramas de secuencia
 Para obtener una lista completa de los elementos de los diagramas de secuencia, vea [diagramas de secuencia UML: referencia](../modeling/uml-sequence-diagrams-reference.md).

> [!NOTE]
> En [Editar modelos y diagramas UML,](../modeling/edit-uml-models-and-diagrams.md)se describen los pasos detallados para crear cualquiera de los diagramas de modelado.

#### <a name="to-create-a-sequence-diagram"></a>Para crear un nuevo diagrama de secuencia

1. En el menú **arquitectura** , haga clic en **nuevo diagrama de UML o de capas**.

2. En **plantillas**, haga clic en **Diagrama de secuencia UML**.

3. Especifique un nombre para el diagrama.

4. En **Agregar a proyecto de modelado**, seleccione un proyecto de modelado existente en la solución o **cree un nuevo proyecto de modelado**y, a continuación, haga clic en **Aceptar**.

    Aparece un nuevo diagrama de secuencia con el cuadro de herramientas **Diagrama de secuencia** . El cuadro de herramientas contiene los elementos y conectores necesarios.

   ![Partes de un diagrama de secuencia](../modeling/media/uml-sequence.png "UML_Sequence")

#### <a name="to-draw-a-sequence-diagram"></a>Para dibujar un diagrama de secuencia

1. Arrastre **lifelines** (1) desde el **cuadro de herramientas** hasta el diagrama para representar instancias de clases, componentes, actores o dispositivos.

    > [!NOTE]
    > También puede crear una línea de vida arrastrando una clase, interfaz, actor o componente existente desde el **Explorador de modelos UML** hasta el diagrama. Esto crea una línea de vida que representa una instancia del tipo elegido.

2. Dibuje mensajes para mostrar cómo colaboran las líneas de vida para lograr un objetivo específico.

     Para crear un mensaje (3, 4, 6, 7), haga clic en una herramienta de mensajes. A continuación, haga clic en la línea de vida emisora en el punto donde desea que comience el mensaje y, a continuación, haga clic en la línea de vida receptora.

     Una ocurrencia de ejecución (5) aparece en la línea de vida receptora. La ocurrencia de ejecución representa un período de tiempo durante el cual la instancia está ejecutando un método. Puede crear otros mensajes que se inicien desde una ocurrencia de ejecución.

3. Para mostrar un mensaje que procede de un origen de eventos desconocido (9) o que difunde a destinatarios desconocidos (10), dibuje un mensaje asincrónico desde o hacia el espacio en blanco del diagrama. Estos mensajes se denominan *mensajes encontrados* (9) y *mensajes perdidos* (10).

    > [!NOTE]
    > Para mover un grupo de las línea de vida que han perdido o encontrado mensajes, siga estos pasos para seleccionar las línea de vida antes de moverlas: dibuje un rectángulo alrededor de esas línea de vida o mantenga presionada la tecla **Ctrl** mientras hace clic en cada línea de vida. Si usa **seleccionar todo** o **Ctrl**+a para seleccionar todas las **línea de vida** y, a continuación, moverlas, los mensajes perdidos o encontrados que estén adjuntos a estas Lifeline no se moverán. En este caso, podrá mover estos mensajes por separado.

4. Dibuje diagramas de secuencia para cada mensaje principal dirigido al mismo componente o sistema.

#### <a name="to-change-the-order-of-messages"></a>Para cambiar el orden de presentación de los mensajes

- Arrastre un mensaje hacia arriba o hacia abajo en su línea de vida. Puede arrastrarlo sobre otros mensajes o dentro o fuera de un bloque de ejecución.

     \- o -

- Haga clic en el mensaje y use las teclas **flecha arriba** y **flecha abajo** para ajustar las posiciones de los mensajes. Use **Mayús + Flecha arriba** y **Mayús + Flecha abajo** para cambiar el orden de los mensajes.

#### <a name="to-move-or-copy-message-sequences-on-the-sequence-diagram"></a>Para mover o copiar secuencias de mensajes en el diagrama de secuencia

1. Haga clic con el botón secundario en un mensaje (3, 4) y, a continuación, haga clic en **copiar**.

2. Haga clic con el botón secundario en la ocurrencia de ejecución (5) o en una línea de vida (1) desde la que desea enviar el nuevo mensaje y, a continuación, haga clic en **pegar**. El nuevo remitente puede estar en un diagrama diferente si lo desea.

     Una copia del mensaje y todos sus mensajes secundarios se agrega al final de la ocurrencia de ejecución o al final de la línea de vida.

    > [!NOTE]
    > El mensaje pegado siempre aparece al final de la ocurrencia de ejecución o línea de vida. Después de pegarlo, puede arrastrarlo hasta una posición anterior.

#### <a name="to-display-and-edit-the-signature-text-for-a-message"></a>Para mostrar y editar el texto de la firma de un mensaje

- La línea de vida de destino debe estar enlazada o asignada para que los tipos del texto de la firma estén visible. Para realizar esta tarea, realice uno de los siguientes pasos:

  - Haga clic con el botón secundario en la línea de vida y, a continuación, elija **crear clase**.

     O bien,

  - Seleccione la línea de vida, presione **F4**y, a continuación, en la ventana **propiedades** , establezca la propiedad **tipo** en un tipo existente o especifique el nombre de un nuevo tipo. Haga clic con el botón secundario en la etiqueta del mensaje y elija **crear operación**.

    El texto de la firma aparece debajo de la etiqueta del mensaje. Ahora puede editar el texto de la firma. Para obtener más información, vea [clases y lifelines](#ClassesAndLifelines).

#### <a name="to-improve-the-layout-of-a-sequence-diagram"></a>Para mejorar el diseño de un diagrama de secuencia

- Haga clic con el botón secundario en una parte en blanco del diagrama y, a continuación, haga clic en **reorganizar diseño**.

- Para deshacer la operación, haga clic en **Editar**y, a continuación, haga clic en **Deshacer**.

#### <a name="to-change-the-package-that-owns-the-interaction"></a>Para cambiar el paquete que contiene la interacción

1. En el **Explorador de modelos UML**, busque la interacción que muestra el diagrama de secuencia.

    > [!NOTE]
    > La interacción no aparecerá en el **Explorador de modelos UML** hasta que se agregue la primera línea de vida al diagrama de secuencia.

2. Arrastre la interacción hasta el paquete.

     \- o -

     Haga clic con el botón secundario en la interacción y, a continuación, haga clic en **cortar**. Haga clic con el botón secundario en el paquete y, a continuación, haga clic en **pegar**.

## <a name="Simple"></a>Crear y usar diagramas de secuencia simples
 La forma más simple y más difundida de diagrama de secuencia contiene solo líneas de vida y mensajes. Un diagrama de este tipo permite mostrar claramente una secuencia típica de las interacciones entre los objetos del diseño o entre el sistema y sus usuarios. Esto suele ser suficiente para ayudarle a debatir y transmitir el diseño.

 Estas son algunas consideraciones cuando dibuja un diagrama de secuencia sencillo.

### <a name="types-of-message"></a>Tipos de mensaje
 Hay tres herramientas que puede usar para crear mensajes.

- Use la herramienta **sincrónica** para describir una interacción en la que el remitente espera a que el receptor devuelva una respuesta (3).

     Al final de la repetición de ejecución, se mostrará un **<\<> flecha >** . Indica la devolución del control al remitente.

- Use la herramienta **asincrónica** para describir una interacción en la que el remitente puede continuar inmediatamente sin tener que esperar al receptor (4).

- Use la herramienta **crear** para describir una interacción en la que el remitente crea el receptor (8).

     Un mensaje de creación debe ser el primer mensaje que recibe el receptor.

### <a name="annotating-the-interactions"></a>Comentar las interacciones
 Para describir más detalles sobre la secuencia, puede colocar un **Comentario** en cualquier parte del diagrama.

 Mediante el uso de **vínculos de comentario**, puede vincular un comentario a las línea de vida, las ejecuciones, los usos de interacción y los fragmentos.

> [!CAUTION]
> Cuando desee adjuntar un comentario a un punto determinado en la secuencia, vincúlelo a una ocurrencia de ejecución, uso de interacción o fragmento. No lo vincule a una línea de vida, porque en ese caso, no permanecerá adjunto en el punto correcto de la secuencia.

 Use un comentario para:

- Tener en cuenta lo que se ha logrado en puntos clave de la secuencia. Esto ayuda a los lectores a ver los objetivos de las interacciones.

- Describir el objetivo global de toda la secuencia. Adjunte el comentario a la ocurrencia de ejecución inicial o déjelo sin adjuntar. Por ejemplo, "el cliente eligió elementos del menú y se le proporcionó un precio".

- Describir las responsabilidades de cada línea de vida. Adjunte el comentario a la línea de vida. Por ejemplo, "el administrador de pedidos recopila las elecciones del menú del cliente".

- Tener en cuenta las excepciones o alternativas que pueden realizarse como una alternativa a la secuencia típica mostrada. Por ejemplo, "el cliente puede optar por omitir el resto de esta secuencia".

  - Considere la posibilidad de usa fragmentos como una alternativa más formal a este tipo de nota. Vea [describir estructuras de control con fragmentos](#Fragments)

## <a name="deciding-the-scope-of-the-diagram"></a>Decidir el ámbito del diagrama
 Es importante tener claro lo que el diagrama está diseñado para mostrar.

#### <a name="initiating-event"></a>Evento de iniciación
 Cada diagrama debe mostrar la secuencia de interacciones que es el resultado de un evento de iniciación. Por ejemplo, podría ser:

- Un usuario que inicia un caso de uso, por ejemplo, abrir la página web para comprar alimentos.

- Un mensaje de un componente del sistema a otro, por ejemplo, para consultar la disponibilidad de los artículos que un cliente desea comprar.

- Un evento desencadenado por un cambio de estado, por ejemplo, las existencias de un artículo que caen por debajo del umbral.

#### <a name="level-of-detail"></a>Nivel de detalle
 Los diagramas de secuencia pueden mostrar diferentes niveles de detalle. Puede decidir el nivel de detalle en dos dimensiones diferentes casi con total independencia:

 Las líneas de vida pueden representar uno de estos niveles de detalle:

- Los objetos en el código de programa, que ya existe o que está desarrollando.

- Los componentes o sus subcomponentes, que suelen omitir fachadas, servidores proxy y otros mecanismos de conexión.

- El sistema y los actores externos

  Los mensajes pueden representar uno de estos niveles de detalle:

- Los mensajes de software en el código de programa, en una API o interfaz web.

- Las transacciones o subtransacciones, por ejemplo, entre los usuarios y el sistema, o entre el código y la base de datos.

- Casos de uso: interacciones principales entre los usuarios y el sistema.

  Tanto si va a explorar el código existente como si va a describir un nuevo diseño, a menudo resulta útil dibujar y discutir las vistas menos detalladas.

## <a name="describing-variations"></a>Descripción de variaciones
 El diagrama muestra una única secuencia típica de eventos. Si desea mostrar las alternativas posibles, como los escenarios de error, puede usar cualquiera de estas opciones:

- Dibujar diagramas de secuencia diferentes para describir dichos escenarios

- Use la [Descripción de estructuras de control con fragmentos](#Fragments) para mostrar bucles, alternativas, etc.

## <a name="assessing-the-design"></a>Evaluación del diseño
 Puede usar el diagrama para evaluar la distribución de las tareas entre sus objetos o componentes. Considere la refactorización si observa estos patrones:

- Una línea de vida parece hacer todo, hacer llamadas a todo lo demás, mientras que las otras líneas de vida solo responden de forma pasiva.

- Muchos mensajes cruzan las líneas de vida. Cada línea de vida debe enviar mensajes a unos pocos elementos vecinos y no debe comunicarse con los vecinos de sus vecinos. Normalmente debería ser posible organizar las líneas de vida, de modo que haya muy pocos lugares donde los mensajes cruzan las líneas de vida. Y cuando hay cruces, la línea de vida de destino tampoco debe intercambiar los mensajes que tienen las líneas de vida cruzadas.

- Algunas líneas de vida pueden controlar más de un tipo de tarea. Debería ser fácil encontrar una frase sucinta que describa las responsabilidades de cada línea de vida y resuma el trabajo que realiza en respuesta a cada mensaje que recibe.

## <a name="ClassesAndLifelines"></a>Clases y lifelines
 Las líneas de vida de los diagramas de secuencia muestran instancias de clases o interfaces de componentes. Puede designar una línea de vida de dos maneras:

|**Para este propósito**|**Usar este formato**|
|--------------------------|-------------------------|
|Instancia anónima de un tipo.<br /><br /> Úselo si tiene solo una línea de vida de cada tipo.|*nombreDeTipo*|
|Instancia con nombre de un tipo.<br /><br /> Úselo si desea mostrar una secuencia que implica más de una instancia del mismo tipo.|*objectname*:*TypeName*|

### <a name="creating-lifelines-from-types"></a>Crear líneas de vida a partir de tipos
 Puede crear nuevas líneas de vida de las clases que ya definió, por ejemplo, en un diagrama de clases.

> [!NOTE]
> Asegúrese de que tiene un diagrama de secuencia existente antes de realizar esta tarea.

##### <a name="to-create-a-lifeline-from-an-existing-type"></a>Para crear una línea de vida a partir de un tipo existente

- Arrastre una clase, un componente o una interfaz desde el explorador de modelos UML hasta un diagrama de secuencia.

   \- o -

  1. Haga clic con el botón secundario en la clase, componente o interfaz en el diagrama correspondiente y, a continuación, haga clic en **Crear línea de vida**.

  2. En el cuadro de diálogo **Crear línea de vida** , seleccione un diagrama de secuencia y, a continuación, haga clic en **Aceptar**.

     Aparece una nueva línea de vida de la instancia con nombre cuyo tipo es el tipo que arrastró.

  > [!NOTE]
  > Puede repetir esta acción tantas veces como desee. Se crearán líneas de vida con nombres de instancia diferentes.

##### <a name="to-change-the-type-of-a-lifeline"></a>Para cambiar el tipo de una línea de vida

1. Haga clic con el botón secundario en una línea de vida y luego haga clic en **propiedades**.

2. En la ventana **propiedades** , establezca la propiedad **tipo** . Puede seleccionar un tipo en el menú desplegable o escribir un nombre nuevo.

### <a name="creating-classes-from-lifelines"></a>Creación de clases a partir de líneas de vida
 Cuando haya creado uno o varios diagramas de secuencia, puede resumir las líneas de vida mediante la creación de clases o interfaces de estas.

##### <a name="to-create-a-class-or-interface-from-a-lifeline"></a>Para crear una clase o interfaz desde una línea de vida

1. Haga clic con el botón secundario en la línea de vida y, a continuación, haga clic en **crear clase** o **crear interfaz**.

     Aparece una nueva clase o interfaz en el Explorador de modelos UML.

2. Cree operaciones en la clase o interfaz para cada mensaje que recibe la línea de vida:

    1. Seleccione todos los mensajes que desea incluir.

    2. Haga clic con el botón secundario en uno de los mensajes y, a continuación, haga clic en **crear método**.

         La nueva clase o interfaz tiene operaciones para cada mensaje seleccionado.

         El nombre de la operación aparece debajo de cada flecha de mensaje y en la propiedad **operación** del mensaje.

         Si el mensaje contiene parámetros en el formulario "(parámetro: tipo)", aparecerán en la lista de parámetros de la operación de nueva.

        > [!NOTE]
        > Debe repetir este paso si agrega nuevos mensajes en el diagrama de secuencia.

3. Para ver la nueva clase o interfaz en detalle, agréguela a un diagrama de componentes o de clases.

    1. Abra o cree un diagrama de componentes o de clases.

    2. Arrastre la nueva clase o interfaz desde el **Explorador de modelos UML** hasta un diagrama de clases.

         La clase o interfaz aparece en el diagrama de clases.

         \- o -

    3. Arrastre la nueva interfaz desde el **Explorador de modelos UML** hasta un componente o un puerto en un diagrama de componentes.

         La interfaz aparece en el componente como un círculo.

### <a name="creating-classes-for-parameters"></a>Crear clases para los parámetros
 Puede incluir parámetros en los mensajes de un diagrama de secuencia. Puede usar un diagrama de clases UML para describir los tipos de parámetros.

## <a name="Multiple"></a>Crear secuencias de interacción reutilizables
 Puede usar un diagrama independiente para describir una secuencia que contiene los detalles que desea separar o que es común entre varios diagramas.

 Puede crear un rectángulo de uso de interacción (12) en un diagrama que apunte a los detalles en otro diagrama.

 Haga doble clic en un uso de interacción para abrir el diagrama de secuencia que está vinculado a este.

#### <a name="to-create-a-reusable-interaction-sequence-from-existing-lifelines"></a>Para crear una secuencia de interacción reutilizable a partir de líneas de vida existentes

1. En el **cuadro de herramientas**, haga clic en **uso de interacción**.

2. En el diagrama de secuencia, mantenga presionado el botón del mouse mientras arrastra las líneas de vida que desea incluir en la secuencia reutilizable. Empiece en la posición vertical donde desee insertar el uso de interacción.

     Aparece un uso de interacción en las líneas de vida seleccionadas en el diagrama de secuencia.

3. Haga doble clic en el nombre del uso de interacción y cámbielo para describir el efecto de la secuencia reutilizable de este diagrama.

     \- o -

     Escriba el nombre como una llamada de función con parámetros.

4. Vincule el uso de interacción a otro diagrama de secuencia Haga clic con el botón secundario en el uso de interacción y después realice cualquiera de las siguientes acciones:

     Haga clic en **crear nueva secuencia** para crear un nuevo diagrama de secuencia

     \- o -

     Haga clic en **vincular a secuencia** para vincular a un diagrama existente.

     Visual Studio crea un vínculo entre el uso de interacción y la nueva secuencia de interacción.

     Aparece un nuevo diagrama de secuencia en la solución que contiene las líneas de vida utilizadas para crear el uso de interacción.

    > [!NOTE]
    > Solo se incluirán las líneas de vida utilizadas para crear el uso de interacción. El nuevo diagrama no incluirá las líneas de vida creadas después del  uso de interacción, aunque el uso de interacción las cubra ahora.

#### <a name="to-create-a-reusable-sequence-from-existing-messages"></a>Para crear una secuencia reutilizable a partir de mensajes existentes

- Haga clic con el botón secundario en el mensaje que desea desplace y, a continuación, haga clic en **cambiar a diagrama**.

  Visual Studio:

  - Reemplaza con un uso de interacción el mensaje seleccionado y sus mensajes secundarios.

  - Mueva los mensajes reemplazados a un nuevo diagrama de secuencia.

  - Crea un vínculo entre el uso de interacción y el nuevo diagrama de secuencia.

#### <a name="to-navigate-to-the-sequence-referenced-by-an-interaction-use"></a>Para navegar a la secuencia a la que hace referencia un uso de interacción

- Haga doble clic en el uso de interacción.

     \- o -

     Haga clic con el botón secundario en el uso de interacción y haga clic en **ir a secuencia**.

### <a name="creating-a-placeholder-with-an-interaction-use"></a>Crear un marcador de posición con un uso de interacción
 Puede crear un uso de interacción sin vincularlo a otro diagrama. Se puede usar como marcador de posición para una parte de la secuencia cuyos detalles todavía se van a trabajar. Use el nombre del uso de interacción para indicar el resultado que desea.

## <a name="Collapse"></a>Contraer grupos de línea de vida
 Puede contraer un conjunto de líneas de vida juntas, de modo que el grupo aparezca como una sola línea de vida. Esto le ayudará a visualizar un grupo de objetos como un solo componente. Se ocultan los mensajes y usos de interacción entre las líneas de vida de un grupo contraído. Se muestran los mensajes y las secuencias de interacción que incluyen otras líneas de vida.

#### <a name="to-collapse-a-group-of-lifelines-together"></a>Para contraer un grupo de líneas de vida juntos

1. Seleccione dos o más líneas de vida.

2. Haga clic con el botón secundario en uno de ellos y, a continuación, haga clic en **contraer**.

     Las líneas de vida independientes se reemplazan por una única línea de vida.

     Se ocultan los mensajes y usos de interacción que solo implican a miembros del grupo.

3. Para cambiar el nombre del grupo, haga clic en el nombre.

    > [!NOTE]
    > Se perderá el nombre del grupo cuando expanda el grupo.

#### <a name="to-expand-a-collapsed-group"></a>Para expandir un grupo contraído

- Haga clic con el botón secundario en la línea de vida contraída y, a continuación, haga clic en **expandir**.

    > [!NOTE]
    > Se perderá el nombre del grupo, junto con todos los vínculos del grupo a los comentarios o elementos de trabajo.

## <a name="Fragments"></a>Describir estructuras de control con fragmentos
 Puede usar fragmentos combinados (13) para definir bucles, bifurcaciones y el procesamiento simultáneo en un diagrama de secuencia. Como alternativa, considere la posibilidad de usar en su lugar un diagrama de actividad. El diagrama de actividad no es tan útil al mostrar mensajes entre actores, pero en algunos casos es mejor al mostrar bucles, bifurcaciones y simultaneidad.

 Para obtener una lista completa de los tipos de fragmentos, vea [describir el flujo de control con fragmentos en diagramas de secuencia de UML](../modeling/describe-control-flow-with-fragments-on-uml-sequence-diagrams.md).

#### <a name="to-create-a-combined-fragment"></a>Para crear un fragmento combinado

1. Seleccione un mensaje o una secuencia de mensajes que comiencen en la misma línea de vida u ocurrencia de ejecución.

    > [!NOTE]
    > Seleccione las flechas del mensaje, no las ocurrencias de ejecución a las que apuntan los mensajes.

2. Haga clic con el botón secundario en uno de los mensajes, seleccione **rodear con**y, a continuación, haga clic en el tipo de fragmento que necesite.

     Aparecerá un nuevo fragmento que contiene los mensajes seleccionados.

     Si el tipo de fragmento combinado permite varios fragmentos, también aparecerá un fragmento vacío.

3. Para establecer la protección de un fragmento, haga clic con el botón secundario en el borde del fragmento y, a continuación, haga clic en **propiedades**. Establezca la propiedad **Guard** .

     La restricción se usa para definir la condición de una bifurcación o un bucle.

4. Para agregar un nuevo fragmento a un tipo que permita varios fragmentos, haga clic con el botón secundario en el límite de un fragmento y seleccione **Agregar**. Haga clic en cualquier **operando de interacción antes** o en **operando de interacción después**de.

5. Para agregar nuevos mensajes a un fragmento, use las herramientas de mensajes o copiar y pegar.

## <a name="see-also"></a>Vea también
 [Diagramas de secuencia UML: referencia](../modeling/uml-sequence-diagrams-reference.md) [Editar modelos y diagramas UML](../modeling/edit-uml-models-and-diagrams.md) [diagramas de casos de uso de UML:](../modeling/uml-use-case-diagrams-reference.md) referencia [diagramas de clases de UML: referencia](../modeling/uml-class-diagrams-reference.md) [diagramas de componentes de UML: referencia](../modeling/uml-component-diagrams-reference.md) diagramas de [componentes de UML:](../modeling/uml-component-diagrams-reference.md) vídeo de referencia: [esbozar interacciones mediante diagramas de secuencia](https://go.microsoft.com/fwlink/?LinkId=201113)
