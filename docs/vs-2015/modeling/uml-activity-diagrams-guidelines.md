---
title: 'Diagramas de actividades UML: Instrucciones | Documentos de Microsoft'
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 626be40ed9889ff7d16c07d511cbd060232412af
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60105078"
---
# <a name="uml-activity-diagrams-guidelines"></a>Diagramas de actividades UML: Instrucciones
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En Visual Studio, puede dibujar un diagrama de actividades para describir un proceso de negocio o un algoritmo de software como un flujo de trabajo a través de una serie de acciones. Las personas, los componentes de software o los dispositivos pueden realizar estas acciones. Para una demostración en vídeo, consulte: [Capturar flujos de trabajo empresariales mediante diagramas de actividades](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-4-Capture-Business-Workflows/).  
  
 Para ver qué versiones de Visual Studio admiten esta característica, vea [Compatibilidad de versiones con las herramientas de arquitectura y modelado](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Para crear un diagrama de actividades UML, en el **arquitectura** menú, haga clic en **nuevo UML o diagrama de capas**.  
  
 Puede usar un diagrama de actividades para muchos fines:  
  
- Para describir un proceso de negocio o un flujo de trabajo entre los usuarios y el sistema. Para obtener más información, consulte [modelar los requisitos del usuario](../modeling/model-user-requirements.md).  
  
- Para describir los pasos que se realizan en un caso de uso. Para obtener más información, consulte [diagramas de casos de uso de UML: Directrices](../modeling/uml-use-case-diagrams-guidelines.md).  
  
- Para describir un método, una función o una operación en el software. Para obtener más información, consulte [modelar la arquitectura de la aplicación](../modeling/model-your-app-s-architecture.md).  
  
  Dibujar un diagrama de actividades puede ayudarle a mejorar un proceso. Si el diagrama de un proceso existente resulta muy complejo, puede considerar cómo se podría simplificar el proceso.  
  
  Para obtener información de referencia sobre los elementos de diagramas de actividades, consulte [diagramas de actividades UML: referencia](../modeling/uml-activity-diagrams-reference.md).  
  
## <a name="Relationships"></a> Relación con otros diagramas  
 Si dibuja un diagrama de actividades para describir un proceso de negocio o la manera en que los usuarios usan el sistema, puede dibujar un diagrama de casos de uso para mostrar una vista diferente de la misma información. En el diagrama de casos de uso, las acciones se dibujan como casos de uso. Asigne a los casos de uso los mismos nombres que las acciones correspondientes. Las ventajas de la vista de casos de uso son las siguientes:  
  
- Puede mostrar en un diagrama la manera en que las acciones y los casos de uso más grandes se componen de otros más pequeños, mediante la relación Includes.  
  
- Puede conectar cada acción o caso de uso explícitamente a los usuarios o a los sistemas externos implicados en su ejecución.  
  
- Puede dibujar límites alrededor de las acciones y los casos de uso admitidos por el sistema o alrededor de cada componente importante.  
  
  También puede dibujar un diagrama de actividades para describir el diseño detallado de una operación de software.  
  
  En un diagrama de actividades, puede mostrar el flujo de datos que se pasan entre las acciones. Consulte la sección sobre [describir el flujo de datos](#DataFlows). Sin embargo, un diagrama de actividades no describe la estructura de los datos. Para ello, puede dibujar un diagrama de clases UML. Para obtener información, consulte [diagramas de clases UML: Directrices](../modeling/uml-class-diagrams-guidelines.md).  
  
## <a name="BasicSteps"></a> Pasos básicos para dibujar diagramas de actividades  
 Se describen los pasos detallados para crear cualquiera de los diagramas de modelado en [modelos y diagramas UML editar](../modeling/edit-uml-models-and-diagrams.md).  
  
#### <a name="to-draw-an-activity-diagram"></a>Para dibujar un diagrama de actividades  
  
1. En el **arquitectura** menú, haga clic en **nuevo UML o diagrama de capas**.  
  
2. En **plantillas**, haga clic en **diagrama de actividades UML**.  
  
3. Especifique un nombre para el diagrama.  
  
4. En **agregar a proyecto de modelado**, seleccione un proyecto de modelado existente de la solución, o **crear un nuevo proyecto de modelado**.  
  
#### <a name="to-draw-elements-on-an-activity-diagram"></a>Para dibujar elementos en un diagrama de actividades  
  
1. Arrastre elementos desde el cuadro de herramientas al diagrama.  
  
     Comience colocando las actividades principales en el diagrama, conéctelas e incorpore los últimos detalles, como los nodos iniciales y finales.  
  
    > [!NOTE]
    >  No puede arrastrar elementos existentes al diagrama desde el Explorador de modelos UML.  
  
2. Para conectar los elementos, siga estos pasos:  
  
    1. En el **diagrama de actividades** cuadro de herramientas, haga clic en **conector**.  
  
    2. En el diagrama, haga clic en el elemento de origen.  
  
    3. Haga clic en el elemento de destino.  
  
        > [!NOTE]
        >  Para usar una herramienta varias veces, haga doble clic en la herramienta en el cuadro de herramientas.  
  
#### <a name="to-move-an-activity-to-another-package"></a>Para mover una actividad a otro paquete  
  
- En **Explorador de modelos UML**, arrastre la actividad a un paquete.  
  
     \- o -  
  
- En **Explorador de modelos UML**, haga clic en la actividad y haga clic en **cortar**. A continuación, haga clic en el paquete y haga clic en **pegar**.  
  
    > [!NOTE]
    >  La actividad aparecerá en el Explorador de modelos UML solo cuando se agregue el primer elemento al diagrama.  
  
## <a name="SimpleControlFlow"></a> Describir el flujo de Control  
 Un diagrama de actividades describe un proceso de negocio o un algoritmo de software como una serie de acciones. Las flechas de conector muestran cómo el control pasa secuencialmente de una acción a la siguiente. Normalmente, una acción solo se puede iniciar una vez completada la acción anterior.  
  
 La ilustración siguiente es un ejemplo de cómo se puede mostrar una secuencia de acciones mediante acciones, conectores, bifurcaciones y bucles. Cada elemento se explica con más detalle en las secciones siguientes.  
  
 ![Un diagrama de actividad simple](../modeling/media/uml-actguidectrl.png "UML_ActGuideCtrl")  
  
 Diagramas de actividades usan **acciones** y **conectores** para describir el sistema o la aplicación como una serie de acciones con el control fluye de manera secuencial de una acción a la siguiente.  
  
- Crear un **acción** (1) para cada tarea importante realizada por un usuario, el sistema o ambos en colaboración.  
  
  > [!NOTE]
  >  Intente describir su proceso o algoritmo con unas pocas acciones. Puede usar **llamar a acciones de comportamiento** para definir cada acción con más detalle en un diagrama diferente, como se describe en [describir actividades secundarias con acciones de comportamiento de llamada a](#Subactivities).  
  
- Asegúrese de que el título de cada acción indica claramente lo que suele hacer.  
  
- Vincule las acciones en secuencia con **conectores** (2).  
  
- Cada acción finaliza antes de que comience la acción siguiente del flujo de control. Si desea describir acciones que se superponen, use un **nodo de bifurcación** tal como se describe en la sección [flujos simultáneos](#Concurrent).  
  
  Aunque el diagrama describe la secuencia de acciones, no describe cómo se ejecutan las acciones o cómo se pasa el control de una acción a la siguiente. Si usa el diagrama para representar un proceso de negocio, el control podría pasarse, por ejemplo, cuando una persona envía un mensaje de correo electrónico. Si usa el diagrama para representar un diseño de software, el flujo de ejecución normal podría pasar el control de una instrucción a la siguiente.  
  
### <a name="describing-decisions-and-loops"></a>Describir decisiones y bucles  
  
- Use un **nodo de decisión** (3) para indicar un punto donde el resultado de una decisión dicta el paso siguiente. Puede dibujar tantas rutas de acceso de salida como desee.  
  
- Si usa el diagrama de actividades para definir parte de una aplicación, debe definir las restricciones (4) para que quede claro cuándo se debe tomar cada ruta de acceso. Haga clic en el conector, haga clic en **propiedades**y en el **propiedades** ventana, escriba un valor para el **Guard** campo.  
  
- No siempre es necesario definir las restricciones. Por ejemplo, si usa el diagrama de actividades para describir un proceso de negocio o un protocolo de interacción, una bifurcación define el intervalo de opciones disponibles para el usuario o para los componentes que interactúan.  
  
- Use un **nodo de combinación** (5) para unir dos o más flujos alternativos que se bifurcan en un **nodo de decisión**.  
  
    > [!NOTE]
    >  Debe usar un **nodo de combinación** para unir flujos alternativos, en lugar de unir los flujos en una acción. En el ejemplo, que no sea correcta para conectarse desde el nodo de decisión se copia directamente en **Elegir elemento del menú**. Esto se debe a que una acción no se inicia hasta que los subprocesos de control llegan a todos sus conectores de entrada. Por lo tanto, en una acción solo debe reunir flujos simultáneos. Para obtener más información, consulte [flujos simultáneos](#Concurrent).  
  
- Use las bifurcaciones para describir bucles, tal como se muestra en el ejemplo.  
  
    > [!NOTE]
    >  Intente anidar los bucles de forma bien estructurada, tal como lo haría en el código del programa. Si está describiendo un proceso de negocio existente, esto podría ofrecer oportunidades para mejorarlo.  
  
### <a name="starting-the-activity"></a>Iniciar la actividad  
 Existen dos maneras de indicar los puntos de entrada en una actividad:  
  
- **Nodo inicial**  
  
     Crear una **inicial del nodo** (6) para indicar la primera acción de la actividad.  
  
     Este método es muy útil cuando se describe una actividad secundaria o cuando no es necesario indicar explícitamente qué inicia la actividad. Por ejemplo, no cabe duda de que la actividad Pedir un menú se inicia cuando un cliente tiene hambre.  
  
- **Acepte el nodo de eventos**  
  
     Crear **Aceptar eventos nodos**, tal y como se describe en la sección [flujos simultáneos](#Concurrent), para indicar el inicio de un subproceso que responde a un evento determinado, como un entrada del usuario. No proporcione un flujo de entrada al nodo. Al omitir el flujo de entrada, se indica que se iniciará un subproceso cada vez que se produzca el evento.  
  
     Este método es muy útil cuando se describe una respuesta a un evento externo concreto.  
  
### <a name="ending-the-activity"></a>Finalizar la actividad  
 Use un **nodo Final de actividad** (7) para indicar el final de una actividad.  
  
- Cuando un subproceso de control alcanza un **nodo Final de actividad**, finalización toda la actividad acciones simultáneas y las actividades secundarias.  
  
- Puede usar más de un nodo de final de actividad para reducir la cantidad de conectores adicionales.  
  
### <a name="interrupting-the-activity"></a>Interrumpir la actividad  
 Para describir cómo se puede interrumpir el flujo normal de una actividad, por ejemplo, si el usuario decide cancelar el proceso, puede crear un nodo de aceptación de evento que escuche ese evento. Para obtener más información, consulte la sección [flujos simultáneos](#Concurrent). Cree un flujo de control desde ese nodo hasta un nodo de final de actividad (7).  
  
### <a name="swimlanes"></a>Calles  
 A veces resulta útil organizar las acciones de una actividad en áreas que se corresponden con distintos objetos o roles de negocio que realizan las acciones. Estas áreas se organizan de manera convencional en columnas y se denominan *calles*.  
  
- Use las líneas o rectángulos de la **formas simples** sección del cuadro de herramientas para dibujar calles u otras áreas.  
  
- Para etiquetar cada calle, cree un comentario y establezca su **transparente** propiedad **True**.  
  
  Las formas simples no forman parte del modelo UML y no aparecen en el Explorador de modelos UML.  
  
## <a name="DataFlows"></a> Describir el flujo de datos  
 Puede describir los datos que entran y salen de una actividad de dos maneras:  
  
- Use un **objeto nodo**. Este es el método más sencillo para describir la información que fluye entre las actividades. Un nodo de objeto es como una variable de un programa. Representa algo que almacena uno o varios valores que se pasan de una acción a otra.  
  
- Use un **Output Pin** y un **clavija de entrada**. Este método permite describir por separado las salidas de una acción y las entradas en otra. Los terminales son como los parámetros de un programa. Los terminales representan puertos donde pueden entrar los objetos y dejar una acción.  
  
    > [!NOTE]
    >  Para obtener información general de los elementos usados en esta sección, consulte la sección flujos de datos del tema consulte [diagramas de actividades UML: referencia](../modeling/uml-activity-diagrams-reference.md).  
  
### <a name="describing-data-flow-with-object-nodes"></a>Describir el flujo de datos con nodos de objeto  
 La mayoría de los flujos de control transportan datos. Por ejemplo, el flujo de salida de la acción "El cliente proporciona detalles" lleva una referencia a la dirección de envío.  
  
 Si desea describir esos datos en el diagrama, puede reemplazar un conector con un nodo de objeto y dos conectores, tal como se muestra en la ilustración siguiente.  
  
 ![Nodos de objeto pueden mostrar datos pasados entre acciones](../modeling/media/uml-actguidedata.png "UML_ActGuideData")  
  
 Observe que los rectángulos redondeados, como Despachar mercancía, representan acciones en las que tiene lugar el procesamiento. Los rectángulos cuadrados, como Dirección de envío, representan un flujo de objetos de una acción a otra.  
  
 Asigne al nodo de objeto un nombre que refleje el rol del nodo como canalización o búfer de los objetos que fluyen entre las acciones.  
  
 Puede establecer el **tipo** del nodo de objeto en la ventana Propiedades. El tipo puede ser un tipo primitivo, como un entero, o una clase, interfaz o enumeración que definiese en un diagrama de clases. Por ejemplo, podría crear una clase Dirección de envío, con atributos como Dirección, Ciudad, etcétera, junto con una asociación con otra clase denominada Cliente. Para más información, vea [Diagramas de clases de UML: Directrices](../modeling/uml-class-diagrams-guidelines.md).  
  
> [!NOTE]
>  Si escribe el nombre de un tipo que aún no se han definido, se agregará un elemento en **tipos sin especificar** en el Explorador de modelos UML. Si posteriormente define un tipo con ese nombre en un diagrama de clases, deberá restablecer el tipo del nodo de objeto para que haga referencia al nuevo tipo.  
  
#### <a name="buffering-data-in-object-nodes"></a>Almacenar en búfer los datos de los nodos de objeto  
 Un nodo de objeto puede actuar como búfer de varios objetos. En la ilustración siguiente, el flujo de control muestra que el usuario puede recorrer el bucle [elegir más] (1) muchas veces, mientras el nodo de objeto Elementos del menú seleccionados (2) acumula las selecciones del usuario. Por último, cuando el usuario finaliza su selección, el control pasa a la acción Confirmar pedido (3), que acepta la lista completa de selecciones del búfer Elementos de menú seleccionados.  
  
 ![En el búfer de datos en los nodos de objeto](../modeling/media/uml-actguidebuffer.png "UML_ActGuideBuffer")  
  
 Puede especificar cómo se almacenan los elementos de un búfer estableciendo las propiedades del nodo de objeto:  
  
- Establecer el **Ordering** propiedad:  
  
    - **Desordenados** para especificar un orden aleatorio o indeterminado. (Valor predeterminado).  
  
    - **Ordenar** para especificar un orden según una clave específica.  
  
    - **FIFO** para especificar un orden de primero en salir.  
  
    - **LIFO** para especificar un orden de último en entrar es el primero.  
  
- Establecer el **límite superior** propiedad para especificar el número máximo de objetos que pueden incluirse en el búfer. El valor predeterminado es *. Esto significa que no hay límite.  
  
### <a name="describing-data-flow-with-input-and-output-pins"></a>Describir el flujo de datos con terminales de entrada y salida  
 Use un **clavija de salida** y un **Terminal de entrada** para describir por separado las salidas de una acción y las entradas en otra.  
  
 ![PIN Input y output son parámetros de acción](../modeling/media/uml-actguidepins.png "UML_ActGuidePins")  
  
 Para crear un pin, haga clic en **Terminal de entrada** o **clavija de salida** en el cuadro de herramientas y, a continuación, haga clic en una acción. A continuación, puede mover el terminal alrededor del perímetro de la acción y cambiarle el nombre. Puede crear la entrada y salida bolos en cualquier tipo de acción, incluidos **llamar a acciones de comportamiento**, **llamar a acciones de operación**, **acciones de envío de señal**, y  **Acepte las acciones de evento**.  
  
 Un conector entre dos terminales representa un flujo de objetos, al igual que los flujos de entrada y salida de un nodo de objeto.  
  
 Asigne a cada terminal un nombre que indique el rol de los objetos que genera o acepta, como un nombre de parámetro.  
  
 Puede establecer el tipo de objetos que se transmiten en el **tipo** propiedad. Debe tratarse de un tipo creado en un diagrama de clases UML.  
  
 Los objetos que fluyen entre los terminales conectados deben ser compatibles de alguna manera. La razón es que los objetos generados por el terminal de salida pertenecen a un tipo derivado del tipo del terminal de entrada.  
  
 También puede especificar que el flujo de objetos incluye una transformación que convierte los datos entre el tipo del terminal de salida y el tipo del terminal de entrada. La transformación más común de este tipo solamente extrae la parte adecuada de un tipo mayor. El ejemplo de la ilustración implica la existencia de una transformación que extrae la dirección de envío de los detalles del pedido.  
  
## <a name="Details"></a> Definir una acción con más detalle  
 Además de usar el nombre de la acción para indicar claramente el resultado que normalmente se debe conseguir, existen otras maneras de agregar más detalles a una acción:  
  
- Escribir una descripción más detallada el **cuerpo** propiedad. Por ejemplo, puede escribir un fragmento de código o seudocódigo de programa o una descripción completa de los resultados obtenidos.  
  
- Reemplace la acción con una acción de llamada a comportamiento y describa su comportamiento detallado en un diagrama de actividades independiente. Consulte [describir actividades secundarias con acciones de llamada a comportamiento](#Subactivities).  
  
- Establezca la acción **Local Postconditions** y **Local Preconditions** propiedades para describir el resultado con más detalle. Para obtener más información, consulte [definir las condiciones previas y](#Postcondition).  
  
### <a name="Subactivities"></a> Describir actividades secundarias con acciones de llamada a comportamiento  
 Puede describir el comportamiento detallado de una acción usando un diagrama de actividades independiente. Un comportamiento llamado es un diagrama de actividades que se representa en el diagrama de actividades principal mediante una acción de llamada a comportamiento. También puede usar la acción de llamada a comportamiento para describir el comportamiento que se comparte entre las diferentes actividades, de modo que no tenga que dibujar varias veces la actividad secundaria.  
  
 En la ilustración siguiente, el diagrama 1 muestra una actividad que tiene una acción de llamada a comportamiento, mientras que el diagrama 2 muestra el diagrama de actividad secundaria donde puede verse el comportamiento llamado.  
  
 ![Un diagrama de actividades independiente que muestra acciones detalladas](../modeling/media/uml-actguidedetail.png "UML_ActGuideDetail")  
  
##### <a name="to-describe-a-sub-activity-with-a-call-behavior-action"></a>Para describir una actividad secundaria con una acción de llamada a comportamiento  
  
1. Para crear el diagrama de la actividad secundaria, en **el Explorador de soluciones**, haga clic en el proyecto de modelado, seleccione **agregar**y, a continuación, haga clic en **nuevo elemento**.  
  
2. En el **Agregar nuevo elemento** cuadro de diálogo **plantillas** haga clic en **diagrama de actividades** y en el **nombre** cuadro, escriba el nombre que desea asignar a su **llamar a la acción de comportamiento**.  
  
3. Dibuje el flujo de trabajo detallado de la actividad secundaria. Este es el comportamiento llamado.  
  
    - En el diagrama de actividad secundaria llamada, el **inicial del nodo** indica dónde empieza el control cuando se invoca el comportamiento llamado. El **nodo Final de actividad** muestra dónde debe devolver el control a la actividad principal.  
  
4. Establecer el **comportamiento** propiedad de la **acción del comportamiento de llamada a** para hacer referencia al diagrama del comportamiento llamado.  
  
    > [!NOTE]
    >  El diagrama de actividad secundaria debe contener algunos elementos o el diagrama no estarán disponible en la lista desplegable para la **comportamiento** propiedad. Además, el icono de Tridente no aparecerá en su **acción del comportamiento de llamada a** hasta que se establece de forma su **comportamiento** propiedad.  
  
5. Establecer el **Is Synchronous** propiedad de la acción para indicar si la actividad espera hasta que se complete la actividad llamada.  
  
    - Si establece **Is Synchronous** en false, indicará que el flujo puede continuar en la siguiente acción antes de que finalice la actividad llamada. No debe definir terminales de salida o flujos de datos salientes desde la acción.  
  
### <a name="describing-data-flow-in-and-out-of-sub-activities"></a>Describir el flujo de datos dentro y fuera de las actividades secundarias  
 Puede describir los datos que fluyen dentro y fuera de las actividades secundarias de la misma manera que usa los parámetros en el software.  
  
- Cree terminales de entrada y salida (1) en la acción de llamada a comportamiento para cada elemento de datos que fluya dentro o fuera de la acción. Asigne a cada uno un nombre apropiado.  
  
- En el diagrama de actividad secundaria, cree un **nodo de parámetros de actividad** (2) para cada terminal de entrada y salida en la acción que realiza la llamada. Asigne a cada nodo el mismo nombre que el de su terminal correspondiente.  
  
  > [!NOTE]
  >  Un nodo de parámetros de actividad se parece a un nodo de objeto. Para comprobar qué tipo de nodo que está examinando, haga clic en el nodo y, a continuación, haga clic en **propiedades**. El tipo de nodo se muestra en el encabezado de la ventana Propiedades.  
  
- En el diagrama de actividad secundaria, dibuje conectores que muestren el flujo de objetos dentro o fuera de cada nodo de parámetros de actividad.  
  
  ![Ancla en mapa de comportamiento de llamar a parámetros de actividad](../modeling/media/uml-actguidesub.png "UML_ActGuideSub")  
  
### <a name="Postcondition"></a> Definir condiciones previas y posteriores  
 Puede usar el **Local Postconditions** y **Local Preconditions** propiedades para especificar en detalle el resultado de una acción. Estas propiedades describen el efecto de la acción sin describir cómo se consigue el efecto.  
  
 Para establecer estas propiedades, haga clic en la acción y, a continuación, haga clic en **propiedades**. Escriba los valores de las propiedades en la ventana Propiedades.  
  
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
  
- Puede establecer el **Is Synchronous** propiedad de la acción para indicar si la actividad espera hasta que se complete la operación.  
  
    - Si establece **Is Synchronous** en false, indicará que el flujo puede continuar en la siguiente acción antes de completar la operación llamada. No debe definir terminales de salida o flujos de datos salientes desde la acción.  
  
## <a name="Concurrent"></a> Flujos simultáneos  
 Puede usar el **nodo de bifurcación** y **nodo de unión** para describir dos o más subprocesos de actividades que se pueden ejecutar al mismo tiempo.  
  
 ![Los nodos de unión y bifurcación muestran flujos simultáneos](../modeling/media/uml-actguideconcurrent.png "UML_ActGuideConcurrent")  
  
 El efecto de la **nodo de bifurcación** (1) consiste en dividir el subproceso de control en dos o más subprocesos. Cuando finalice la acción anterior, podrán iniciarse todas las acciones del lado de salida de la bifurcación.  
  
 Un **nodo de unión** (2) reúne los subprocesos simultáneos. La acción después de la **nodo de unión** podrían no iniciarse hasta que todas las acciones que dan lugar a la **nodo de unión** están completos.  
  
### <a name="describing-signals-and-events"></a>Describir señales y eventos  
 Puede mostrar un paso en un proceso que envía una señal como una acción de envío de señal de una actividad. Puede mostrar un paso que espera una señal específica o un evento antes de que el paso pueda continuar como una acción de aceptación de evento.  
  
 Por ejemplo, puede mostrar un paso que envía un pedido y, a continuación, otro paso que debe recibir el pedido antes de procesarlo.  
  
#### <a name="sending-a-signal"></a>Enviar una señal  
 Use una acción de envío de señal (3) para indicar que se envía una señal o un mensaje de algún tipo a otras actividades o procesos. Use el nombre de la acción para indicar qué tipo de mensaje se envía.  
  
- El control pasa inmediatamente a la acción siguiente del flujo de control, si la hay.  
  
- No puede usar una acción de envío de señal para describir cómo responde el proceso a una información devuelta. Para ello, use una acción de aceptación de evento independiente.  
  
- Puede mostrar el flujo de datos entrante en una acción de envío de señal para indicar qué datos pueden enviarse con el mensaje saliente. Para obtener más información, consulte [describir el flujo de datos](#DataFlows).  
  
#### <a name="waiting-for-a-signal-or-event"></a>Esperar una señal o evento  
 Use una acción de aceptación de evento (4) para indicar que esta actividad espera algún evento externo o mensaje entrante. Use el nombre de la acción para indicar el tipo de evento que espera.  
  
- Para mostrar que la actividad espera un mensaje o evento externo en un punto concreto de su flujo, dibuje una acción de aceptación de evento con un flujo de entrada en el lugar adecuado de la actividad.  
  
- Para mostrar que la actividad puede responder a un mensaje o evento externo en cualquier momento, dibuje una acción de aceptación de evento sin flujo de entrada. Cuando se produce el evento externo con nombre, se iniciará un nuevo subproceso en la actividad a partir de la acción de aceptación de evento.  
  
- No puede usar una acción de aceptación de evento para describir el valor devuelto al remitente de la señal. Use una acción de envío de señal diferente para ese propósito.  
  
- Puede mostrar flujos de datos salientes de la acción para indicar cómo procesa la actividad los datos que se reciben en la señal. Si desea mostrar más de un flujo de salida, debe establecer el **IsUnmarshall** propiedad de la acción de aceptación de evento, lo que indica que la acción analiza la señal de entrada en sus diferentes componentes. Para obtener más información, consulte [describir el flujo de datos](#DataFlows).  
  
### <a name="describing-multiple-data-flows"></a>Describir varios flujos de datos  
 Puede dibujar más de un flujo de control o flujo de objeto saliendo de una acción para indicar que varios subprocesos emergen cuando finaliza la acción. El efecto es similar al de una bifurcación, salvo que se puede usar una combinación de flujos de control y objeto.  
  
 El ejemplo siguiente muestra varios flujos que entran y salen de acciones.  
  
 ![Flujos de objeto en paralelo](../modeling/media/uml-actguidemulti.png "UML_ActGuideMulti")  
  
 Cuando se completa la acción "El cliente proporciona detalles", genera dos objetos: "Dirección de envío" y "detalles de la tarjeta de crédito". Los dos objetos avanzan en el procesamiento mediante acciones diferentes.  
  
 Dado que una acción requiere que todas sus entradas estén disponibles antes de iniciarse, la última acción no se inicia hasta que se completen todas las acciones anteriores.  
  
### <a name="streams"></a>Secuencias  
 Puede usar un diagrama de actividades para describir una canalización o una serie de acciones que se ejecutan al mismo tiempo y pasan datos continuamente de una acción a otra.  
  
 La finalidad del ejemplo siguiente es que cada acción genere objetos y siga funcionando. Dado que no hay flujos de control, cada acción se puede iniciar en cuanto recibe sus primero objetos.  
  
 Observe que los conectores de este ejemplo son flujos de objeto, ya que todos tienen al menos un extremo en un nodo de parámetros de actividad, un nodo de objeto o un terminal de entrada o salida.  
  
 ![Un flujo de datos](../modeling/media/uml-actguidestream.png "UML_ActGuideStream")  
  
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
  
  ![Objeto definido en otro diagrama de transformación](../modeling/media/uml-actguidetransform.png "UML_ActGuideTransform")  
  
  Puede especificar una transformación o selección de dos maneras:  
  
- Adjunte un comentario al terminal de entrada o salida.  
  
  - Para distinguir esta descripción de un comentario general, puede empezar el comentario con <\<**transformación**>> o <\<**selección**>>.  
  
- Especifique con detalle la transformación o selección en un diagrama de actividades independiente.  
  
  - Si usa este método, adjunte también un comentario para dejar claro a los lectores que se definió la transformación.  
  
##### <a name="to-specify-a-transformation-or-selection-in-a-separate-activity-diagram"></a>Para especificar una transformación o selección en un diagrama de actividades independiente  
  
1. Cree un nuevo diagrama de actividades en el que se describa el flujo de transformación o selección.  
  
   - En **el Explorador de soluciones**, haga clic en el proyecto, seleccione **agregar**, haga clic en **nuevo elemento**y, a continuación, haga clic en **diagrama de actividades**. Asigne al diagrama un nombre adecuado para el flujo de transformación o selección. Haga clic en **Agregar**.  
  
2. En el nuevo diagrama:  
  
   1. Cree dos nodos de parámetros de actividad, uno para el flujo de entrada y otro para el de salida.  
  
   2. Cree acciones interconectadas con los flujos de objeto. De esta manera se muestra cómo funciona la transformación o la selección.  
  
3. En los diagramas en los que desee usar la transformación o la selección:  
  
   1. Cree un flujo de objeto, es decir, un conector que entre o salga de un terminal de entrada o salida, un nodo de objeto o un nodo de parámetros de actividad.  
  
   2. Haga clic en el flujo de objeto y, a continuación, haga clic en **propiedades**.  
  
   3. En el **transformación** o **selección** propiedad, seleccione el diagrama en la que especificó el flujo de transformación o selección.  
  
   También puede definir una selección en un nodo de objeto y en terminales de entrada y salida individuales. Definir una actividad de selección como en el procedimiento anterior y, a continuación, establezca el **selección** propiedad del nodo de objeto, o Terminal de entrada o salida.  
  
## <a name="see-also"></a>Vea también  
 [Editar modelos y diagramas UML](../modeling/edit-uml-models-and-diagrams.md)   
 [Diagramas de secuencia de UML: Referencia](../modeling/uml-sequence-diagrams-reference.md)   
 [Diagramas de componentes UML: Referencia](../modeling/uml-component-diagrams-reference.md)   
 [Diagramas de casos de uso UML: Referencia](../modeling/uml-use-case-diagrams-reference.md)   
 [Diagrama de clases de UML: Referencia](../modeling/uml-class-diagrams-reference.md)   
 [Diagramas de componentes UML: Referencia](../modeling/uml-component-diagrams-reference.md)   
 [Vídeo: Capturar flujos de trabajo empresariales mediante diagramas de actividades](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-4-Capture-Business-Workflows/)
