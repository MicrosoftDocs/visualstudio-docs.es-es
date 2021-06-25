---
title: Patrones compuestos para Visual Studio | Microsoft Docs
description: Obtenga información sobre patrones compuestos importantes para la coherencia en Visual Studio. Los patrones compuestos combinan elementos de interacción y diseño.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: e48ecfb2-f4b5-4d3a-b4a2-7a4d62fa4ec0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b8b84baa7be7449b8edb6241e415fc90c9acd594
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901427"
---
# <a name="composite-patterns-for-visual-studio"></a>Patrones compuestos para Visual Studio
Los patrones compuestos combinan elementos de interacción y diseño en configuraciones distintas. Algunos de los patrones compuestos más importantes en Visual Studio con respecto a la coherencia incluyen:

- [Visualización de datos](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_DataVisualization)

- [Interfaz de usuario en objeto y visualización](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

- [Modelos de selección](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

- [Persistencia y guardado de la configuración](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

- [Entrada táctil](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)

## <a name="data-visualization"></a><a name="BKMK_DataVisualization"></a> Visualización de datos

### <a name="overview"></a>Información general
 Los gráficos son una manera visual de agregar y visualizar datos para mejorar la toma de decisiones. Pueden ayudar a los usuarios a enfrentarse a una gran cantidad de datos, pero poco significa ver lo que merece atención y lo que podría necesitar una acción.

 El usuario se beneficiará de un gráfico si se cumple alguna de las condiciones siguientes:

- ¿El gráfico ayudará a los usuarios a identificar las tareas en las que pueden actuar?

- ¿Permitirá el gráfico a los usuarios prever las consecuencias de posibles cambios?

- ¿El gráfico ayudará a los usuarios a detectar tendencias e identificar patrones?

- ¿Permitirá el gráfico a los usuarios tomar mejores decisiones?

- ¿El gráfico ayudará a responder a una pregunta específica que los usuarios puedan tener en el contexto dado?

#### <a name="general-rules-for-charts"></a>Reglas generales para gráficos

- Etiquete claramente los datos. Las ilustraciones sin explicación son simplemente imágenes bastantes.

- Inicie los ejes en cero para evitar la asimetría de proporciones. La longitud de línea y el tamaño de la barra son indicaciones visuales importantes para comprender las relaciones entre los puntos de datos.

- Crear gráficos, no infografías. Las infografías son representaciones gráficas de datos y su objetivo principal es la narración visual. Los gráficos pueden (y deben) ser visualmente atractivos, pero dejar que los datos hablen por sí mismos.

- Evite el skeumorphism, los gráficos de barras gráficas, las marcas hash de contraste y otros toques infográficos.

- No use efectos 3D como elemento decorador. Úsenlos solo si realmente son integrales para la capacidad del usuario de comprender la información.

- Evite el uso de varias líneas y rellenos, ya que más de dos colores pueden hacer que este tipo de gráfico sea difícil de leer e interpretar correctamente.

- No use un gráfico (ni ninguna ilustración) como único medio para comprender un concepto o interactuar con los datos. Esto presenta dificultades para los usuarios con discapacidades visuales.

- No use gráficos como elementos gratuitos o decorados en una página. En otras palabras, si un gráfico no agrega ningún valor o ayuda a los usuarios a resolver un problema, no lo use.

### <a name="chart-types"></a>Tipos de gráfico
 Los tipos de gráficos usados en Visual Studio incluyen gráficos de barras, gráficos de líneas, un gráfico circular modificado conocido como gráfico circular o "gráfico de anillos", escalas de tiempo, gráficos de dispersión (también denominados "gráficos de clúster") y gráficos de Gantt. Cada tipo de gráfico es útil para comunicar un tipo de información diferente.

### <a name="other-charting-considerations"></a>Otras consideraciones de gráficos

#### <a name="color"></a>Color
 Hay una paleta específica de colores de gráficos definidos para su uso en Visual Studio. La paleta es accesible para los principales tipos de celo de color y los colores se pueden diferenciar incluso cuando se usan como segmentos de color muy estrechos. Puede usar estos colores en cualquier combinación para cualquier tipo de gráfico o gráfico en la interfaz de usuario. No es necesario usar los siete colores si no necesita tantos colores distintos. Estos colores no se diseñaron para usarse con ningún elemento de primer plano, por lo que no coloque texto ni glifos encima de estos colores. Estos matiz deben estar codificados de forma definida y exponerse a la personalización del usuario en **Herramientas > opciones** (consulte Exposición de colores para los usuarios [finales).](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)

|Muestra|Hex|RGB|
|------------|---------|---------|
|![Muestra 71B252](../../extensibility/ux-guidelines/media/0711_71b252.png "0711_71B252")|#71B252|113,178,82|
|![Muestra BF3F00](../../extensibility/ux-guidelines/media/0711_bf3f00.png "0711_BF3F00")|#BF3F00|191,63,0|
|![Muestra FCB714](../../extensibility/ux-guidelines/media/0711_fcb714.png "0711_FCB714")|#FCB714|252,183,20|
|![Muestra 903F8B](../../extensibility/ux-guidelines/media/0711_903f8b.png "0711_903F8B")|#903F8B|144,63,139|
|![Muestra 117AD1](../../extensibility/ux-guidelines/media/0711_117ad1.png "0711_117AD1")|#117AD1|17,122,209|
|![Muestra 79D7F2](../../extensibility/ux-guidelines/media/0711_79d7f2.png "0711_79D7F2")|#79D7F2|121,215,242|
|![Muestra B5B5B5](../../extensibility/ux-guidelines/media/0711_b5b5b5.png "0711_B5B5B5")|#B5B5B5|181,181,181|

## <a name="on-object-ui-and-peeking"></a><a name="BKMK_OnObjectUI"></a> Interfaz de usuario en objeto y visualización
 En esta sección se proporciona contexto para ver, también conocido como vista de vista de código, un tipo de interfaz de usuario en objeto única para Visual Studio.

### <a name="overview"></a>Información general

- La interfaz de usuario en objeto debe proporcionar al usuario más información o interactividad sin desatraer su tarea principal.

- El patrón principal de la interfaz de usuario en Visual Studio se conoce como "información en el punto de atención".

- La interfaz de usuario en Visual Studio es inserta o flotante y es duradera o transitoria.

  - La vista de vista de código, un tipo de interfaz de usuario en Visual Studio, es insertada y duradera.

  - CodeLens, un tipo de interfaz de usuario en objeto Visual Studio, es flotante y transitorio.

  Comprender cómo funciona un fragmento de código o buscar detalles sobre ese código, a menudo requiere que un desarrollador cambie de contexto y vaya a otro contenido u otra ventana. Estos cambios de contexto pueden ser perjudiciales, ya que los usuarios pueden perder el foco en su tarea original si abandonan su ventana principal. Además, recuperar ese contexto original puede ser difícil, especialmente si el cambio de ventanas provoca que otra interfaz de usuario oculte su código original.

  La interfaz de usuario en objeto sigue un patrón denominado "información en el punto de atención". Estos mensajes, ventanas emergentes y cuadros de diálogo dan a los usuarios información adicional y pertinente que agrega aclaración o interactividad sin perder el foco en su tarea principal. Algunos ejemplos de interfaz de usuario en objeto son las ventanas emergentes que aparecen cuando un usuario mantiene el puntero sobre un icono en el área de notificación, el subrayado ondulado rojo bajo una palabra mal escrita y la vista de vista previa introducida en Visual Studio 2013.

### <a name="decision-points"></a>Puntos de decisión
 Dentro Visual Studio, hay varias maneras de usar este patrón de información en el punto de atención. Elegir el mecanismo adecuado e implementarlo de una manera coherente y predecible es esencial para la experiencia general. De lo contrario, es posible que a los usuarios se les presente una experiencia confusa o incoherente que resta importancia al propio contenido.

#### <a name="relationships-between-master-and-detail-content"></a>Relaciones entre el contenido maestro y el contenido detallado
 La información en el punto de atención se usa para mostrar una relación entre el contenido en el que se centra el usuario (el contenido "maestro") y el contenido relacionado adicional (el contenido "detallado"). En este patrón, el contenido detallado está claramente relacionado con el contenido con el que el usuario está trabajando y se puede mostrar cerca del contenido maestro. La información complementaria o la información que no se puede resumir sin desbordar el contenido maestro debe seguir otro patrón, como una ventana de herramientas.

- **Muestre** siempre el contenido detallado cerca del contenido maestro.

- **Asegúrese** siempre de que el contenido detallado todavía permite que un usuario permanezca centrado en el contenido maestro. A menudo, la mejor manera de lograrlo es representar el contenido detallado lo más cerca posible del contenido maestro. Para ello, puede representar el contenido detallado en una ventana emergente junto al contenido maestro o representar el contenido detallado en línea debajo del contenido maestro.

- **Nunca** use información en el punto de atención que aleja al usuario del contenido maestro. Si los usuarios necesitan ver el contenido detallado por separado, exponga una acción explícita que permita al usuario hacerlo.

#### <a name="design-details"></a>Detalles de diseño
 Una vez que haya determinado que la interfaz de usuario en el objeto es la opción correcta, hay cuatro consideraciones de diseño principales:

1. **Persistencia: ¿se** espera que el contenido sea duradero o transitorio?
   ¿Querrán los usuarios mantener la información visible para hacer referencia a la información o interactuar con ella? ¿O los usuarios querrán echar un vistazo rápidamente a la información y continuar con su tarea principal?

2. **Tipo de contenido:** ¿el contenido será informativo, utilizable o navegable?
   ¿Necesita el usuario detalles adicionales sobre el contenido maestro? ¿Necesita el usuario completar una tarea que afecte al contenido maestro? ¿O es necesario dirigir al usuario a otro recurso?

3. **Tipo de indicador:** ¿tiene sentido un indicador ambiente?
   ¿Se puede resumir la información de una manera útil y mostrarse sin sobresalte el contenido maestro?

4. **Gestos: ¿qué** gestos se usarán para invocar y descartar la interfaz de usuario?
   ¿Cómo mostrará el usuario el contenido detallado y lo enviará? ¿Hay valor en agregar un gesto como anclar para cambiar entre estados transitorios y duraderos?

   Cada uno de estos cuatro puntos de decisión tendrá un impacto en los componentes principales de la interfaz de usuario en el objeto.

### <a name="on-object-ui-components"></a>Componentes de interfaz de usuario en objeto

1. Tipo contenedor (presentador de contenido)

    - Flotante

    - En línea

2. Tipo de contenido

    - Informativo: datos que pueden ser estáticos o dinámicos

    - Actionable: comandos que cambian el contenido maestro

    - Navegación: vínculos que llevan al usuario a otra ventana o aplicación, como MSDN

3. Gestos

    - Invocación

    - Despido

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

#### <a name="container-content-presenter-type"></a>Tipo contenedor (presentador de contenido)
 Hay dos opciones principales disponibles para presentar contenido en el punto de atención:

1. **En línea:** un presentador en línea, como la vista de peek que se introdujo en el Editor de código de Visual Studio 2013, hace espacio para el nuevo contenido desplazando el contenido existente.

    - **Prefiere** los presentadores en línea si espera que los usuarios quieran dedicar una cantidad significativa de tiempo a hacer referencia al contenido que presenta o a interactuar con él.

    - **Evite** los presentadores en línea si espera que los usuarios quieran echar un vistazo a la información que presenta y, a continuación, continúe con su tarea principal con una interrupción mínima.

2. **Flotante:** un presentador flotante se coloca lo más cerca posible del contenido seleccionado, pero no modifica el diseño del contenido existente. Se pueden emplear varias estrategias, como mostrar un panel de contenido flotante sobre el espacio en blanco disponible más cercano al símbolo seleccionado.

    - **Prefiere** los presentadores flotantes si espera que los usuarios quieran echar un vistazo a la información que presenta y, a continuación, continúe con su tarea principal con una interrupción mínima.

    - **Evite** los presentadores flotantes si espera que los usuarios quieran dedicar una cantidad significativa de tiempo a hacer referencia al contenido que presenta o a interactuar con él.

#### <a name="content-type"></a>Tipo de contenido
 Hay tres tipos principales de contenido que se pueden mostrar dentro de cualquier contenedor de interfaz de usuario en objeto. Se puede mostrar cualquier combinación de estos tipos de información. Los tres tipos son:

1. **Informativo: la mayoría** de los contenedores de interfaz de usuario del objeto mostrarán algún tipo de contenido informativo. El contenido puede representar información sobre el estado actual del entorno o puede representar información sobre un posible estado futuro del entorno. Por ejemplo, podría usarse para mostrar el efecto de un comando determinado, como una refactorización, en el código existente.

    - **Use** siempre la representación canónica de la información que se muestra. Por ejemplo, el código debe parecerse a código, completarse con el resaltado de sintaxis y debe respetar cualquier fuente y otra configuración de entorno que haya establecido el usuario.

    - **Considere** siempre la posibilidad de admitir cualquier acción sobre el contenido informativo que sería posible si esa misma información se presenta como contenido maestro. Por ejemplo, si presenta código existente dentro de un contenedor de interfaz de usuario en objeto, considere la posibilidad de admitir la capacidad de examinar y modificar ese código.

    - **Considere** siempre la posibilidad de usar un color de fondo diferente si presenta contenido informativo que represente un posible estado futuro.

2. Acción: algunos contenedores de interfaz de usuario en objeto proporcionarán la capacidad de realizar alguna acción sobre el contenido maestro, como realizar una operación de refactorización.

    - **Coloque** siempre los comandos que pueden actuar por separado del contenido informativo.

    - **Habilite** y deshabilite siempre las acciones cuando corresponda.

    - **Consulte** siempre las directrices estándar para representar comandos dentro de cuadros de diálogo.

    - **Mantenga** siempre el número de acciones que se exponen en un contenedor de interfaz de usuario en objeto a un mínimo absoluto. Interactuar con la interfaz de usuario en el objeto debe ser una experiencia ligera y rápida. El usuario no debe tener que gastar energía en administrar el propio contenedor de interfaz de usuario en objeto.

    - **Tenga** en cuenta siempre cómo y cuándo se cerrará o descartará un contenedor de interfaz de usuario en objeto. Como procedimiento recomendado, cualquier acción que concluya el diálogo entre el contenido maestro y el contenido detallado también debe cerrar el contenedor de interfaz de usuario en objeto cuando se invoque esa acción.

3. **Navegación: algunos** contenedores de interfaz de usuario en objeto incluyen vínculos que llevan al usuario a otra ventana o aplicación, como abrir un artículo de MSDN en el explorador web del usuario.

    - **Antepone** siempre cualquier vínculo de navegación con "Abrir" para que los usuarios no se sorprendan al navegar a algún otro contenido.

    - **Separe** siempre los vínculos de navegación de los vínculos que se pueden actuar.

#### <a name="ambient-indicators-optional"></a>Indicadores de ambiente (opcional)
 Los indicadores ambientales pueden ser sutiles, incluido el texto presentado en un color de contraste del resto del código, o obvios, incluidos símbolos de marca de graduación, como subrayados ondulados e iconos de etiqueta inteligente. Los indicadores ambientales comunican la disponibilidad de información adicional y pertinente. Idealmente, proporcionan información útil incluso sin necesidad de que el usuario interactúe con ellos.

- **Coloque** siempre un indicador ambiente para que no distraiga ni abrume al usuario. Si no es posible colocar un indicador ambiente de este modo, considere otra solución.

- **Coloque** siempre el indicador ambiente lo más cerca posible del contenido con el que está relacionado.

- **Intente** siempre crear un indicador que resuma la información que pone a disposición. Considere la posibilidad de proporcionar un recuento del número de elementos de datos disponibles (por ejemplo, "3 referencias" en lugar de simplemente "Referencias") o piense en alguna otra manera de resumir los datos.

  - En los casos en los que los datos de un indicador no se pueden calcular y mostrar siempre, considere la posibilidad de proporcionar comentarios progresivas a medida que se calculan los valores. Por ejemplo, considere la posibilidad de animar los cambios que reflejan las actualizaciones de los datos disponibles, de forma similar a la forma en que el icono dinámico de correo electrónico en Windows Phone se actualiza a medida que aumenta el número de correos electrónicos no leídos.

- **No** agregue nunca más indicadores de los que un usuario pueda asumir razonablemente para un determinado fragmento de contenido. Los indicadores ambientales deben ser útiles sin necesidad de ninguna interacción del usuario. Los indicadores pierden su ambiente si requieren desbordamiento y otros controles de administración para verlos.

#### <a name="gestures"></a>Gestos
 Un aspecto clave de permitir que el usuario mantenga el foco en el contenido maestro es admitir los gestos adecuados para abrir y descartar el contenido de detalles adicional.

- **Exija** siempre al usuario que realice algún gesto explícito para abrir el contenido adicional. Los gestos abiertos comunes incluyen:

  - **Mantener el puntero:** información sobre herramientas o contenido informativo no interactivo

  - **Comando explícito:** presentador en línea

  - **Haga doble clic en el indicador ambiente:** Ventana emergente de CodeLens

- **Descarte** siempre el contenido detallado cada vez que el usuario presione la tecla Esc.

- **Tenga** siempre en cuenta el contexto de la interfaz de usuario en objeto. En el caso de los presentadores de contenido que permiten la interacción dentro del contenedor, considere detenidamente si se debe mostrar información adicional al mantener el puntero, lo que es probable que sea perjudicial para el flujo de trabajo del usuario.

- **No** muestre nunca contenido al mantener el puntero que parece ser editable o invita a la interacción del usuario. Este comportamiento puede frustrar a los usuarios si intentan mover el cursor sobre el contenido detallado, ya que el comportamiento estándar de una información sobre herramientas es descartar inmediatamente cuando el cursor deja de estar sobre el contenido maestro que lo produjo.

## <a name="selection-models"></a><a name="BKMK_SelectionModels"></a> Modelos de selección

### <a name="overview"></a>Información general
 Un modelo de selección es el mecanismo que se usa para indicar y confirmar operaciones en uno o varios objetos de interés dentro de la interfaz de usuario. En este tema se de abordan los patrones de interacción de selección Visual Studio editores de documentos: editores de texto, superficies de diseño y superficies de modelado.

 Los usuarios deben tener una manera de indicar Visual Studio en qué están trabajando, y Visual Studio debe responder de forma predecible con comentarios a los usuarios sobre el funcionamiento. Las diferencias o una comunicación errónea entre el usuario y la interfaz de usuario pueden dar lugar a que el usuario no tenga en cuenta una acción, lo que puede tener consecuencias involuntarias. A menudo, el error pasa desapercibido hasta que el usuario ve que falta algo o que ha cambiado. Por lo tanto, los modelos de selección son una de las partes más críticas del diseño de la interfaz de usuario. Aunque los modelos de Visual Studio son coherentes con Windows, hay ligeras variaciones.

 En Visual Studio, como en Windows, los modelos de selección difieren en función del contexto en el que se produce la interacción. Las selecciones pueden producirse en cuatro tipos de objetos:

- Texto

- Objetos gráficos

- Listas y árboles

- Cuadrículas

  Dentro de estos objetos, hay tres tipos de selecciones:

- Contiguos

- Desunido

- Region

#### <a name="scope"></a>Ámbito
 El componente más importante de la selección es asegurarse de que el usuario sabe en qué ventana está trabajando (activación) y dónde se encuentra el foco (selección). Visual Studio la funcionalidad de administración de ventanas en Windows, pero el esquema de activación es el mismo: la interacción con una ventana aporta el foco a la ventana. Visual Studio tiene dos indicadores para la activación: uno para las ventanas de documentos y otro para las ventanas de herramientas.

 Para las ventanas de documento, la ventana activa se indica mediante una pestaña de ventana de documento que llega al principio y cambia su color de fondo:

 ![Selección de pestaña activa en Visual Studio](../../extensibility/ux-guidelines/media/0713-01_activetab.png "0713-01_ActiveTab")

 **Selección de pestañas activas**

 Para las ventanas de herramientas, la ventana activa se indica mediante un cambio en el color del área de la barra de título de la ventana de herramientas:

 ![Selección de ventana de herramientas activa en Visual Studio](../../extensibility/ux-guidelines/media/0713-02_activetoolwindow.png "0713-02_ActiveToolWindow")

 **Ventana de herramientas activa que muestra la selección principal de un nodo**

 ![Selección de ventana de herramientas inactiva en Visual Studio](../../extensibility/ux-guidelines/media/0713-03_inactivetoolwindow.png "0713-03_InactiveToolWindow")

 **Ventana de herramientas inactiva, que muestra la selección latente del nodo**

 Una vez que una ventana está activa, su foco se indica según los modelos de selección descritos en esta sección de las directrices.

#### <a name="context"></a>Contexto
 Visual Studio diseñado para conservar un concepto sólido de contexto y realizar un seguimiento de dónde está trabajando el usuario. Solo hay una ventana activa, ya sea una herramienta o una ventana de documento. Sin embargo, la ventana de documento superior siempre conserva una selección latente. Aunque el foco podría estar en una ventana de herramientas, la ventana del documento que se activó por última vez muestra una selección, incluso en un estado inactivo. Esto se hace para conservar el contexto del usuario en el documento que estaba editando, mostrándole que Visual Studio ha conservado su estado para que puedan volver y desplazarse sin problemas entre ventanas de herramientas y ventanas de documentos.

### <a name="text-selection"></a>Selección de texto
 Visual Studio editores que son estrictamente textuales, como el editor de texto integrado, usan el mismo modelo de selección de texto y la misma apariencia que se describe en la página Mouse [and Pointers (Punteros](/windows/desktop/uxguide/inter-mouse) y mouse) de las Instrucciones de interacción de la experiencia del usuario de Windows en MSDN. El foco de entrada en el editor de texto se indica mediante una barra vertical denominada punto de inserción. El punto de inserción tiene un grosor de un solo píxel y se colore como el inverso de lo que aparece detrás. Parpadea según la velocidad establecida por la configuración  de velocidad  de parpadeo cursor en la pestaña Velocidad del applet Teclado en Panel de control. 

#### <a name="contiguous-and-disjoint-selection"></a>Selección contigua y desconexa
 La selección en el editor de texto es solo contigua. No se permiten selecciones de texto no unida, pero deben abordarse en editores gráficos de objetos. Cuando el puntero del mouse del usuario está sobre un área de texto, el cursor cambia a un haz de I. Un solo clic coloca el punto de inserción en el editor de texto en la ubicación de clic. Al mantener presionado el botón del mouse, se inicia un resaltado de selección y al soltar el botón del mouse se finaliza el resaltado de selección.

#### <a name="region-selection-box-selection"></a>Selección de región (selección de cuadro)
 Visual Studio selecciones de región en el editor de texto, y esto se denomina selección de cuadro. La selección de cuadro permite al usuario seleccionar una región de texto que no sigue la secuencia de texto normal. Al igual que con la selección de texto estándar, la selección debe ser contigua. La selección de cuadro se inicia manteniendo presionada la tecla Alt mientras se arrastra con el mouse. La selección de cuadro también se puede iniciar manteniendo presionadas las teclas Alt y Mayús mientras se usan las teclas de dirección para indicar la región de selección. La selección de cuadro usa el resaltado de selección normal y muestra el cursor del punto de inserción parpadeando al final del área de selección.

 ![Selección &#40;cuadro&#41; configuración regional en Visual Studio](../../extensibility/ux-guidelines/media/0713-04_boxselection.png "0713-04_BoxSelection")

 **Selección de región (cuadro) en Visual Studio**

#### <a name="text-selection-appearance"></a>Apariencia de la selección de texto
 Los colores usados para la selección activa e inactiva en el editor se pueden personalizar. Para personalizar la apariencia visual del editor, un usuario puede ir a Herramientas **> Opciones** y, a continuación, buscar en Entorno > Fuentes y colores > Editor **de texto.**

### <a name="graphical-selection"></a>Selección gráfica

#### <a name="interaction"></a>Interacción
 La selección de objetos gráficos puede ser compleja y depende de una serie de factores:

- **Modelo de selección principal del editor.** Los editores que contienen objetos gráficos también se pueden usar para editar texto o cuadrículas. Por ejemplo, el editor podría ser un editor basado en texto que también admite la colocación de objetos gráficos, como el diseñador XAML Visual Studio. La compatibilidad con varios tipos de objetos puede afectar a la forma en que el usuario selecciona grupos que se com decir de distintos tipos de objetos.

- **Compatibilidad con los estados de selección principal y secundario.** Un editor puede proporcionar estados de selección principal y secundario para que los objetos se puedan editar al unísono, alinearse entre sí, cambiar de tamaño juntos, y así sucesivamente.

- **Compatibilidad con la edición en contexto.** Los editores también pueden permitir editar el contenido de sus objetos gráficos. Por ejemplo, una forma de rectángulo también puede contener texto en el interior que el usuario puede cambiar. Además, ese texto se podría centrar o justificar. La edición en contexto implica un nivel más detallado de interacción del usuario y, por tanto, requiere un conjunto adecuado de indicaciones visuales para presentar información de estado al usuario.

#### <a name="mouse-interaction"></a>Interacción del mouse

|Entrada|Resultado|
|-----------|------------|
|Hacer clic en un objeto no seleccionado|Selecciona el objeto y muestra una línea discontinua y identificadores de selección, si el objeto es de tamaño ajustable.|
|Haga clic en un objeto seleccionado.|Activa la edición en contexto si el objeto lo admite. Al hacer clic fuera del objeto se desactiva el modo de edición en contexto.|
|Hacer doble clic en un objeto|Abre el código subyacente al objeto para su edición y podría insertar un controlador de eventos predeterminado, si procede.|
|Apuntar a un objeto|Cambia el puntero al cursor de movimiento. La apariencia del objeto, como su luminosidad o color, puede cambiar.|
|Apuntar a un identificador de selección|Cambia el puntero al cursor de cambio de tamaño. En el caso de los objetos que admiten la rotación, algunos identificadores de selección pueden cambiar el puntero a un cursor de rotación, ya que el puntero se coloca de forma diferente (por ejemplo, se mueve más lejos) con respecto al identificador de selección.|
|Arrastrar|Incluso si el objeto no está seleccionado previamente, cambia el puntero al cursor de movimiento y mueve el objeto.|
|El editor pierde el foco|Desactiva el modo de edición en contexto, aunque el objeto conserva el contenido y la apariencia que tenía durante su último estado de operación o selección.|
|Selección de objetos|Se indica mediante un borde, una línea de puntos u otro tratamiento visualmente distinto para resaltar el límite del objeto.|
|Cambio de tamaño de un objeto seleccionado|Indicado por identificadores de selección.<br /><br /> Un objeto de tamaño variable tiene ocho identificadores, que representan cada dirección en la que se puede cambiar el tamaño. Se pueden usar menos identificadores si el objeto solo se puede cambiar de tamaño en determinadas direcciones. Cuando el usuario puede cambiar el tamaño de un objeto a donde ocho identificadores no serían interactivos, se pueden usar cuatro identificadores. Los tamaños de identificador deben estar asociados al borde de la ventana y a las métricas perimetrales con la función de API **GetSystemMetrics** para que el tamaño sea proporcional a la resolución de pantalla.<br /><br /> ![Controladores de tamaño](../../extensibility/ux-guidelines/media/0713-05_resizehandles.png "0713-05_ResizeHandles")|
|Girar un objeto seleccionado|![Controladores de giro](../../extensibility/ux-guidelines/media/0713-06_rotate.png "0713-06_Rotate")|

#### <a name="keyboard-interaction"></a>Interacción con el teclado

|Entrada|Resultado|
|-----------|------------|
|Pestaña|Mueve el indicador de foco entre el orden lógico de los objetos en el editor. Puede ser de izquierda a derecha o de arriba a abajo según el valor de propiedad **TabIndex** (o equivalente), el orden de creación de objetos y el propósito general del editor. Mayús+Tab invierte la dirección del indicador de foco.|
|Barra espaciadora|Activa el modo de movimiento panorámico mientras se mantiene la pulsación de tecla. Se requiere una entrada adicional del mouse para desplazarse por la posición de la ventanilla.|
|Ctrl+Barra espaciadora|Activa el modo de zoom mientras se mantiene la pulsación de tecla. Se requiere una entrada adicional del mouse para aumentar y disminuir el factor de zoom.|
|Ctrl+Alt+Signo menos|Reduce el factor de zoom en un nivel.|
|Ctrl+Alt+Signo más|Aumenta el factor de zoom en un nivel.|
|Mayús O Ctrl|Agrega el objeto al grupo de selección. Ctrl también permite quitar objetos individualmente del grupo de selección.|
|Entrar|Realiza el comando predeterminado para el objeto (normalmente Abrir o Editar).|
|F2|Activa la edición en contexto para el objeto .|
|Teclas de dirección|Mueve los objetos seleccionados en la dirección de la tecla de flecha presionada, en incrementos pequeños (por ejemplo, 1 píxel a la vez)|
|Ctrl+teclas de dirección|Mueve los objetos seleccionados en la dirección de la tecla de flecha presionada, en incrementos mayores (por ejemplo, 10 píxeles a la vez)|
|Mayús+teclas de dirección|Cambia el tamaño de los objetos seleccionados en la dirección respectiva, en incrementos pequeños (por ejemplo, 1 píxel a la vez)|
|Ctrl+Mayús+teclas de dirección|Cambia el tamaño de los objetos seleccionados en la dirección respectiva, en incrementos mayores (por ejemplo, 10 píxeles a la vez)|

 Cuando los usuarios editan controles en su lugar, puede que tenga sentido que los objetos cambien automáticamente de tamaño con la entrada del usuario. Por ejemplo, si el usuario edita un control de etiqueta, la etiqueta debería crecer para mostrar el texto que el usuario acaba de escribir. Si esto no se hace, el usuario debe cambiar el tamaño del control manualmente después de editar el texto. Si el usuario tiene muchos controles, esto se convierte en una tarea rote e improductiva.

#### <a name="graphical-containers"></a>Contenedores gráficos
 En algunos casos, los editores gráficos proporcionan contenedores para otros objetos gráficos, como el control Panel de Windows Forms o el control Diseño de cuadrícula en el diseñador HTML. Si el editor proporciona contenedores para otros objetos gráficos, debe usarse el siguiente modelo de selección solo para el contenedor (los objetos dentro del contenedor siguen el modelo estándar como se describió anteriormente):

|Entrada|Resultado|
|-----------|------------|
|Un solo clic en el contenedor|Selecciona el objeto contenedor sin seleccionar directamente ninguno de los objetos contenidos. El contenedor se puede mover o cambiar de tamaño con la entrada estándar del mouse y el teclado (como se describió anteriormente). Los objetos contenidos se mueven en relación con el contenedor, pero los objetos contenidos no se cambian de tamaño a menos que también se seleccionen directamente.|
|Mantenga el puntero sobre la región de límite del contenedor.|Convierte el mouse en el cursor de movimiento, lo que indica que se puede mover el contenedor.|
|Arrastre la región de límite del contenedor.|Cambia el mouse al cursor de movimiento y mueve el contenedor (y los objetos contenidos dentro de ). El contenedor no se puede mover sin seleccionarse primero con un solo clic.|
|Un solo clic en un objeto dentro del contenedor|Anula la selección del contenedor (si está seleccionado) y selecciona solo el objeto en el que se ha hecho clic.|
|Mayús+clic o Ctrl+clic en un objeto o contenedor contenidos|Agrega el objeto en el que se ha hecho clic a un grupo de selección o selección existente. Si el objeto en el que se ha hecho clic ya es miembro del grupo de selección, se quita del grupo de selección.|

 Los objetos contenidos deben cumplir el modelo de selección básico como se describe en la sección anterior. A partir de las pruebas de facilidad de uso del diseñador de Windows Forms, los usuarios esperaban un acceso sin problemas a los objetos contenidos sin intervención de los pasos (impuestos por el objeto de contención).

#### <a name="disjoint-and-region-selections"></a>Selecciones de región y desconexas
 Los editores de objetos gráficos deben admitir selecciones desconexas. Tenga en cuenta que este gráfico no muestra la apariencia del control para Visual Studio. Consulte [Apariencia de selección de objetos gráficos](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_GraphicalObjectSelectionAppearance) para obtener especificaciones visuales detalladas.

 ![Selectores de región y discontinuos](../../extensibility/ux-guidelines/media/0713-07_disjointregionselectors.png "0713-07_DisjointRegionSelectors")

 **Selección desconexa**

 Los editores gráficos también deben proporcionar selecciones de región con un indicador de selección de tipo marquesina. Si el editor gráfico admite otros tipos de objeto (como texto), es posible que las selecciones de región no sean posibles en función de las restricciones de esos otros tipos de objeto.

 ![Selección de recuadro](../../extensibility/ux-guidelines/media/0713-08_marqueeselection.png "0713-08_MarqueeSelection")

 **Selección de recuadro**

#### <a name="primary-and-secondary-selections"></a>Selecciones principales y secundarias
 Algunos editores gráficos de objetos permiten al usuario editar o alinear objetos en grupos. En este caso, es necesario introducir el concepto de selecciones principales y secundarias. La selección principal es el objeto al que responden todos los demás objetos para las operaciones de grupo. El objeto que el usuario selecciona primero se convierte en el control principal y las selecciones posteriores se convierten en las selecciones secundarias. La selección principal tiene un tratamiento visual distinto de las selecciones secundarias para indicar qué objeto es principal:

 ![Selección primaria y secundaria](../../extensibility/ux-guidelines/media/0713-09_primarysecondary.png "0713-09_PrimarySecondary")

 **Selección principal con dos selecciones secundarias**

#### <a name="graphical-object-selection-appearance"></a><a name="BKMK_GraphicalObjectSelectionAppearance"></a> Apariencia de selección de objetos gráficos
 Los identificadores de selección son cuadrados dibujados en un patrón rectangular alrededor del rectángulo delimitador del objeto. En el gráfico siguiente se muestran ejemplos de los distintos estados que puede tener un objeto gráfico con el identificador, el tamaño y la apariencia de edición en contexto. El tamaño de los identificadores debe estar vinculado a las métricas perimetrales y de borde de la ventana mediante la API **GetSystemMetrics.**

| State | Aspecto | Detalles del objeto visual |
|-------------------------|---------------| - |
| **No seleccionado** | Predeterminado | ![Estado de botón predeterminado](../../extensibility/ux-guidelines/media/0713-10_defaultstate.png "0713-10_DefaultState") |
| **Selección principal** | Redimensionable | ![Selección primaria con controladores de tamaño](../../extensibility/ux-guidelines/media/0713-11_primaryresize.png "0713-11_PrimaryResize") |
| **Selección principal** | No se puede hacer el tamaño | ![Selección primaria sin controladores de tamaño](../../extensibility/ux-guidelines/media/0713-13_primarynoresize.png "0713-13_PrimaryNoResize") |
| **Selección principal** | Bloqueado | ![Selección primaria bloqueada](../../extensibility/ux-guidelines/media/0713-15_primarylocked.png "0713-15_PrimaryLocked") |
| **Selección secundaria** | Redimensionable | ![Selección primaria con controladores de tamaño](../../extensibility/ux-guidelines/media/0713-17_secondaryresize.png "0713-17_SecondaryResize") |
| **Selección secundaria** | No se puede hacer el tamaño | ![Selección secundaria sin controladores de tamaño](../../extensibility/ux-guidelines/media/0713-19_secondarynoresize.png "0713-19_SecondaryNoResize") |
| **Selección secundaria** | Bloqueado | ![Selección secundaria bloqueada](../../extensibility/ux-guidelines/media/0713-21_secondarylocked.png "0713-21_SecondaryLocked") |
| **Interfaz de usuario activa** | Predeterminado | ![Estado activo de interfaz de usuario](../../extensibility/ux-guidelines/media/0713-23_uiactive.png "0713-23_UIActive") |

### <a name="view-selection-models"></a>Visualización de modelos de selección

#### <a name="tree-view"></a>Vista de árbol
 La selección en una vista de árbol se muestra con un resaltado simple. Si el usuario hace clic en un nombre de nodo o un icono de nodo, el nodo se selecciona. Los glifos triangulares situados a la izquierda del nodo expanden o contraen el control de árbol, pero no afectan a la selección del usuario, con una excepción: al contraer un nodo primario cuando la selección está en un elemento secundario de ese nodo, la selección se mueve al nodo primario.

 ![Vista de árbol típica de Visual Studio](../../extensibility/ux-guidelines/media/0713-25_treeview.png "0713-25_TreeView")

 **Vista de árbol típica de Visual Studio**

 Las vistas de árbol pueden admitir selecciones contiguas y no contiguos, incluso en varios niveles del árbol. Se deben realizar varias selecciones contiguas o no contiguos en nodos de árbol visibles. Si se contrae un nodo, se pierde la selección desconexa y el nodo que se contrae obtiene la selección. De esta manera, el usuario puede ver los nodos que se verán afectados por una operación. Cuando se contraen los nodos, no queda claro qué nodos podrían verse afectados.

 Cuando se selecciona un nodo primario, la operación debe aplicarse al elemento primario, aunque puede haber casos en los que tenga sentido que una operación se aplique al elemento primario y a todos sus elementos secundarios. En este caso, proporcione una interfaz de usuario adicional durante la operación, como una casilla o un cuadro de diálogo de confirmación para que la opción "Aplicar a todos los elementos secundarios" sea explícita para el usuario.

##### <a name="renaming"></a>Cambiar nombre
 Si los nodos del árbol admiten el cambio de nombre, el cambio de nombre debe realizarse en contexto. La operación local debe ser el estándar en todos los controles de árbol de Visual Studio. Proporcione un comando de cambio de nombre que active inmediatamente el modo de edición en contexto, con la selección de texto que abarca todo el nombre del nodo, listo para aceptar la entrada del usuario. Si el nodo representa un archivo, el nombre de archivo debe contener la extensión. El resaltado de selección debe incluir solo el cuerpo del nombre de archivo y no la extensión.

|Entrada|Resultado|
|-----------|------------|
|Entrar (tecla)|Confirma la operación de cambio de nombre.|
|Tecla Esc|Cancela la operación de cambio de nombre.|
|Hacer clic fuera de la región de edición local|Confirma la operación de cambio de nombre.|
|Deshacer|Proporcionar deshacer fácilmente para cancelar la operación de cambio de nombre|

#### <a name="selection-within-lists-and-grid-controls"></a>Selección dentro de listas y controles de cuadrícula
 El concepto clave en la selección de lista es que se basa en filas, lo que significa que cuando se realiza una selección, toda la fila se selecciona como una unidad. Por el contrario, las cuadrículas pueden permitir seleccionar celdas específicas sin afectar a ningún otro aspecto de la fila. Las cuadrículas también pueden contener una jerarquía de filas anidadas (por ejemplo, en treeGrid) que permiten seleccionar y deseleccionar ramas completas de la jerarquía mediante la interacción con las filas primarias. La selección en las listas se muestra mediante un color de resaltado simple en toda la fila de datos. El foco se muestra mediante un borde de puntos de un solo píxel alrededor de la fila o celda editable actual (fila si todas las celdas son de solo lectura).

> [!NOTE]
> **El enfoque** **y la selección** son conceptos diferentes. *El* foco es una indicación de qué elemento de la interfaz de  usuario está destinado a recibir entradas no dirigidas explícitamente a otro objeto, mientras que la selección hace referencia al estado de inclusión de un objeto en un conjunto de objetos en el que pueden tener lugar operaciones posteriores.

 Las selecciones de las listas pueden ser contiguas, no contiguos o regiones. Cuando se permiten varias selecciones, siempre se debe admitir la selección contigua y descontigua, mientras que la compatibilidad con las selecciones de región (cuadro) es opcional. Las selecciones de región se inician arrastrando en el espacio en blanco del cuerpo de la lista.

| Object | Selección |
|--------|------------|
| List | Contiguos |
| List | Desunido |
| List | Region |

 Al hacer clic una vez en una lista, se selecciona la fila donde se produjo el clic. Si el usuario hace clic en una celda de lista que admite la edición en contexto, la celda también se activa inmediatamente para la edición en contexto. De lo contrario, la fila completa se selecciona inmediatamente y muestra un resaltado.

 Arrastrar en el cuerpo de la lista hace una de estas tres cosas:

- Inicia una selección de región si la lista la admite y el mouse hacia abajo está en un espacio en blanco.

- Inicia una operación de arrastrar y colocar si la celda o fila de lista admite ser un origen de arrastre.

- Selecciona la fila actual.

##### <a name="in-place-editing"></a>Edición en contexto
 Cuando se permite la edición en contexto, hay dos modelos básicos: control de edición simple y selector de propiedades. Con un control de edición simple, el contenido está resaltado y listo para la entrada del usuario en cuanto se activa la edición en contexto. Cuando se implementa un selector de propiedades, el botón que invoca el selector de propiedades se muestra una vez activado el modo de edición en contexto y no se resalta la selección actual. El botón selector debe estar justifique a la derecha en la celda. Para ver ejemplos de edición en contexto, consulte la ventana **Propiedades** **y** Lista de tareas en Visual Studio.

##### <a name="keyboard-support"></a>Compatibilidad con el teclado
 La compatibilidad con el teclado para la selección en listas y cuadrículas sigue las convenciones estándar de Windows:

- Las teclas de dirección navegan por la lista y seleccionan cada fila o celda a medida que se mueve el foco.

- Mayús + flecha realiza una selección contigua en la dirección de las teclas de dirección.

- Ctrl + flecha seguida de barra espaciadora alterna entre agregar y quitar elementos de lista de la selección, creando una selección no unida.

- Para las cuadrículas que contienen jerarquías anidadas, la tecla Flecha derecha expande una fila primaria y la tecla Flecha izquierda contrae una.

- La tecla Tab mueve el foco entre las celdas de la fila actual si las celdas son editables.

- La tecla Entrar realiza el comando predeterminado en el elemento de la lista (a menudo **Abrir**).

- La tecla F2 activa la edición en contexto para la celda seleccionada actualmente.

## <a name="persistence-and-saving-settings"></a><a name="BKMK_PersistenceAndSavingSettings"></a> Persistencia y guardado de la configuración

### <a name="overview"></a>Información general
 Aunque cada componente de software de Visual Studio suele ser responsable de su propio estado y persistencia, Visual Studio guarda automáticamente la configuración en algunos casos, como con tamaños y posiciones de ventana. La tabla siguiente es una combinación de la configuración guardada automáticamente y la configuración que requiere que se haga una acción explícita del usuario o programada.

|Object|Qué guardar|Cuándo guardar|Dónde guardar|
|------------|------------------|------------------|-------------------|
|Objeto seleccionable (por ejemplo, una línea de código)|Un punto de interrupción en una línea de código<br /><br /> Acceso directo de usuario asociado a la línea de código|Cuando se guarda el proyecto|Archivo **de opciones de usuario (.suo)** para el proyecto|
|Diálogo|Ubicación del cuadro de diálogo, si se ha movido<br /><br /> Vista que el usuario usó por última vez en el cuadro de diálogo|Cuando se cierra el cuadro de diálogo<br /><br /> Cuando finaliza Visual Studio sesión|En memoria<br /><br /> Registro en **HKEY_Current_User**|
|Periodo|Tamaño y ubicación de la ventana|Cuando se cierra la ventana<br /><br /> Cuando cambia Visual Studio modo de configuración<br /><br /> Cuando finaliza Visual Studio sesión|Archivo **de opciones de usuario (.suo)** para el proyecto<br /><br /> Archivo de opciones personalizado para la configuración de ventana|
|Documento|Selección actual en el documento<br /><br /> Vista del documento<br /><br /> Los últimos lugares que visitó el usuario|Cuando se guarda el documento|Archivo **de opciones de usuario (.suo)** para el proyecto|
|Project|Referencias a archivos<br /><br /> Referencias a directorios en disco<br /><br /> Referencias a otro software<br /><br /> Componentes<br /><br /> Información de estado sobre el propio proyecto|Cuando se guarda el proyecto|El archivo del proyecto|
|Solución|Referencias a proyectos<br /><br /> Referencias a archivos|Cuando se guarda el proyecto o la solución|El **archivo de solución (.sln)**|
|Configuración en **Herramientas > opciones**|Personalizaciones de teclado<br /><br /> Personalizaciones de la barra de herramientas<br /><br /> Esquemas de colores|Cuando se **cierra el cuadro de diálogo >** herramientas<br /><br /> Cuando finaliza Visual Studio sesión|Registro en **HKEY_Current_User**|

 Lo que hace el usuario y, cuando lo hace, determina si una configuración se guarda en memoria (durante la sesión), se guarda en el disco (entre sesiones como una configuración del Registro), como parte del propio archivo de proyecto o solución, como parte del archivo de opciones de solución **(.suo)** o como un archivo de configuración personalizado que solo ese componente de software conoce. En la tabla anterior se muestran varios eventos en los que se puede guardar la configuración. Sin embargo, hay otras ocasiones en las que es posible que desee guardar el estado:

- Cuando el usuario cambia de ubicación dentro de un cuadro de diálogo o ventana

- Cuando el usuario transfiere el foco a otra ventana

- Cuando el usuario cambia del diseño al modo de depuración

- Cuando el usuario cierra la sesión de su cuenta

- Cuando el equipo entra en hibernación o se apaga

- Cuando el equipo o la unidad de disco duro esté a punto de volver a formatear y configurarse

### <a name="window-configurations"></a>Configuraciones de ventana
 Una configuración de ventana es la presentación básica del entorno de desarrollo; es un esquema que consta de la lista de ventanas de herramientas presentes y la forma en que se organizan. En el caso de las ventanas administradas por el IDE (ventanas ide), la información de diseño se conserva por usuario, por lo que cuando un usuario inicia el IDE, el diseño de la ventana aparece igual que cuando salió por última vez Visual Studio. El estado y la posición de las ventanas ide se conservan en un archivo de opciones personalizado en formato XML. Las ventanas de herramientas creadas por paquetes cargados en el IDE conservan su información de estado en el Registro y pueden ser o no por usuario.

#### <a name="profile-specific-layouts"></a>Diseños específicos del perfil
 Cada perfil incluye diseños de ventana de herramientas, organizados de forma familiar para determinados roles de desarrollador (los desarrolladores de Visual C++ esperan ver el **Explorador de soluciones en** el lado izquierdo del IDE, mientras que los desarrolladores de C# esperan ver el **Explorador de soluciones a** la derecha). Los diseños de ventana específicos del perfil se cargan después de que el usuario elija un perfil al iniciarse. Un autor del paquete debe determinar el diseño de ventana más adecuado para la experiencia del cliente, sabiendo que los cambios que realiza el usuario en la configuración de la ventana se conservarán.

## <a name="touch-input"></a><a name="BKMK_TouchInput"></a> Entrada táctil
 Los usuarios usan cada vez más productos de desarrollo de Microsoft en dispositivos táctiles. Sin embargo, hay barreras que dificultan el uso de herramientas de desarrollo en dispositivos táctiles. Los usuarios esperarán que nuestros productos proporcionen una experiencia táctil confiable y precisa. La intención de estas directrices es informar sobre las capacidades táctiles que se deben incorporar y fomentar una experiencia táctil coherente entre Visual Studio y productos relacionados.

### <a name="levels-of-experience"></a>Niveles de experiencia
 Los siguientes niveles de experiencia están diseñados para servir como guía para ayudar a los equipos a decidir qué funcionalidades táctiles ofrecer en función de su nivel deseado de interés de inversión en el contacto.

- La **experiencia básica es** para los equipos que desean proporcionar funcionalidades táctiles para que no haya ningún punto de conexión a lo largo de su trabajo.

- La **experiencia optimizada es** para los equipos que desean proporcionar las funcionalidades táctiles más comunes (por ejemplo, las que normalmente están disponibles en las aplicaciones de explorador de Internet).

- La **experiencia con privilegios** elevados es para los equipos que desean agregar funcionalidades como gestos u otras funcionalidades opcionales que pueden hacer que su aplicación sea fácil de usar.

||Experiencia básica|Experiencia optimizada|Experiencia con privilegios elevados|
|-|----------------------|--------------------------|-------------------------|
|**Permite a los usuarios...**|Corrección del código y la lectura de nivel de proyecto o solución sin inter-ends|Realizar tareas de mantenimiento, refactorizaciones y navegación|Operar en una experiencia coherente, intuitiva y fluida con confianza|
|**Editor**|Movimiento panorámico y selección táctiles<br /><br /> Barra de desplazamiento táctil para saltar y presionar +arrastrar|Reducir zoom<br /><br /> Desplazamiento rápido<br /><br /> Selección<br /><br /> Uso sencillo del menú contextual||
|**Ventanas de herramientas principales**|Desplazamiento panorámico de lista<br /><br /> Selección de elementos<br /><br /> Barra de desplazamiento táctil para saltar y presionar +arrastrar|Desplazamiento y selección sencillos de elementos||
|**Basado en ventanas**||Ventana De cambio de tamaño<br /><br /> Acceso rápido||
|**Documento completo**||Navegación sencilla entre archivos abiertos||
|**Gestos**||Asegurarse de que los gestos comunes funcionan en el IDE|Acciones basadas en gestos<br /><br /> Compatibilidad con arrastrar y colocar y diseñadores|
|**Otras consideraciones**|||Teclado en pantalla personalizado|

#### <a name="gestures"></a>Gestos
 Los gestos proporcionan a los usuarios un acceso directo a los comandos que, de lo contrario, podrían requerir una interacción más complicada. Consulte las directrices de Windows sobre los [gestos](/windows/desktop/wintouch/windows-touch-gestures-overview)táctiles comunes para aplicaciones de escritorio y siga esta guía para la mayoría de los gestos, incluidos gestos sencillos como movimiento panorámico y zoom.
