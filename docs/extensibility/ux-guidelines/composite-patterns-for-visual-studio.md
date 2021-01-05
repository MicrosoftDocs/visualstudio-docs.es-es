---
title: Patrones compuestos para Visual Studio | Microsoft Docs
description: Obtenga información sobre los patrones compuestos importantes para lograr coherencia en Visual Studio. Los patrones compuestos combinan elementos de interacción y diseño.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e48ecfb2-f4b5-4d3a-b4a2-7a4d62fa4ec0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 719ce0ac88761599fbed7da90643fd8a9d79db69
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2020
ms.locfileid: "97715826"
---
# <a name="composite-patterns-for-visual-studio"></a>Patrones compuestos para Visual Studio
Los patrones compuestos combinan elementos de interacción y diseño en configuraciones distintas. Algunos de los patrones compuestos más importantes en Visual Studio con respecto a la coherencia incluyen:

- [Visualización de datos](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_DataVisualization)

- [Interfaz de usuario y inspección de objetos en el objeto](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

- [Modelos de selección](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

- [Persistencia y guardado de la configuración](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

- [Entrada táctil](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)

## <a name="data-visualization"></a><a name="BKMK_DataVisualization"></a> Visualización de datos

### <a name="overview"></a>Información general
 Los gráficos son un método visual para agregar y visualizar datos con el fin de mejorar la toma de decisiones. Pueden ayudar a los usuarios a tener una gran cantidad de datos, pero poco significado ven qué merece la atención y lo que podría necesitar una acción.

 El usuario se beneficiará de un gráfico si se cumple alguna de las siguientes condiciones:

- ¿El gráfico ayudará a los usuarios a identificar las tareas en las que pueden actuar?

- ¿El gráfico permitirá a los usuarios pronosticar las consecuencias de los posibles cambios?

- ¿El gráfico ayudará a los usuarios a detectar tendencias e identificar patrones?

- ¿El gráfico permitirá a los usuarios tomar mejores decisiones?

- ¿Le ayudará el gráfico a responder a una pregunta específica que pueden tener los usuarios en el contexto determinado?

#### <a name="general-rules-for-charts"></a>Reglas generales para gráficos

- Etiquete los datos con claridad. Las ilustraciones sin explicación son simplemente imágenes muy precisas.

- Inicie los ejes en cero para evitar el sesgo de las proporciones. La longitud de línea y el tamaño de la barra son indicaciones visuales importantes para comprender las relaciones entre los puntos de datos.

- Cree gráficos, no infografías. Infografías son representaciones artísticas de los datos y su objetivo principal es visual contar historias. Los gráficos pueden (y deberían) ser atractivos visualmente, pero permiten que los datos se hablen por sí mismos.

- Evite skeumorphism, gráficos de barras fotográficas, almohadillas de contraste y otros toques de infografía.

- No utilice efectos 3D como elemento decorativo. Úselos solo si son realmente integrales para la capacidad del usuario de comprender la información.

- Evite el uso de varias líneas y rellenos, ya que más de dos colores pueden dificultar la lectura y la interpretación de este tipo de gráfico.

- No utilice un gráfico (ni ninguna ilustración) como el único medio para comprender un concepto o interactuar con los datos. Esto presenta dificultades para los usuarios con discapacidades visuales.

- No utilice gráficos como elementos innormales o decorativos en una página. En otras palabras, si un gráfico no agrega ningún valor o ayuda a los usuarios a resolver un problema, no lo utilice.

### <a name="chart-types"></a>Tipos de gráficos
 Los tipos de gráficos que se usan en Visual Studio incluyen gráficos de barras, gráficos de líneas, gráficos circulares modificados denominados gráficos de anillos o gráficos de anillos, escalas de tiempo, gráficos de dispersión (también denominados "gráficos de clúster") y diagramas de Gantt. Cada tipo de gráfico resulta útil para comunicar un tipo diferente de información.

### <a name="other-charting-considerations"></a>Otras consideraciones sobre gráficos

#### <a name="color"></a>Color
 Hay una paleta específica de colores de gráficos definidos para su uso en Visual Studio. La paleta es accesible para los principales tipos de ceguera de color y los colores se pueden diferenciar incluso cuando se usan como segmentos de color muy estrechos. Puede usar estos colores en cualquier combinación para cualquier tipo de gráfico o gráfico de la interfaz de usuario. No es necesario usar los siete colores si no se necesitan muchos colores distintos. Estos colores no se diseñaron para usarse con elementos de primer plano, por lo que no debe colocar texto ni glifos encima de estos colores. Estas tonalidades deben estar codificadas de forma rígida y expuestas a la personalización del usuario en **herramientas > opciones** (consulte [exposición de colores para usuarios finales](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)).

|Muestra|Hex|RGB|
|------------|---------|---------|
|![Muestra 71B252](../../extensibility/ux-guidelines/media/0711_71b252.png "0711_71B252")|#71B252|113178, 82|
|![Muestra BF3F00](../../extensibility/ux-guidelines/media/0711_bf3f00.png "0711_BF3F00")|#BF3F00|191, 63, 0|
|![Muestra FCB714](../../extensibility/ux-guidelines/media/0711_fcb714.png "0711_FCB714")|#FCB714|252183, 20|
|![Muestra 903F8B](../../extensibility/ux-guidelines/media/0711_903f8b.png "0711_903F8B")|#903F8B|144, 63139|
|![Muestra 117AD1](../../extensibility/ux-guidelines/media/0711_117ad1.png "0711_117AD1")|#117AD1|17.122.209|
|![Muestra 79D7F2](../../extensibility/ux-guidelines/media/0711_79d7f2.png "0711_79D7F2")|#79D7F2|121.215.242|
|![Muestra B5B5B5](../../extensibility/ux-guidelines/media/0711_b5b5b5.png "0711_B5B5B5")|#B5B5B5|181.181.181|

## <a name="on-object-ui-and-peeking"></a><a name="BKMK_OnObjectUI"></a> Interfaz de usuario y inspección de objetos en el objeto
 En esta sección se proporciona un contexto para la inspección, también conocido como vista de código PEEK, un tipo de interfaz de usuario en el objeto única de Visual Studio.

### <a name="overview"></a>Información general

- La interfaz de usuario en el objeto debe proporcionar más información o interactividad al usuario sin destraerse de su tarea principal.

- El patrón principal para la interfaz de usuario en el objeto en Visual Studio se conoce como "información en el punto de atención".

- La interfaz de usuario en el objeto de Visual Studio es insertada o flotante, o bien duradera o transitoria.

  - La vista de lectura de código, un tipo de interfaz de usuario en el objeto en Visual Studio, es inline y duradera.

  - Codelens, un tipo de interfaz de usuario en el objeto en Visual Studio, es flotante y transitoria

  Entender cómo funciona un fragmento de código o buscar detalles sobre el código, a menudo requiere que un programador cambie de contexto y vaya a otro contenido u otra ventana. Estos cambios de contexto pueden ser perjudiciales, ya que los usuarios pueden perder el foco en su tarea original si salen de la ventana principal. Además, la obtención del contexto original puede ser difícil, especialmente si el cambio de Windows hizo que el código original estuviera oculto por otra interfaz de usuario.

  La interfaz de usuario en el objeto sigue un patrón denominado "información en el punto de atención". Estos mensajes, ventanas emergentes y cuadros de diálogo proporcionan a los usuarios información adicional relevante que agrega aclaración o interactividad sin perder el foco en su tarea principal. Entre los ejemplos de interfaz de usuario en objeto se incluyen ventanas emergentes que aparecen cuando un usuario mantiene el puntero sobre un icono en el área de notificación, el subrayado ondulado de color rojo bajo una palabra mal escrita y la vista de inspección presentada en Visual Studio 2013.

### <a name="decision-points"></a>Puntos de decisión
 En Visual Studio, hay varias maneras de usar este patrón de información en el momento de la atención. Elegir el mecanismo adecuado e implementarlo de forma coherente y predecible es esencial para la experiencia general. De lo contrario, los usuarios podrían presentar una experiencia confusa o incoherente que distrae el foco del contenido en sí.

#### <a name="relationships-between-master-and-detail-content"></a>Relaciones entre el contenido maestro y los detalles
 La información en el momento de la atención se usa para mostrar una relación entre el contenido en el que se centra el usuario (el contenido "principal") y el contenido relacionado adicional (el contenido de "detalle"). En este patrón, el contenido detallado está claramente relacionado con el contenido con el que está trabajando el usuario y se puede mostrar cerca del contenido maestro. La información adicional o la información que no se puede resumir sin saturar el contenido maestro debe seguir otro patrón, como una ventana de herramientas.

- Muestre **siempre** el contenido de detalle cerca del contenido maestro.

- Asegúrese **siempre** de que el contenido de detalle todavía permita que un usuario permanezca centrado en el contenido maestro. A menudo, la mejor manera de lograrlo es presentar el contenido de detalle lo más cerca posible del contenido maestro. Esto se puede hacer representando el contenido de detalle en una ventana emergente situada junto al contenido maestro o representando el contenido de detalle alineado debajo del contenido maestro.

- No utilice **nunca** información en el momento de la atención que le lleve al usuario del contenido maestro. Si los usuarios necesitan ver el contenido de detalle por separado, exponga una acción explícita que permita al usuario hacerlo.

#### <a name="design-details"></a>Detalles de diseño
 Una vez que haya determinado que la interfaz de usuario en el objeto es la opción correcta, hay cuatro consideraciones de diseño principales:

1. **Persistencia:** ¿se espera que el contenido sea duradero o transitorio?
   ¿Los usuarios quieren mantener la información visible para hacer referencia a ella o interactuar con ella? ¿O los usuarios quieren ver rápidamente la información y continuar con su tarea principal?

2. **Tipo de contenido:** ¿el contenido será informativo, accionable o de navegación?
   ¿Necesita el usuario información adicional sobre el contenido maestro? ¿El usuario necesita completar una tarea que afecte al contenido maestro? ¿O el usuario debe ser dirigido a otro recurso?

3. **Tipo de indicador:** ¿tiene sentido un indicador de ambiente?
   ¿Se puede resumir la información de una manera útil y mostrarla sin saturar el contenido maestro?

4. **Gestos:** ¿qué gestos se usarán para invocar y descartar la interfaz de usuario?
   ¿Cómo mostrará el usuario el contenido de detalle y lo enviará? ¿Hay algún valor al agregar un gesto, como anclar para cambiar entre Estados transitorios y duraderos?

   Cada uno de estos cuatro puntos de decisión afectará a los componentes principales de la interfaz de usuario en el objeto.

### <a name="on-object-ui-components"></a>Componentes de interfaz de usuario en el objeto

1. Tipo de contenedor (presentador de contenido)

    - Flotante

    - En línea

2. Tipo de contenido

    - Información: datos que pueden ser estáticos o dinámicos

    - Accionable: comandos que cambian el contenido maestro

    - Navegación: vínculos que llevan al usuario a otra ventana o aplicación, como MSDN

3. Gestos

    - Invocación

    - Descartado

    - Anclaje

    - Otras interacciones

4. Modelo de persistencia y confirmación

    - Transitorio

    - Duradero

    - Automático

    - A petición

5. Indicadores de ambiente (opcional)

    - Subrayado ondulado

    - Icono de etiqueta inteligente

    - Otros indicadores ambientales

#### <a name="container-content-presenter-type"></a>Tipo de contenedor (presentador de contenido)
 Hay dos opciones principales disponibles para presentar el contenido en el punto de atención:

1. En **línea:** un presentador alineado, como la vista de búsqueda que se presentó en el editor de código Visual Studio 2013, hace que el contenido nuevo se desplace por el contenido existente.

    - **Prefiere** los presentadores en línea si espera que los usuarios deseen dedicar una cantidad considerable de tiempo a hacer referencia al contenido que tiene o interactuar con él.

    - **Evite** la presencia de moderadores en línea si espera que los usuarios quieran echar un vistazo a la información que presenta y luego continúe con su tarea principal con una interrupción mínima.

2. **Flotante:** un presentador flotante se coloca lo más cerca posible del contenido seleccionado, pero no modifica el diseño del contenido existente. Se pueden emplear varias estrategias, como mostrar un panel de contenido flotante sobre el espacio en blanco disponible más cercano al símbolo seleccionado.

    - **Prefiere** los presentadores flotantes si espera que los usuarios quieran echar un vistazo a la información que presenta y luego continuar con su tarea principal con una interrupción mínima.

    - **Evite** los presentadores flotantes si espera que los usuarios deseen dedicar una cantidad considerable de tiempo a hacer referencia a él o interactuar con él.

#### <a name="content-type"></a>Tipo de contenido
 Hay tres tipos principales de contenido que se pueden mostrar en cualquier contenedor de interfaz de usuario de objeto. Se puede mostrar cualquier combinación de estos tipos de información. Los tres tipos son:

1. **Información:** la mayoría de los contenedores de la interfaz de usuario de objetos mostrarán algún tipo de contenido informativo. El contenido puede representar información sobre el estado actual del entorno o puede representar información sobre un posible estado futuro del entorno. Por ejemplo, podría usarse para mostrar el efecto de un comando determinado, como una refactorización, en el código existente.

    - Use **siempre** la representación canónica de la información que se muestra. Por ejemplo, el código debe ser similar a código, completo con resaltado de sintaxis y debe respetar cualquier fuente y otra configuración de entorno establecida por el usuario.

    - Considere **siempre** la posibilidad de admitir cualquier acción sobre el contenido informativo que sea posible si la misma información se presenta como contenido maestro. Por ejemplo, si se presenta el código existente dentro de un contenedor de interfaz de usuario de objeto, considere la posibilidad de admitir la capacidad de examinar y modificar ese código.

    - Considere **siempre** usar un color de fondo diferente si presenta contenido informativo que representa un posible estado futuro.

2. Accionable: algunos contenedores de IU en objetos proporcionarán la capacidad de realizar alguna acción sobre el contenido maestro, como realizar una operación de refactorización.

    - Coloque **siempre** los comandos que se puedan accionar de forma independiente del contenido informativo.

    - Habilite y deshabilite **siempre** las acciones cuando sea necesario.

    - **Siempre** consulte las directrices estándar para representar comandos dentro de cuadros de diálogo.

    - Mantenga **siempre** el número de acciones que se exponen en un contenedor de interfaz de usuario de un objeto en un mínimo absoluto. La interacción con la interfaz de usuario en el objeto debe ser una experiencia ligera y rápida. El usuario no debe tener que dedicar energía a administrar el propio contenedor de la interfaz de usuario en el objeto.

    - **Siempre** debe tener en cuenta cómo y cuándo se cerrará o descartará un contenedor de interfaz de usuario de objeto. Como procedimiento recomendado, cualquier acción que concluye el cuadro de diálogo entre el contenido maestro y el contenido de detalle también debe cerrar el contenedor de la interfaz de usuario en el objeto cuando se invoca la acción.

3. **Navegación:** algunos contenedores de IU en objetos incluyen vínculos que llevan al usuario a otra ventana o aplicación, como abrir un artículo de MSDN en el explorador Web del usuario.

    - Anteponga **siempre** cualquier vínculo de navegación con "abierto" para que los usuarios no se sorprendan al navegar a otro contenido.

    - **Siempre** separe los vínculos de navegación de los vínculos que se puedan accionar.

#### <a name="ambient-indicators-optional"></a>Indicadores de ambiente (opcional)
 Los indicadores ambientales pueden ser sutiles, incluido el texto presentado en un color de contraste del resto del código, o obvio, incluidos símbolos tickler, como subrayados en zigzag y iconos de etiqueta inteligente. Los indicadores ambientales comunican la disponibilidad de información adicional pertinente. Idealmente, proporcionan información útil incluso sin necesidad de que el usuario interactúe con ellos.

- Coloque **siempre** un indicador de ambiente para que no distraiga o desbordado al usuario. Si no es posible colocar un indicador de ambiente de este modo, considere otra solución.

- Coloque **siempre** el indicador de ambiente lo más cerca posible del contenido con el que está relacionado.

- Intente crear **siempre** un indicador que resume la información que está disponible. Considere la posibilidad de proporcionar un recuento del número de elementos de datos disponibles (por ejemplo, "3 referencias" en lugar de simplemente "referencias") o piense en alguna otra manera de resumir los datos.

  - En los casos en los que los datos de un indicador no se pueden calcular y mostrar inmediatamente, considere la posibilidad de proporcionar comentarios progresivos a medida que se calculan los valores. Por ejemplo, considere la posibilidad de animar los cambios que reflejan las actualizaciones de los datos disponibles, de manera similar a la forma en que se actualiza el icono de correo electrónico activo en Windows Phone a medida que aumenta el número de correos electrónicos no leídos.

- **Nunca** agregue más indicadores de los que un usuario puede asumir razonablemente para un fragmento de contenido determinado. Los indicadores ambientales deben ser útiles sin requerir ninguna interacción del usuario. Los indicadores pierden su ambiente si requieren desbordamiento y otros controles de administración para mostrarlos.

#### <a name="gestures"></a>Gestos
 Un aspecto clave de permitir al usuario mantener el foco en el contenido maestro es admitir los gestos correctos para abrir y descartar el contenido de detalle adicional.

- Pida **siempre** al usuario que realice algún gesto explícito para abrir el contenido adicional. Los gestos comunes de apertura incluyen:

  - **Mantener el mouse:** información sobre herramientas o contenido informativo no interactivo

  - **Comando explícito:** presentador alineado

  - **Haga doble clic en el indicador de ambiente:** Ventana emergente codelens

- Descartar **siempre** el contenido detallado siempre que el usuario presione la tecla ESC.

- Considere **siempre** el contexto de la interfaz de usuario en el objeto. En el caso de los presentadores de contenido que permiten la interacción dentro del contenedor, considere detenidamente si se debe mostrar información adicional sobre el desplazamiento, que es probable que sea perjudicial para el flujo de trabajo del usuario.

- **Nunca** muestre el contenido en el mantener el mouse que parezca ser editable o invite a la interacción del usuario. Este comportamiento puede frustrar a los usuarios si intentan trasladar el cursor sobre el contenido de detalle, ya que el comportamiento estándar para una información sobre herramientas es descartar inmediatamente cuando el cursor ya no está sobre el contenido maestro que lo generó.

## <a name="selection-models"></a><a name="BKMK_SelectionModels"></a> Modelos de selección

### <a name="overview"></a>Información general
 Un modelo de selección es el mecanismo que se usa para indicar y confirmar las operaciones en uno o varios objetos de interés dentro de la interfaz de usuario. En este tema se describen los patrones de interacción de selección en los editores de documentos de Visual Studio: editores de texto, superficies de diseño y superficies de modelado.

 Los usuarios deben tener una manera de indicar a Visual Studio en qué están trabajando y Visual Studio debe responder de forma predecible con los comentarios a los usuarios sobre su funcionamiento. Las diferencias o una comunicación incoherente entre el usuario y la interfaz de usuario pueden dar lugar a que el usuario no note una acción, lo que puede tener consecuencias imprevistas. A menudo, el error pasa desapercibido hasta que el usuario ve que falta algo o ha cambiado. Por lo tanto, los modelos de selección son una de las partes más importantes del diseño de la interfaz de usuario. Aunque los modelos de selección de Visual Studio son coherentes con Windows, hay ligeras variaciones.

 En Visual Studio, como en Windows, los modelos de selección difieren en función del contexto en el que se produce la interacción. Las selecciones pueden producirse en cuatro tipos de objetos:

- Texto

- Objetos gráficos

- Listas y árboles

- Cuadrículas

  Dentro de estos objetos, hay tres tipos de selecciones:

- Contiguo

- Separado

- Region

#### <a name="scope"></a>Ámbito
 El componente más importante de la selección es asegurarse de que el usuario sabe en qué ventana trabajan (activación) y dónde se encuentra el foco (selección). Visual Studio amplía la funcionalidad de administración de ventanas en Windows, pero el esquema de activación es el mismo: al interactuar con una ventana, el foco se centra en la ventana. Visual Studio tiene dos indicadores de activación: uno para las ventanas de documento y otro para las ventanas de herramientas.

 En las ventanas de documento, la ventana activa se indica mediante una pestaña de la ventana de documento que llega al principio y cambia su color de fondo:

 ![Selección de pestaña activa en Visual Studio](../../extensibility/ux-guidelines/media/0713-01_activetab.png "0713-01_ActiveTab")

 **Selección de la pestaña activa**

 En las ventanas de herramientas, la ventana activa se indica mediante un cambio en el color del área de la barra de título de la ventana de herramientas:

 ![Selección de ventana de herramientas activa en Visual Studio](../../extensibility/ux-guidelines/media/0713-02_activetoolwindow.png "0713-02_ActiveToolWindow")

 **Ventana de herramientas activa que muestra la selección primaria de un nodo**

 ![Selección de ventana de herramientas inactiva en Visual Studio](../../extensibility/ux-guidelines/media/0713-03_inactivetoolwindow.png "0713-03_InactiveToolWindow")

 **Ventana de herramientas inactiva, que muestra una selección latente de nodo**

 Una vez que una ventana está activa, su enfoque se indica según los modelos de selección descritos en esta sección de las instrucciones.

#### <a name="context"></a>Context
 Visual Studio se diseñó para conservar un concepto de contexto muy importante, realizando un seguimiento del lugar en el que está trabajando el usuario. Solo hay una ventana activa, ya sea una herramienta o una ventana de documento. Sin embargo, la ventana de documento de nivel superior siempre conserva una selección latente. Aunque el foco puede estar en una ventana de herramientas, la ventana de documento que estaba activa por última vez muestra una selección, incluso en un estado inactivo. Esto se hace para conservar el contexto del usuario en el documento que estaba editando, mostrándole que Visual Studio ha conservado su estado para que pueda devolver y desplazarse sin problemas entre ventanas de herramientas y ventanas de documento.

### <a name="text-selection"></a>Selección de texto
 Los editores de Visual Studio que son estrictamente texto, como el editor de texto integrado, usan el mismo modelo de selección de texto y la misma apariencia descritas en la página [punteros y punteros](/windows/desktop/uxguide/inter-mouse) de las instrucciones de interacción de la experiencia del usuario de Windows en MSDN. El foco de entrada en el editor de texto se indica mediante una barra vertical denominada punto de inserción. El punto de inserción es un solo píxel grueso y coloreado como el inverso de lo que aparece detrás. Parpadea según la tasa establecida por el valor de **velocidad de intermitencia del cursor** en la pestaña **velocidad** del applet de **teclado** en el panel de control.

#### <a name="contiguous-and-disjoint-selection"></a>Selección contigua y no conjunta
 La selección dentro del editor de texto solo es contigua. No se permiten selecciones de texto no contiguos, pero deben solucionarse en editores de objetos gráficos. Cuando el puntero del mouse del usuario está sobre un área de texto, el cursor cambia a un cursor. Un solo clic coloca el punto de inserción en el editor de texto en la ubicación de clics. Si mantiene presionado el botón del mouse, se inicia una selección resaltada y soltar el botón del mouse finaliza el resaltado de la selección.

#### <a name="region-selection-box-selection"></a>Selección de región (selección de cuadro)
 Visual Studio admite selecciones de región en el editor de texto y se llama selección de cuadro. La selección de cuadros permite al usuario seleccionar una región de texto que no sigue la secuencia de texto normal. Al igual que con la selección de texto estándar, la selección debe ser contigua. La selección de cuadros se inicia manteniendo presionada la tecla Alt mientras se arrastra con el mouse. La selección de cuadros también se puede iniciar manteniendo presionadas las teclas Alt y Mayús mientras usa las teclas de dirección para indicar el área de selección. La selección de cuadros usa el resaltado de selección normal y muestra el cursor de punto de inserción que parpadea al final del área de selección.

 ![Cuadro de &#40;regional&#41; selección en Visual Studio](../../extensibility/ux-guidelines/media/0713-04_boxselection.png "0713-04_BoxSelection")

 **Selección de región (cuadro) en Visual Studio**

#### <a name="text-selection-appearance"></a>Apariencia de la selección de texto
 Los colores que se usan para la selección activa e inactiva en el editor se pueden personalizar. Para personalizar el aspecto visual del editor, un usuario puede ir a **herramientas > opciones** y, a continuación, buscar en **entorno > fuentes y colores > editor de texto**.

### <a name="graphical-selection"></a>Selección gráfica

#### <a name="interaction"></a>Interacción
 La selección de objetos gráficos puede ser compleja y depende de una serie de factores:

- **El modelo de selección principal del editor.** Los editores que contienen objetos gráficos también se pueden usar para editar texto o cuadrículas. Por ejemplo, el editor puede ser un editor basado en texto que también admite la colocación de objetos gráficos, como el diseñador XAML de Visual Studio. La compatibilidad con varios tipos de objeto puede afectar al modo en que el usuario selecciona grupos que se componen de diferentes tipos de objetos.

- **Compatibilidad con los Estados de selección principal y secundaria.** Un editor puede proporcionar los Estados de selección principal y secundario para que los objetos se puedan editar en el unísono, se alineen entre sí, se cambie el tamaño juntos, etc.

- **Compatibilidad con la edición en contexto.** Los editores también pueden permitir la edición del contenido de sus objetos gráficos. Por ejemplo, una forma de rectángulo también puede contener texto en el interior que el usuario puede cambiar. Además, ese texto podría estar centrado o justificado. La edición en contexto implica un nivel más detallado de interacción con el usuario y, por tanto, requiere un conjunto adecuado de indicaciones visuales para presentar la información de estado al usuario.

#### <a name="mouse-interaction"></a>Interacción con el mouse

|Entrada|Resultado|
|-----------|------------|
|Haga clic en un objeto no seleccionado|Selecciona el objeto y muestra una línea discontinua y controladores de selección, si el objeto es ajustable.|
|Haga clic en un objeto seleccionado|Activa la edición en contexto si el objeto lo admite. Al hacer clic fuera del objeto, se desactiva el modo de edición en contexto.|
|Hacer doble clic en un objeto|Abre el código subyacente del objeto para editarlo y puede insertar un controlador de eventos predeterminado, si es necesario.|
|Apuntar a un objeto|Cambia el puntero al cursor de movimiento. La apariencia del objeto, como su luminosidad o color, podría cambiar.|
|Apuntar a un controlador de selección|Cambia el puntero al cursor de cambio de tamaño. En el caso de los objetos que admiten la rotación, algunos controladores de selección pueden cambiar el puntero a un cursor de giro, ya que el puntero se coloca de manera diferente (por ejemplo, se mueve más lejos) con respecto al controlador de selección.|
|Arrastrar|Incluso si el objeto no está seleccionado previamente, cambia el puntero al cursor de movimiento y mueve el objeto.|
|El editor pierde el foco|Desactiva el modo de edición en contexto, aunque el objeto conserva el contenido y la apariencia que tenía durante su último estado de operación o selección.|
|Selección de objetos|Indicado por un borde, una línea de puntos u otro tratamiento visualmente distinto para resaltar el límite del objeto.|
|Cambiar el tamaño de un objeto seleccionado|Indicado por los controladores de selección.<br /><br /> Un objeto de tamaño variable tiene ocho identificadores, que representan cada dirección en la que se puede cambiar el tamaño. Se pueden usar menos identificadores si el objeto solo se puede cambiar de tamaño en determinadas direcciones. Cuando el usuario ajusta el tamaño de un objeto hasta que ocho manipulaciones no serían interactivos, se pueden usar cuatro identificadores. Los tamaños de los identificadores deben estar vinculados a las métricas de borde y borde de la ventana con la función de la API **GetSystemMetrics** para el tamaño en proporción con la resolución de pantalla.<br /><br /> ![Controladores de tamaño](../../extensibility/ux-guidelines/media/0713-05_resizehandles.png "0713-05_ResizeHandles")|
|Girar un objeto seleccionado|![Controladores de giro](../../extensibility/ux-guidelines/media/0713-06_rotate.png "0713-06_Rotate")|

#### <a name="keyboard-interaction"></a>Interacción con el teclado

|Entrada|Resultado|
|-----------|------------|
|Pestaña|Mueve el indicador de foco entre el orden lógico de los objetos en el editor. Puede ser de izquierda a derecha o de arriba abajo, según el valor de propiedad **TabIndex** (o equivalente), el orden de creación de objetos y el propósito general del editor. Mayús + Tab invierte la dirección del indicador de foco.|
|Barra espaciadora|Activa el modo de movimiento panorámico mientras se mantiene pulsada la tecla. Se requiere una entrada adicional del mouse para desplazar la posición de la ventanilla.|
|Ctrl+Barra espaciadora|Activa el modo de zoom mientras se mantiene pulsada la tecla. Se requiere una entrada del mouse adicional para aumentar y disminuir el factor de zoom.|
|CTRL + ALT + signo menos|Reduce el factor de zoom en un nivel.|
|CTRL + ALT + signo más|Aumenta el factor de zoom en un nivel.|
|Mayús o Ctrl|Agrega el objeto al grupo de selección. Ctrl también permite quitar objetos individualmente del grupo de selección.|
|Escriba|Ejecuta el comando predeterminado para el objeto (normalmente, abrir o editar).|
|F2|Activa la edición en contexto para el objeto.|
|Teclas de dirección|Mueve los objetos seleccionados en la dirección de la tecla de dirección presionada, en incrementos pequeños (por ejemplo, 1 píxel a la vez)|
|Ctrl + teclas de dirección|Mueve los objetos seleccionados en la dirección de la tecla de dirección presionada, en incrementos mayores (por ejemplo, 10 píxeles a la vez)|
|Mayús + teclas de dirección|Cambia el tamaño de los objetos seleccionados en la dirección respectiva, en incrementos pequeños (por ejemplo, 1 píxel a la vez)|
|Ctrl + Mayús + teclas de dirección|Cambia el tamaño de los objetos seleccionados en la dirección respectiva, en incrementos mayores (por ejemplo, 10 píxeles a la vez)|

 Cuando los usuarios editan controles en su lugar, es posible que los objetos cambien de tamaño automáticamente con los datos proporcionados por el usuario. Por ejemplo, si el usuario modifica un control de etiqueta, la etiqueta debería aumentar para mostrar el texto que el usuario acaba de escribir. Si no se hace esto, el usuario debe cambiar el tamaño del control manualmente después de editar el texto. Si el usuario tiene muchos controles, esto se convierte en una tarea de gran grado de producción.

#### <a name="graphical-containers"></a>Contenedores gráficos
 En algunos casos, los Editores gráficos proporcionan contenedores para otros objetos gráficos, como el control de panel de Windows Forms o el control de diseño de cuadrícula en el diseñador HTML. Si el editor proporciona contenedores para otros objetos gráficos, se debe usar el siguiente modelo de selección solo para el contenedor (los objetos dentro del contenedor siguen el modelo estándar como se describió anteriormente):

|Entrada|Resultado|
|-----------|------------|
|Un solo clic en el contenedor|Selecciona el objeto contenedor sin seleccionar directamente ninguno de los objetos contenidos. Es posible que el contenedor se mueva o cambie de tamaño con la entrada estándar del mouse y del teclado (como se describió anteriormente). Los objetos contenidos se mueven en relación con el contenedor, pero no se cambia el tamaño de los objetos contenidos a menos que también se seleccionen directamente.|
|Desplazar el puntero sobre la región de límite del contenedor|Convierte el mouse en el cursor de movimiento, lo que indica que el contenedor puede moverse.|
|Arrastre la región de límite del contenedor|Cambia el mouse al cursor de movimiento y mueve el contenedor (y los objetos contenidos dentro). No se puede moverse el contenedor sin seleccionarse primero con un solo clic.|
|Un solo clic en un objeto dentro del contenedor|Anula la selección del contenedor (si se selecciona) y selecciona solo el objeto en el que se ha seleccionado.|
|Mayús + clic o Ctrl + clic en un objeto o contenedor contenido|Agrega el objeto al que se hace clic en un grupo de selección o selección existente. Si el objeto al que se hace clic ya es miembro del grupo de selección, se quita del grupo de selección.|

 Los objetos contenidos deben adherirse al modelo de selección básica, como se describe en la sección anterior. Desde las pruebas de facilidad de uso del diseñador de Windows Forms, los usuarios esperaban un acceso sin problemas a los objetos contenidos sin necesidad de realizar ningún paso (impuesto por el objeto de contención).

#### <a name="disjoint-and-region-selections"></a>Selecciones disjuntos y de región
 Los editores de objetos gráficos deben admitir selecciones discontinuas. Tenga en cuenta que en este gráfico no se muestra la apariencia del control para Visual Studio. Vea la [presentación de selección de objetos gráficos](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_GraphicalObjectSelectionAppearance) para obtener especificaciones visuales detalladas.

 ![Selectores de región y discontinuos](../../extensibility/ux-guidelines/media/0713-07_disjointregionselectors.png "0713-07_DisjointRegionSelectors")

 **Selección no conjunta**

 Los Editores gráficos también deben proporcionar selecciones de región con un indicador de selección de tipo de marquesina. Si el editor gráfico admite otros tipos de objeto (como texto), es posible que las selecciones de región no sean posibles en función de las restricciones de los demás tipos de objeto.

 ![Selección de recuadro](../../extensibility/ux-guidelines/media/0713-08_marqueeselection.png "0713-08_MarqueeSelection")

 **Selección de recuadro**

#### <a name="primary-and-secondary-selections"></a>Selecciones principales y secundarias
 Algunos editores de objetos gráficos permiten al usuario editar o Alinear objetos en grupos. En este caso, es necesario introducir el concepto de selecciones principales y secundarias. La selección principal es el objeto al que todos los demás objetos responden para las operaciones de grupo. El objeto que el usuario selecciona primero se convierte en el control principal y las selecciones subsiguientes se convierten en las selecciones secundarias. La selección principal tiene un tratamiento visual distintivo de las selecciones secundarias para indicar qué objeto es principal:

 ![Selección primaria y secundaria](../../extensibility/ux-guidelines/media/0713-09_primarysecondary.png "0713-09_PrimarySecondary")

 **Selección principal con dos selecciones secundarias**

#### <a name="graphical-object-selection-appearance"></a><a name="BKMK_GraphicalObjectSelectionAppearance"></a> Apariencia de selección de objetos gráficos
 Los controladores de selección son los cuadrados dibujados en un patrón rectangular alrededor del rectángulo de selección del objeto. En el gráfico siguiente se muestran ejemplos de los distintos Estados que un objeto gráfico puede tener con el control, el ajuste de tamaño y la apariencia de edición en contexto. El tamaño de los identificadores debe estar vinculado a las métricas de borde y borde de la ventana mediante la API de **GetSystemMetrics** .

| State | Aspecto | Detalles visuales |
|-------------------------|---------------| - |
| **No seleccionado** | Valor predeterminado | ![Estado de botón predeterminado](../../extensibility/ux-guidelines/media/0713-10_defaultstate.png "0713-10_DefaultState") |
| **Selección principal** | Tamaño | ![Selección primaria con controladores de tamaño](../../extensibility/ux-guidelines/media/0713-11_primaryresize.png "0713-11_PrimaryResize") |
| **Selección principal** | No redimensionable | ![Selección primaria sin controladores de tamaño](../../extensibility/ux-guidelines/media/0713-13_primarynoresize.png "0713-13_PrimaryNoResize") |
| **Selección principal** | Bloqueado | ![Selección primaria bloqueada](../../extensibility/ux-guidelines/media/0713-15_primarylocked.png "0713-15_PrimaryLocked") |
| **Selección secundaria** | Tamaño | ![Selección primaria con controladores de tamaño](../../extensibility/ux-guidelines/media/0713-17_secondaryresize.png "0713-17_SecondaryResize") |
| **Selección secundaria** | No redimensionable | ![Selección secundaria sin controladores de tamaño](../../extensibility/ux-guidelines/media/0713-19_secondarynoresize.png "0713-19_SecondaryNoResize") |
| **Selección secundaria** | Bloqueado | ![Selección secundaria bloqueada](../../extensibility/ux-guidelines/media/0713-21_secondarylocked.png "0713-21_SecondaryLocked") |
| **Interfaz de usuario activa** | Valor predeterminado | ![Estado activo de interfaz de usuario](../../extensibility/ux-guidelines/media/0713-23_uiactive.png "0713-23_UIActive") |

### <a name="view-selection-models"></a>Ver modelos de selección

#### <a name="tree-view"></a>Vista de árbol
 La selección en una vista de árbol se muestra con un resaltado simple. Si el usuario hace clic en un nombre de nodo o en un icono de nodo, se selecciona el nodo. Los glifos triangulares a la izquierda del nodo expanden o contraen el control de árbol, pero no afectan a la selección del usuario, con una excepción: al contraer un nodo primario cuando la selección está en un elemento secundario de ese nodo, la selección se mueve al elemento primario.

 ![Vista de árbol típica de Visual Studio](../../extensibility/ux-guidelines/media/0713-25_treeview.png "0713-25_TreeView")

 **Vista de árbol típica de Visual Studio**

 Las vistas de árbol pueden admitir selecciones contiguas y disjuntos, incluso en varios niveles del árbol. Se deben realizar selecciones contiguas o separadas en los nodos de árbol visibles. Si un nodo está contraído, la selección no conjunta se pierde y el nodo que se contrajo obtiene la selección. De esta manera, el usuario puede ver los nodos que se verán afectados por una operación. Cuando se contraen los nodos, deja de estar claro qué nodos podrían verse afectados.

 Cuando se selecciona un nodo primario, la operación se debe aplicar al elemento primario, aunque puede haber casos en los que tenga sentido que una operación se aplique al elemento primario y a todos sus elementos secundarios. En este caso, proporcione una interfaz de usuario adicional durante la operación, como una casilla o un cuadro de diálogo de confirmación para que la opción "aplicar a todos los elementos secundarios" sea explícita para el usuario.

##### <a name="renaming"></a>Cambiar nombre
 Si los nodos del árbol admiten el cambio de nombre, el cambio de nombre debe realizarse en su lugar. La operación en contexto debe ser el estándar en todos los controles de árbol de Visual Studio. Proporcione un comando Rename que Active inmediatamente el modo de edición en contexto, con la selección de texto que abarca el nombre completo del nodo, preparado para aceptar los datos proporcionados por el usuario. Si el nodo representa un archivo, el nombre de archivo debe contener la extensión. El resaltado de la selección solo debe incluir el cuerpo del nombre de archivo y no la extensión.

|Entrada|Resultado|
|-----------|------------|
|Entrar (tecla)|Confirma la operación de cambio de nombre|
|Tecla ESC|Cancela la operación de cambio de nombre.|
|Hacer clic fuera de la región de edición en contexto|Confirma la operación de cambio de nombre|
|Deshacer|Deshacer sencillo para cancelar la operación de cambio de nombre|

#### <a name="selection-within-lists-and-grid-controls"></a>Selección en listas y controles de cuadrícula
 El concepto clave en la selección de lista es que se basa en filas, lo que significa que cuando se hace una selección, se selecciona toda la fila como una unidad. Por el contrario, las cuadrículas pueden permitir seleccionar celdas específicas sin que ello afecte a ningún otro aspecto de la fila. Las cuadrículas también pueden contener una jerarquía de filas anidadas (como en un TreeGrid) que permiten seleccionar y anular la selección de todas las ramas de la jerarquía mediante la interacción con las filas primarias. La selección en las listas se muestra mediante un color de resaltado simple en toda la fila de datos. El foco se muestra mediante un borde de puntos de un solo píxel alrededor de la fila o celda modificable actual (fila si todas las celdas son de solo lectura).

> [!NOTE]
> El **foco** y la **selección** son conceptos diferentes. El *foco* es una indicación de qué elemento de la interfaz de usuario está destinada a recibir la entrada no dirigida explícitamente a otro objeto, mientras que la *selección* hace referencia al estado de la inclusión de un objeto en un conjunto de objetos en el que pueden tener lugar las operaciones posteriores.

 Las selecciones de las listas pueden ser contiguas, disjuntas o regiones. Cuando se permiten selecciones múltiples, siempre se admite la selección contigua y separada, mientras que la compatibilidad con las selecciones de región (cuadro) es opcional. Las selecciones de región se inician arrastrando en el espacio en blanco del cuerpo de la lista.

| Object | Selección |
|--------|------------|
| Lista | Contiguo |
| Lista | Separado |
| Lista | Region |

 Al hacer clic en una vez en una lista, se selecciona la fila en la que se hizo clic. Si el usuario hace clic en una celda de la lista que admite la edición en contexto, la celda también se activa inmediatamente para la edición en contexto. De lo contrario, se selecciona la fila completa de inmediato y se muestra un resaltado.

 Al arrastrar en el cuerpo de la lista, se realiza una de estas tres acciones:

- Inicia una selección de región si la lista lo admite y el mouse está en el espacio en blanco

- Inicia una operación de arrastrar y colocar si la celda o fila de la lista admite un origen de arrastre.

- Selecciona la fila actual

##### <a name="in-place-editing"></a>Edición en contexto
 Cuando se permite la edición en contexto, hay dos modelos básicos: control de edición simple y selector de propiedades. Con un control de edición simple, el contenido se resalta y está listo para la entrada del usuario en cuanto se activa la edición en contexto. Cuando se implementa un selector de propiedades, el botón que invoca al selector de propiedades se muestra una vez que se activa el modo de edición en contexto y no se resalta la selección actual. El botón selector debe estar justificado a la derecha en la celda. Para ver ejemplos de edición en contexto, vea la **ventana Propiedades** y **lista de tareas** en Visual Studio.

##### <a name="keyboard-support"></a>Compatibilidad con el teclado
 La compatibilidad con el teclado para la selección en listas y cuadrículas sigue las convenciones estándar de Windows:

- Las teclas de dirección navegan por la lista, seleccionando cada fila o celda a medida que se mueve el foco.

- Mayús + Flecha realiza una selección contigua en la dirección de las teclas de dirección.

- Ctrl + flecha seguido de la barra espaciadora alterna entre agregar y quitar elementos de lista de la selección, creando una selección no conjunta.

- En las cuadrículas que contienen jerarquías anidadas, la tecla de flecha derecha expande una fila primaria y la tecla de flecha izquierda contrae una.

- La tecla TAB mueve el foco entre las celdas de la fila actual si las celdas son editables.

- La tecla entrar realiza el comando predeterminado en el elemento de la lista (a menudo **abierto**).

- La tecla F2 activa la edición en contexto para la celda seleccionada actualmente.

## <a name="persistence-and-saving-settings"></a><a name="BKMK_PersistenceAndSavingSettings"></a> Persistencia y guardado de la configuración

### <a name="overview"></a>Información general
 Aunque cada componente de software de Visual Studio suele ser responsable de su propio estado y persistencia, Visual Studio guarda automáticamente la configuración en algunos casos, como los tamaños y las posiciones de las ventanas. La tabla siguiente es una combinación de opciones de configuración guardadas automáticamente y configuraciones que requieren que se lleve a cabo un usuario explícito o una acción programada.

|Object|Qué se debe guardar|Cuándo guardar|Dónde guardar|
|------------|------------------|------------------|-------------------|
|Objeto seleccionable (por ejemplo, una línea de código)|Un punto de interrupción en una línea de código<br /><br /> Un acceso directo de usuario asociado a la línea de código|Cuando se guarda el proyecto|El archivo de **Opciones de usuario (. suo)** del proyecto|
|Diálogo|Ubicación del cuadro de diálogo, si se ha cambiado.<br /><br /> La vista que el usuario utilizó por última vez en el cuadro de diálogo|Cuando se cierre el cuadro de diálogo<br /><br /> Cuando finaliza la sesión de Visual Studio|En memoria<br /><br /> Registro en **HKEY_Current_User**|
|Periodo|El tamaño y la ubicación de la ventana|Cuando se cierra la ventana<br /><br /> Cuando cambia el modo de Visual Studio<br /><br /> Cuando finaliza la sesión de Visual Studio|El archivo de **Opciones de usuario (. suo)** del proyecto<br /><br /> Archivo de opciones personalizadas para la configuración de la ventana|
|Documento|La selección actual en el documento<br /><br /> Vista del documento<br /><br /> Los últimos puntos visitados por el usuario|Cuando se guarda el documento|El archivo de **Opciones de usuario (. suo)** del proyecto|
|Proyecto|Referencias a archivos<br /><br /> Referencias a directorios en disco<br /><br /> Referencias a otro software<br /><br /> Componentes<br /><br /> Información de estado sobre el propio proyecto|Cuando se guarda el proyecto|El archivo del proyecto|
|Solución|Referencias a proyectos<br /><br /> Referencias a archivos|Cuando se guarda el proyecto o la solución|El archivo de **solución (. sln)**|
|Configuración en **herramientas > opciones**|Personalizaciones de teclado<br /><br /> Personalizaciones de la barra de herramientas<br /><br /> Esquemas de colores|Cuando se cierra el cuadro de diálogo **herramientas > opciones**<br /><br /> Cuando finaliza la sesión de Visual Studio|Registro en **HKEY_Current_User**|

 Lo que hace el usuario y, cuando lo hace, indica si un valor se guarda en memoria (durante la sesión), se guarda en el disco (entre las sesiones como una configuración del registro), como parte del archivo de proyecto o de solución, como parte del archivo de **Opciones de solución (. suo)** o como un archivo de configuración personalizado que solo el componente de software conoce. En la tabla anterior se muestran varios eventos en los que se pueden guardar los valores de configuración. Sin embargo, hay otras horas en las que puede que desee guardar el estado:

- Cuando el usuario cambia la ubicación dentro de un cuadro de diálogo o una ventana

- Cuando el usuario transfiere el foco a otra ventana

- Cuando el usuario cambia de diseño al modo de depuración

- Cuando el usuario cierra la sesión de su cuenta

- Cuando el equipo entra en hibernación o se apaga

- Cuando el equipo o disco duro está a punto de volver a formatearse y configurarse de nuevo

### <a name="window-configurations"></a>Configuraciones de ventanas
 Una configuración de ventana es la presentación básica del entorno de desarrollo; es un esquema que consta de la lista de ventanas de herramientas y la manera en que se organizan. Para Windows administrado por el IDE (Windows IDE), la información de diseño se conserva por usuario, de modo que cuando un usuario inicia el IDE, el diseño de la ventana es el mismo que cuando salió por última vez en Visual Studio. El estado y la posición de las ventanas del IDE se guardan en un archivo de opciones personalizado en formato XML. Las ventanas de herramientas creadas por paquetes cargados en el IDE conservan su información de estado en el registro y pueden ser o no por usuario.

#### <a name="profile-specific-layouts"></a>Diseños específicos de perfiles
 Cada perfil incluye diseños de ventanas de herramientas, organizados de una forma familiar para los roles de desarrollador específicos (Visual C++ los desarrolladores esperan ver el **Explorador de soluciones** en el lado izquierdo del IDE, mientras que los desarrolladores de C# esperan ver el **Explorador de soluciones** a la derecha). Los diseños de ventana específicos del perfil se cargan después de que el usuario elija un perfil en el inicio. El autor de un paquete debe determinar el diseño de la ventana que sea más adecuado para la experiencia del cliente, sabiendo que los cambios que realice el usuario en la configuración de la ventana se conservarán.

## <a name="touch-input"></a><a name="BKMK_TouchInput"></a> Entrada táctil
 Los usuarios utilizan cada vez más productos de desarrollo de Microsoft en dispositivos táctiles. Sin embargo, existen barreras que dificultan el uso de las herramientas de desarrollo en dispositivos táctiles. Los usuarios esperarán que nuestros productos proporcionen una experiencia táctil confiable y precisa. La intención de estas instrucciones es informar de las decisiones sobre qué capacidades táctiles incorporar y para fomentar una experiencia de toque coherente en Visual Studio y en los productos relacionados.

### <a name="levels-of-experience"></a>Niveles de experiencia
 Los siguientes niveles de experiencia están diseñados para servir como guía para ayudar a los equipos a decidir qué capacidades táctiles ofrecer en función de su nivel deseado de interés de inversión en contacto.

- La **experiencia básica** es para los equipos que desean proporcionar capacidades táctiles, por lo que no hay extremos muertos a lo largo de su trabajo.

- La **experiencia optimizada** es para los equipos que desean proporcionar las capacidades táctiles más comunes (por ejemplo, las que normalmente están disponibles en aplicaciones de explorador de Internet).

- La **experiencia elevada** es para los equipos que desean agregar funcionalidades como gestos u otras funcionalidades opcionales que pueden hacer que su aplicación sea más fácil de usar.

||Experiencia básica|Experiencia optimizada|Experiencia elevada|
|-|----------------------|--------------------------|-------------------------|
|**Permite a los usuarios...**|Corrección del código y la lectura de soluciones/proyectos sin extremos inactivos|Realizar tareas de mantenimiento, refactorización y navegación|Trabaje en una experiencia coherente, intuitiva y fluida con confianza|
|**Editor**|Movimiento y selección táctiles<br /><br /> Touch ScrollBar para saltar y presionar + arrastrar|Zoom de alejar<br /><br /> Desplazamiento rápido<br /><br /> Selección<br /><br /> Uso sencillo del menú contextual||
|**Principales ventanas de herramientas**|Mostrar panorámica<br /><br /> Selección de elementos<br /><br /> Touch ScrollBar para saltar y presionar + arrastrar|Desplazamiento y selección de elementos fáciles||
|**Basado en ventanas**||Cambiar el tamaño de la ventana<br /><br /> Acceso rápido||
|**Cuadro de documento**||Navegación sencilla entre archivos abiertos||
|**Gestos**||Asegurarse de que los gestos comunes funcionan en el IDE|Acciones basadas en gestos<br /><br /> Compatibilidad con arrastrar y colocar y diseñadores|
|**Otras consideraciones**|||Teclado en pantalla personalizado|

#### <a name="gestures"></a>Gestos
 Los gestos proporcionan a los usuarios un acceso directo a los comandos que, de otro modo, podrían requerir una interacción más complicada. Consulte las instrucciones de Windows sobre los [gestos táctiles comunes de las aplicaciones de escritorio](/windows/desktop/wintouch/windows-touch-gestures-overview)y siga estas instrucciones para la mayoría de los gestos, incluidos gestos simples como la panorámica y el zoom.
