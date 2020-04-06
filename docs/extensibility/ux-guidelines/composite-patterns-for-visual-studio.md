---
title: Patrones compuestos para Visual Studio ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e48ecfb2-f4b5-4d3a-b4a2-7a4d62fa4ec0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 500ea8ffe7c33c1d747590ea074bff43fa1a3ab3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698615"
---
# <a name="composite-patterns-for-visual-studio"></a>Patrones compuestos para Visual Studio
Los patrones compuestos combinan elementos de interacción y diseño en configuraciones distintas. Algunos de los patrones compuestos más importantes de Visual Studio con respecto a la coherencia incluyen:

- [Visualización de datos](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_DataVisualization)

- [Interfaz de usuario en el objeto y miradas](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

- [Modelos de selección](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

- [Configuración de persistencia y ahorro](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

- [Entrada táctil](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)

## <a name="data-visualization"></a><a name="BKMK_DataVisualization"></a>Visualización de datos

### <a name="overview"></a>Información general
 Los gráficos son una forma visual de agregar y visualizar datos con el fin de mejorar la toma de decisiones. Pueden ayudar a los usuarios que se enfrentan a una gran cantidad de datos, pero poco significado ver lo que merece atención y lo que podría necesitar una acción.

 El usuario se beneficiará de un gráfico si se cumple alguna de las siguientes condiciones:

- ¿El gráfico ayudará a los usuarios a identificar las tareas en las que pueden actuar?

- ¿Permitirá el gráfico a los usuarios pronosticar las consecuencias de posibles cambios?

- ¿El gráfico ayudará a los usuarios a descubrir tendencias e identificar patrones?

- ¿Permitirá el gráfico a los usuarios tomar mejores decisiones?

- ¿Ayudará el gráfico a responder a una pregunta específica que los usuarios puedan tener en el contexto dado?

#### <a name="general-rules-for-charts"></a>Reglas generales para gráficos

- Etiquete claramente los datos. Las ilustraciones sin explicación son sólo imágenes bonitas.

- Arranque los ejes en cero para evitar proporciones sesgadas. La longitud de línea y el tamaño de la barra son indicaciones visuales importantes para comprender las relaciones entre los puntos de datos.

- Crear gráficos, no infografías. Las infografías son representaciones artísticas de los datos, y su objetivo principal es la narración visual. Los gráficos pueden (y deben) ser visualmente atractivos, pero deje que los datos hablen por sí mismos.

- Evite el eskeumorfismo, los gráficos de barras pictóricas, las marcas hash de contraste y otros toques infográficos.

- No utilice efectos 3D como elemento decorativo. Utilícelos sólo si realmente son parte integral de la capacidad del usuario para comprender la información.

- Evite el uso de varias líneas y rellenos, ya que más de dos colores pueden hacer que este tipo de gráfico sea difícil de leer e interpretar correctamente.

- No utilice un gráfico (o cualquier ilustración) como único medio para entender un concepto o interactuar con los datos. Esto presenta dificultades para los usuarios con discapacidades visuales.

- No utilice gráficos como elementos gratuitos o decorativos en una página. En otras palabras, si un gráfico no agrega ningún valor o ayuda a los usuarios a resolver un problema, no lo use.

### <a name="chart-types"></a>Tipos de gráficos
 Los tipos de gráficos utilizados en Visual Studio incluyen gráficos de barras, gráficos de líneas, un gráfico circular modificado conocido como gráfico circular o "gráfico de anillos", líneas de tiempo, gráficos de dispersión (también denominados "gráficos de clúster") y gráficos de Gantt. Cada tipo de gráfico es útil para comunicar un tipo diferente de información.

### <a name="other-charting-considerations"></a>Otras consideraciones de gráficos

#### <a name="color"></a>Color
 Hay una paleta específica de colores de gráficos definidas para su uso en Visual Studio. La paleta es accesible para los principales tipos de daltonismo, y los colores se pueden diferenciar incluso cuando se utilizan como rebanadas de color muy estrechas. Puede usar estos colores en cualquier combinación para cualquier tipo de gráfico o gráfico en la interfaz de usuario. No es necesario utilizar los siete colores si no necesita tantos colores distintos. Estos colores no se diseñaron para ser utilizados con ningún elemento de primer plano, por lo que no coloque texto o glifos encima de estos colores. Estos tonos deben estar codificados de forma rígida y exponerse a la personalización del usuario en **Herramientas > Opciones** (consulte Exposición de [colores para los usuarios finales).](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)

|Swatch|Hex|RGB|
|------------|---------|---------|
|![Muestra 71B252](../../extensibility/ux-guidelines/media/0711_71b252.png "0711_71B252")|#71B252|113,178,82|
|![Muestra BF3F00](../../extensibility/ux-guidelines/media/0711_bf3f00.png "0711_BF3F00")|#BF3F00|191,63,0|
|![Muestra FCB714](../../extensibility/ux-guidelines/media/0711_fcb714.png "0711_FCB714")|#FCB714|252,183,20|
|![Muestra 903F8B](../../extensibility/ux-guidelines/media/0711_903f8b.png "0711_903F8B")|#903F8B|144,63,139|
|![Muestra 117AD1](../../extensibility/ux-guidelines/media/0711_117ad1.png "0711_117AD1")|#117AD1|17,122,209|
|![Muestra 79D7F2](../../extensibility/ux-guidelines/media/0711_79d7f2.png "0711_79D7F2")|#79D7F2|121,215,242|
|![Muestra B5B5B5](../../extensibility/ux-guidelines/media/0711_b5b5b5.png "0711_B5B5B5")|#B5B5B5|181,181,181|

## <a name="on-object-ui-and-peeking"></a><a name="BKMK_OnObjectUI"></a>Interfaz de usuario en el objeto y miradas
 En esta sección se proporciona contexto a los peeking, también conocido como vista de vista de vista de código, un tipo de interfaz de usuario en el objeto exclusiva de Visual Studio.

### <a name="overview"></a>Información general

- La interfaz de usuario en el objeto debe proporcionar al usuario más información o interactividad sin menoscabo de su tarea principal.

- El patrón principal para la interfaz de usuario en el objeto en Visual Studio se conoce como "información en el punto de atención."

- La interfaz de usuario en el objeto en Visual Studio es en línea o flotante y es duradera o transitoria.

  - Vista de vista de código, un tipo de interfaz de usuario en el objeto en Visual Studio, es en línea y duradero.

  - CodeLens, un tipo de interfaz de usuario en el objeto en Visual Studio, es flotante y transitorio

  Comprender cómo funciona un fragmento de código o encontrar detalles sobre ese código, a menudo requiere que un desarrollador cambie de contexto e vaya a otro contenido u otra ventana. Estos cambios de contexto pueden ser perjudiciales, ya que los usuarios pueden perder el foco en su tarea original si abandonan su ventana principal. Además, recuperar ese contexto original puede ser difícil, especialmente si cambiar las ventanas hizo que su código original quedara oscurecido por otra interfaz de usuario.

  La interfaz de usuario en el objeto sigue un patrón denominado "información en el punto de atención." Estos mensajes, ventanas emergentes y cuadros de diálogo proporcionan a los usuarios información adicional y relevante que agrega aclaración o interactividad sin perder el foco en su tarea principal. Ejemplos de interfaz de usuario en el objeto incluyen ventanas emergentes que aparecen cuando un usuario pasa el puntero sobre un icono en el área de notificación, el ondulador rojo bajo una palabra mal escrita y la vista peek introducida en Visual Studio 2013.

### <a name="decision-points"></a>Puntos de decisión
 En Visual Studio, hay varias maneras de usar este patrón de información en el punto de atención. Elegir el mecanismo adecuado e implementarlo de una manera coherente y predecible es esencial para la experiencia general. De lo contrario, es posible que se presente a los usuarios una experiencia confusa o incoherente que resta atención al propio contenido.

#### <a name="relationships-between-master-and-detail-content"></a>Relaciones entre el contenido maestro y el contenido detallado
 La información en el punto de atención se utiliza para mostrar una relación entre el contenido en el que el usuario se centra (el contenido "maestro") y el contenido relacionado adicional (el contenido "detalle"). En este patrón, el contenido detallado está claramente relacionado con el contenido con el que el usuario está trabajando y se puede mostrar cerca del contenido maestro. La información suplementaria o la información que no se puede resumir sin sobrecargar el contenido maestro debe seguir otro patrón, como una ventana de herramientas.

- **Muestre siempre** el contenido detallado cerca del contenido maestro.

- **Asegúrese siempre** de que el contenido detallado todavía permite a un usuario permanecer centrado en el contenido maestro. A menudo, la mejor manera de lograr esto es representar el contenido de detalle lo más cerca posible del contenido maestro. Esto se puede hacer representando el contenido de detalle en una ventana emergente junto al contenido maestro, o representando el contenido de detalle en línea debajo del contenido maestro.

- **Nunca** utilice la información en el punto de atención que aleja al usuario del contenido maestro. Si los usuarios necesitan ver el contenido detallado por separado, exponga una acción explícita que permita al usuario hacerlo.

#### <a name="design-details"></a>Detalles de diseño
 Una vez que haya determinado que la interfaz de usuario en el objeto es la opción correcta, hay cuatro consideraciones de diseño principales:

1. **Persistencia:** ¿se espera que el contenido sea duradero o transitorio?
   ¿Desearán los usuarios mantener la información visible para hacer referencia o interactuar con ella? ¿O los usuarios querrán echar un vistazo rápidamente a la información y luego continuar con su tarea principal?

2. **Tipo de contenido:** ¿el contenido será informativo, procesable o navegable?
   ¿Necesita el usuario detalles adicionales sobre el contenido maestro? ¿Es necesario que el usuario complete una tarea que afecte al contenido maestro? ¿O es necesario dirigir al usuario a otro recurso?

3. Tipo de **indicador:** ¿tiene sentido un indicador ambiental?
   ¿Se puede resumir la información de una manera útil y mostrarse sin agobiar el contenido maestro?

4. **Gestos:** ¿qué gestos se usarán para invocar y descartar la interfaz de usuario?
   ¿Cómo mostrará el usuario el contenido detallado y lo enviará? ¿Hay valor en agregar un gesto como anclar para cambiar entre estados transitorios y duraderos?

   Cada uno de estos cuatro puntos de decisión tendrá un impacto en los componentes principales de la interfaz de usuario en el objeto.

### <a name="on-object-ui-components"></a>Componentes de interfaz de usuario en el objeto

1. Tipo de contenedor (presentador de contenido)

    - Flotante

    - En línea

2. Tipo de contenido

    - Informativo: datos que pueden ser estáticos o dinámicos

    - Accionable: comandos que cambian el contenido maestro

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

5. Indicadores ambientales (opcional)

    - Subrayado squiggle

    - Icono de etiqueta inteligente

    - Otros indicadores ambientales

#### <a name="container-content-presenter-type"></a>Tipo de contenedor (presentador de contenido)
 Hay dos opciones principales disponibles para presentar contenido en el punto de atención:

1. **En línea:** un presentador en línea, como la vista de vista que se introdujo en el Editor de código de Visual Studio 2013, hace espacio para el nuevo contenido cambiando el contenido existente.

    - **Prefiere** los presentadores en línea si espera que los usuarios quieran pasar una cantidad significativa de tiempo haciendo referencia o interactuando con el contenido que presenta.

    - **Evite los** presentadores en línea si espera que los usuarios quieran echar un vistazo a la información que presenta y, a continuación, continúe con su tarea principal con una interrupción mínima.

2. **Flotante:** un presentador flotante se coloca lo más cerca posible del contenido seleccionado, pero no altera el diseño del contenido existente. Se pueden emplear varias estrategias, como mostrar un panel de contenido flotante sobre el espacio en blanco disponible más cercano al símbolo seleccionado.

    - **Prefiere** los presentadores flotantes si espera que los usuarios quieran echar un vistazo a la información que presenta y, a continuación, continuar con su tarea principal con una interrupción mínima.

    - **Evite los** presentadores flotantes si espera que los usuarios quieran pasar una cantidad significativa de tiempo haciendo referencia o interactuando con el contenido que presenta.

#### <a name="content-type"></a>Tipo de contenido
 Hay tres tipos principales de contenido que se pueden mostrar dentro de cualquier contenedor de interfaz de usuario en el objeto. Se puede mostrar cualquier combinación de estos tipos de información. Los tres tipos son:

1. **Informativo: la** mayoría de los contenedores de interfaz de usuario en el objeto mostrarán algún tipo de contenido informativo. El contenido puede representar información sobre el estado actual del entorno o puede representar información sobre un posible estado futuro del entorno. Por ejemplo, podría utilizarse para mostrar el efecto de un comando determinado, como una refactorización, en el código existente.

    - **Utilice siempre** la representación canónica de la información que muestra. Por ejemplo, el código debe parecerse al código, con resaltado de sintaxis, y debe respetar cualquier fuente y otra configuración de entorno que el usuario haya establecido.

    - **Considere siempre** admitir cualquier acción sobre el contenido informativo que sería posible si esa misma información se presenta como contenido maestro. Por ejemplo, si presenta código existente dentro de un contenedor de interfaz de usuario en el objeto, considere la posibilidad de admitir la capacidad de examinar y modificar ese código.

    - **Considere siempre** el uso de un color de fondo diferente si presenta contenido informativo que representa un estado futuro potencial.

2. Accionable: algunos contenedores de interfaz de usuario en el objeto proporcionarán la capacidad de realizar alguna acción sobre el contenido maestro, como realizar una operación de refactorización.

    - **Coloque siempre** los comandos accionables por separado del contenido informativo.

    - **Habilite** y deshabilite siempre las acciones cuando corresponda.

    - **Consulte siempre** las directrices estándar para representar comandos dentro de los cuadros de diálogo.

    - **Mantenga siempre** el número de acciones que se exponen en un contenedor de interfaz de usuario en el objeto a un mínimo absoluto. Interactuar con la interfaz de usuario en el objeto debe ser una experiencia ligera y rápida. El usuario no debe tener que gastar energía en la administración del propio contenedor de interfaz de usuario en el objeto.

    - **Considere siempre** cómo y cuándo se cerrará o descartará un contenedor de interfaz de usuario en el objeto. Como práctica recomendada, cualquier acción que concluya el cuadro de diálogo entre el contenido maestro y el contenido de detalle también debe cerrar el contenedor de interfaz de usuario en el objeto cuando se invoca esa acción.

3. **Navegación:** algunos contenedores de interfaz de usuario en el objeto incluyen vínculos que llevan al usuario a otra ventana o aplicación, como abrir un artículo de MSDN en el explorador web del usuario.

    - **Siempre** anteponga cualquier enlace de navegación con "Abrir" para que los usuarios no se sorprendan al ser navegados a algún otro contenido.

    - **Separe siempre** los vínculos de navegación de los vínculos procesables.

#### <a name="ambient-indicators-optional"></a>Indicadores ambientales (opcional)
 Los indicadores ambientales pueden ser sutiles, incluido el texto presentado en un color de contraste del resto del código, o obvio, incluidos símbolos de tickler como subrayados ondulados e iconos de etiquetas inteligentes. Los indicadores ambientales comunican la disponibilidad de información adicional y relevante. Idealmente, proporcionan información útil incluso sin necesidad de que el usuario interactúe con ellos.

- **Coloque siempre** un indicador ambiental para que no distraiga ni abrume al usuario. Si es imposible colocar un indicador ambiental de tal manera, considere otra solución.

- **Coloque siempre** el indicador ambiental lo más cerca posible del contenido con el que está relacionado.

- **Trate siempre** de crear un indicador que resuma la información que pone a disposición. Considere la posibilidad de proporcionar un recuento del número de elementos de datos disponibles (por ejemplo, "3 referencias" en lugar de simplemente "Referencias") o pensar en alguna otra manera de resumir los datos.

  - En los casos en que los datos de un indicador no siempre se pueden calcular y mostrar, considere inmediatamente proporcionar comentarios progresivos a medida que se calculan los valores. Por ejemplo, considere la posibilidad de animar los cambios que reflejan las actualizaciones de los datos disponibles, de forma similar a la forma en que se actualiza el icono de correo electrónico en Windows Phone a medida que aumenta el número de correos electrónicos no leídos.

- **Nunca** agregue más indicadores de los que un usuario puede aceptar razonablemente para un determinado contenido. Los indicadores ambientales deben ser útiles sin necesidad de ninguna interacción del usuario. Los indicadores pierden su ambiente si requieren desbordamiento y otros controles de gestión para llevarlos a la vista.

#### <a name="gestures"></a>Gestos
 Un aspecto clave de permitir al usuario mantener el enfoque en el contenido maestro es apoyar los gestos correctos para abrir y descartar el contenido de detalle adicional.

- **Siempre** requiere que el usuario realice algún gesto explícito para abrir el contenido adicional. Los gestos abiertos comunes incluyen:

  - **Hover:** información sobre herramientas o contenido informativo no interactivo

  - **Comando explícito:** presentador en línea

  - **Haga doble clic en el indicador ambiental:** Ventana emergente CodeLens

- **Descarte siempre** el contenido detallado cada vez que el usuario presione la tecla Esc.

- **Considere siempre** el contexto de la interfaz de usuario en el objeto. Para los presentadores de contenido que permiten la interacción dentro del contenedor, considere cuidadosamente si desea mostrar información adicional al mantener el mouse, lo que probablemente sea perjudicial para el flujo de trabajo del usuario.

- **Nunca** muestre contenido al mantener el mouse que parezca editable o invite a la interacción del usuario. Este comportamiento puede frustrar a los usuarios si intentan mover el cursor sobre el contenido de detalle, ya que el comportamiento estándar de una información sobre herramientas es descartar inmediatamente cuando el cursor ya no está sobre el contenido maestro que lo produjo.

## <a name="selection-models"></a><a name="BKMK_SelectionModels"></a>Modelos de selección

### <a name="overview"></a>Información general
 Un modelo de selección es el mecanismo utilizado para indicar y confirmar operaciones en uno o varios objetos de interés dentro de la interfaz de usuario. En este tema se describen los patrones de interacción de selección en los editores de documentos de Visual Studio: editores de texto, superficies de diseño y superficies de modelado.

 Los usuarios deben tener una forma de indicar a Visual Studio en qué están trabajando y Visual Studio debe responder predeciblemente con comentarios a los usuarios sobre lo que está operando. Las diferencias o una comunicación incorrecta entre el usuario y la interfaz de usuario pueden dar lugar a que el usuario no se dé cuenta de una acción, que puede tener consecuencias no deseadas. A menudo, el error pasa desapercibido hasta que el usuario ve que falta algo o ha cambiado. Por lo tanto, los modelos de selección son una de las piezas más críticas del diseño de la interfaz de usuario. Aunque los modelos de selección en Visual Studio son coherentes con Windows, hay ligeras variaciones.

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
 El componente más importante de la selección es asegurarse de que el usuario sabe en qué ventana está trabajando (activación) y dónde se encuentra el foco (selección). Visual Studio amplía la funcionalidad de administración de ventanas en Windows, pero el esquema de activación es el mismo: interactuar con una ventana pone el foco en la ventana. Visual Studio tiene dos indicadores para la activación: uno para las ventanas de documento y otro para las ventanas de herramientas.

 Para las ventanas de documento, la ventana activa se indica mediante una pestaña de ventana de documento que viene al frente y cambia su color de fondo:

 ![Selección de pestaña activa en Visual Studio](../../extensibility/ux-guidelines/media/0713-01_activetab.png "0713-01_ActiveTab")

 **Selección activa de pestañas**

 Para las ventanas de herramientas, la ventana activa se indica mediante un cambio en el color del área de la barra de título de la ventana de herramientas:

 ![Selección de ventana de herramientas activa en Visual Studio](../../extensibility/ux-guidelines/media/0713-02_activetoolwindow.png "0713-02_ActiveToolWindow")

 **Ventana de herramientas activa que muestra la selección principal de un nodo**

 ![Selección de ventana de herramientas inactiva en Visual Studio](../../extensibility/ux-guidelines/media/0713-03_inactivetoolwindow.png "0713-03_InactiveToolWindow")

 **Ventana de herramientas inactiva, que muestra la selección latente del nodo**

 Una vez que una ventana está activa, su enfoque se indica de acuerdo con los modelos de selección descritos en esta sección de las directrices.

#### <a name="context"></a>Context
 Visual Studio se diseñó para conservar un concepto sólido de contexto, realizar un seguimiento de dónde está trabajando el usuario. Solo hay una ventana activa, ya sea una ventana de herramienta o de documento. Sin embargo, la ventana de documento superior siempre conserva una selección latente. Aunque el foco puede estar en una ventana de herramientas, la ventana de documento que estuvo activa por última vez muestra una selección, incluso en un estado inactivo. Esto se hace para conservar el contexto del usuario en el documento que estaban editando, mostrándoles que Visual Studio ha conservado su estado para que puedan volver y cambiar sin problemas entre las ventanas de herramientas y las ventanas de documento.

### <a name="text-selection"></a>Selección de texto
 Los editores de Visual Studio que son estrictamente textuales, como el editor de texto integrado, usan el mismo modelo de selección de texto y apariencia que se describe en la página [Mouse y punteros](/windows/desktop/uxguide/inter-mouse) de las directrices de interacción de la experiencia del usuario de Windows en MSDN. El foco de entrada en el editor de texto se indica mediante una barra vertical denominada punto de inserción. El punto de inserción es un solo píxel grueso y coloreado como el inverso de lo que aparece detrás de él. Parpadea según la velocidad establecida por el ajuste velocidad de **parpadeo del cursor** en la pestaña **Velocidad** del applet **Teclado** del Panel de control.

#### <a name="contiguous-and-disjoint-selection"></a>Selección contigua y desarticulada
 La selección dentro del editor de texto es solo contigua. Las selecciones de texto desarticuladas no están permitidas, pero deben abordarse en editores de objetos gráficos. Cuando el puntero del ratón del usuario está sobre un área de texto, el cursor cambia a una viga I. Un solo clic coloca el punto de inserción en el editor de texto en la ubicación de clic. Al mantener pulsado el botón del ratón se inicia un resaltado de selección y al soltar el botón del ratón se finaliza el resaltado de selección.

#### <a name="region-selection-box-selection"></a>Selección de región (selección de cuadro)
 Visual Studio admite selecciones de región en el editor de texto y esto se denomina selección de cuadro. La selección de cuadro permite al usuario seleccionar una región de texto que no sigue la secuencia de texto normal. Al igual que con la selección de texto estándar, la selección debe ser contigua. La selección de cuadros se inicia manteniendo pulsada la tecla Alt mientras arrastra con el ratón. La selección de cuadros también se puede iniciar manteniendo pulsadas las teclas Alt y Mayús mientras se utilizan las teclas de flecha para indicar la región de selección. La selección de cuadro utiliza el resaltado de selección normal y muestra el cursor del punto de inserción parpadeando al final del área de selección.

 ![Selección de&#41; de cuadro de &#40;regional en Visual Studio](../../extensibility/ux-guidelines/media/0713-04_boxselection.png "0713-04_BoxSelection")

 **Selección de región (cuadro) en Visual Studio**

#### <a name="text-selection-appearance"></a>Apariencia de selección de texto
 Los colores utilizados para la selección activa e inactiva en el editor se pueden personalizar. Para personalizar la apariencia visual del editor, un usuario puede ir a **Herramientas > Opciones**y, a continuación, buscar en Entorno > Fuentes y **colores > Editor**de texto .

### <a name="graphical-selection"></a>Selección gráfica

#### <a name="interaction"></a>Interacción
 La selección gráfica de objetos puede ser compleja y depende de una serie de factores:

- **Modelo de selección principal del editor.** Los editores que contienen objetos gráficos también se pueden utilizar para editar texto o cuadrículas. Por ejemplo, el editor podría ser un editor basado en texto que también admite la colocación de objetos gráficos, como el diseñador XAML de Visual Studio. La compatibilidad con varios tipos de objetos puede afectar a la forma en que el usuario selecciona grupos formados por diferentes tipos de objetos.

- **Compatibilidad con los estados de selección primarios y secundarios.** Un editor puede proporcionar estados de selección primarios y secundarios para que los objetos se puedan editar al unísono, alinearse entre sí, cambiar el tamaño entre sí, etc.

- **Soporte de edición in situ.** Los editores también pueden permitir que se edite el contenido de sus objetos gráficos. Por ejemplo, una forma de rectángulo también puede contener texto en el interior que el usuario puede cambiar. Además, ese texto podría centrarse o justificarse. La edición in situ implica un nivel más detallado de interacción del usuario y, por lo tanto, requiere un conjunto adecuado de indicaciones visuales para presentar información de estado al usuario.

#### <a name="mouse-interaction"></a>Interacción con el ratón

|Entrada|Resultado|
|-----------|------------|
|Haga clic en un objeto no seleccionado|Selecciona el objeto y muestra una línea discontinua y los identificadores de selección, si el objeto es redimensionable.|
|Haga clic en un objeto seleccionado|Activa la edición in situ si el objeto lo admite. Al hacer clic fuera del objeto se desactiva el modo de edición in situ.|
|Haga doble clic en un objeto|Abre el código detrás del objeto para su edición y podría insertar un controlador de eventos predeterminado, si procede.|
|Apuntar a un objeto|Cambia el puntero al cursor de movimiento. La apariencia del objeto, como su luminosidad o color, puede cambiar.|
|Señale un controlador de selección|Cambia el puntero al cursor de cambio de tamaño. Para los objetos que admiten la rotación, algunos identificadores de selección pueden cambiar el puntero a un cursor de rotación a medida que el puntero se coloca de forma diferente (por ejemplo, se mueve más lejos) con respecto al identificador de selección.|
|Arrastrar|Incluso si el objeto no está seleccionado previamente, cambia el puntero al cursor de movimiento y mueve el objeto.|
|Editor pierde el foco|Desactiva el modo de edición in situ, aunque el objeto conserva el contenido y la apariencia que tuvo durante su último estado de operación/selección.|
|Selección de objetos|Indicado por un borde, una línea punteada u otro tratamiento visualmente distinto para resaltar el límite del objeto.|
|Cambiar el tamaño de un objeto seleccionado|Indicado por los controladores de selección.<br /><br /> Un objeto redimensionable tiene ocho identificadores, que representan cada dirección en la que se puede cambiar el tamaño. Se pueden utilizar menos identificadores si el objeto solo se puede cambiar de tamaño en determinadas direcciones. Cuando el usuario ajusta el tamaño de un objeto hasta donde ocho identificadores no serían interactivos, se pueden usar cuatro identificadores. Los tamaños de los identificadores deben estar vinculados a las métricas de borde y borde de la ventana con la función de API **GetSystemMetrics** para que el tamaño sea proporcional a la resolución de pantalla.<br /><br /> ![Controladores de tamaño](../../extensibility/ux-guidelines/media/0713-05_resizehandles.png "0713-05_ResizeHandles")|
|Girar un objeto seleccionado|![Controladores de giro](../../extensibility/ux-guidelines/media/0713-06_rotate.png "0713-06_Rotate")|

#### <a name="keyboard-interaction"></a>Interacción con el teclado

|Entrada|Resultado|
|-----------|------------|
|Pestaña|Mueve el indicador de enfoque entre el orden lógico de los objetos en el editor. Esto puede ser de izquierda a derecha o de arriba a abajo dependiendo del valor de la propiedad **TabIndex** (o equivalente), el orden de creación del objeto y el propósito general del editor. Mayús+Tab invierte la dirección del indicador de enfoque.|
|Barra espaciadora|Activa el modo de panorámica mientras se mantiene la pulsación de tecla. Se requiere una entrada adicional del ratón para desplazar la posición de la ventana gráfica.|
|Ctrl+Barra espaciadora|Activa el modo de zoom mientras se mantiene la pulsación de tecla. Se requiere una entrada adicional del ratón para aumentar y disminuir el factor de zoom.|
|Ctrl+Alt+Signo menos|Disminuye el factor de zoom en un nivel.|
|Ctrl+Alt+Signo Más|Aumenta el factor de zoom en un nivel.|
|Mayús O Ctrl|Agrega el objeto al grupo de selección. Ctrl también le permite eliminar objetos individualmente del grupo de selección.|
|Escriba|Realiza el comando predeterminado para el objeto (normalmente Abrir o Editar).|
|F2|Activa la edición in situ para el objeto.|
|Teclas de dirección|Mueve los objetos seleccionados en la dirección de la tecla de flecha pulsada, en pequeños incrementos (por ejemplo, 1 píxel a la vez)|
|Ctrl+teclas de flecha|Mueve los objetos seleccionados en la dirección de la tecla de flecha pulsada, en incrementos más grandes (por ejemplo, 10 píxeles a la vez)|
|Teclas Mayús+flecha|Cambia el tamaño de los objetos seleccionados en la dirección respectiva, en pequeños incrementos (por ejemplo, 1 píxel a la vez)|
|Ctrl+Mayús+teclas de flecha|Cambia el tamaño de los objetos seleccionados en la dirección respectiva, en incrementos más grandes (por ejemplo, 10 píxeles a la vez)|

 Cuando los usuarios editan los controles en su lugar, puede tener sentido que los objetos cambie de tamaño automáticamente con la entrada del usuario. Por ejemplo, si el usuario edita un control de etiqueta, la etiqueta debe crecer para mostrar el texto que el usuario acaba de escribir. Si esto no se hace, el usuario debe cambiar el tamaño del control manualmente después de editar el texto. Si el usuario tiene muchos controles, esto se convierte en una tarea de sorción e improductiva.

#### <a name="graphical-containers"></a>Contenedores gráficos
 En algunos casos, los editores gráficos proporcionan contenedores para otros objetos gráficos, como el control Panel de formularios Windows Forms o el control Diseño de cuadrícula en el diseñador HTML. Si el editor proporciona contenedores para otros objetos gráficos, se debe utilizar el siguiente modelo de selección solo para el contenedor (los objetos dentro del contenedor siguen el modelo estándar como se ha descrito anteriormente):

|Entrada|Resultado|
|-----------|------------|
|Un solo clic en el contenedor|Selecciona el objeto contenedor sin seleccionar directamente ninguno de los objetos contenidos. El contenedor se puede mover y/o cambiar de tamaño con la entrada estándar del ratón y el teclado (como se describió anteriormente). Los objetos contenidos se mueven en relación con el contenedor, pero los objetos contenidos no se redimensionan a menos que también se seleccionen directamente.|
|Pase el cursor sobre la región límite del contenedor|Convierte el ratón en el cursor de movimiento, lo que indica que se puede mover el contenedor.|
|Arrastre la región de límite del contenedor|Cambia el ratón al cursor de movimiento y mueve el contenedor (y los objetos contenidos dentro). El contenedor no se puede mover sin seleccionarse primero con un solo clic.|
|Haga un solo clic en un objeto dentro del contenedor|Anula la selección del contenedor (si está seleccionado) y selecciona solo el objeto en el que se ha clic.|
|Mayús+clic o pulse O Ctrl+clic en un objeto y/o contenedor contenidos|Agrega el objeto en el que se ha clic a una selección o grupo de selección existente. Si el objeto en el que se ha hecho clic ya es miembro del grupo de selección, se elimina del grupo de selección.|

 Los objetos contenidos deben adherirse al modelo de selección básico como se describe en la sección anterior. A partir de las pruebas de usabilidad del diseñador de Windows Forms, los usuarios esperaban un acceso sin problemas a los objetos contenidos sin pasos intermedios (impuestos por el objeto de contención).

#### <a name="disjoint-and-region-selections"></a>Selección desarticulada y de región
 Los editores de objetos gráficos deben admitir selecciones desarticuladas. Tenga en cuenta que este gráfico no muestra la apariencia del control para Visual Studio. Consulte Apariencia de selección de [objetos gráficos](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_GraphicalObjectSelectionAppearance) para obtener especificaciones visuales detalladas.

 ![Selectores de región y discontinuos](../../extensibility/ux-guidelines/media/0713-07_disjointregionselectors.png "0713-07_DisjointRegionSelectors")

 **Selección desarticulada**

 Los editores gráficos también deben proporcionar selecciones de región con un indicador de selección de tipo marco. Si el editor gráfico admite otros tipos de objetos (como texto), es posible que las selecciones de región no sean posibles en función de las restricciones de esos otros tipos de objeto.

 ![Selección de recuadro](../../extensibility/ux-guidelines/media/0713-08_marqueeselection.png "0713-08_MarqueeSelection")

 **Selección de recuadro**

#### <a name="primary-and-secondary-selections"></a>Selecciones primarias y secundarias
 Algunos editores gráficos de objetos permiten al usuario editar o alinear objetos en grupos. En este caso, es necesario introducir el concepto de selecciones primarias y secundarias. La selección principal es el objeto al que responden todos los demás objetos para las operaciones de grupo. El objeto que el usuario selecciona primero se convierte en el control principal y las selecciones posteriores se convierten en las selecciones secundarias. La selección primaria tiene un tratamiento visual distinto de la(s) selección(es) secundaria(s) para indicar qué objeto es primario:

 ![Selección primaria y secundaria](../../extensibility/ux-guidelines/media/0713-09_primarysecondary.png "0713-09_PrimarySecondary")

 **Selección primaria con dos selecciones secundarias**

#### <a name="graphical-object-selection-appearance"></a><a name="BKMK_GraphicalObjectSelectionAppearance"></a>Apariencia de selección de objetos gráficos
 Los controladores de selección son cuadrados dibujados en un patrón rectangular alrededor del cuadro delimitador del objeto. El gráfico siguiente muestra ejemplos de los distintos estados que un objeto gráfico puede tener con el identificador, el tamaño y la apariencia de edición in situ. El tamaño de los identificadores debe estar vinculado a las métricas de borde y borde de la ventana mediante la API **GetSystemMetrics.**

| State | Apariencia | Detalles visuales |
|-------------------------|---------------| - |
| **No seleccionado** | Valor predeterminado | ![Estado de botón predeterminado](../../extensibility/ux-guidelines/media/0713-10_defaultstate.png "0713-10_DefaultState") |
| **Selección primaria** | Redimensionable | ![Selección primaria con controladores de tamaño](../../extensibility/ux-guidelines/media/0713-11_primaryresize.png "0713-11_PrimaryResize") |
| **Selección primaria** | No redimensionable | ![Selección primaria sin controladores de tamaño](../../extensibility/ux-guidelines/media/0713-13_primarynoresize.png "0713-13_PrimaryNoResize") |
| **Selección primaria** | Bloqueado | ![Selección primaria bloqueada](../../extensibility/ux-guidelines/media/0713-15_primarylocked.png "0713-15_PrimaryLocked") |
| **Selección secundaria** | Redimensionable | ![Selección primaria con controladores de tamaño](../../extensibility/ux-guidelines/media/0713-17_secondaryresize.png "0713-17_SecondaryResize") |
| **Selección secundaria** | No redimensionable | ![Selección secundaria sin controladores de tamaño](../../extensibility/ux-guidelines/media/0713-19_secondarynoresize.png "0713-19_SecondaryNoResize") |
| **Selección secundaria** | Bloqueado | ![Selección secundaria bloqueada](../../extensibility/ux-guidelines/media/0713-21_secondarylocked.png "0713-21_SecondaryLocked") |
| **Interfaz de usuario activa** | Valor predeterminado | ![Estado activo de interfaz de usuario](../../extensibility/ux-guidelines/media/0713-23_uiactive.png "0713-23_UIActive") |

### <a name="view-selection-models"></a>Ver modelos de selección

#### <a name="tree-view"></a>Vista de árbol
 La selección en una vista de árbol se muestra con un resaltado simple. Si el usuario hace clic en un nombre de nodo o un icono de nodo, el nodo se selecciona. Los glifos triangulares a la izquierda del nodo expanden o contraen el control de árbol, pero no afectan a la selección del usuario, con una excepción: al contraer un nodo primario cuando la selección está en un elemento secundario de ese nodo, la selección se mueve al elemento primario.

 ![Vista de árbol típica de Visual Studio](../../extensibility/ux-guidelines/media/0713-25_treeview.png "0713-25_TreeView")

 **Vista de árbol típica de Visual Studio**

 Las vistas de árbol pueden admitir selecciones contiguas y desarticuladas, incluso en varios niveles del árbol. Se deben realizar selecciones múltiples contiguas o desarticuladas en nodos de árbol visibles. Si se contrae un nodo, se pierde la selección desarticulada y el nodo contraído obtiene la selección. De esta manera, el usuario puede ver los nodos que se verán afectados por una operación. Cuando los nodos se contraen, no está claro qué nodos podrían verse afectados.

 Cuando se selecciona un nodo primario, la operación debe aplicarse al elemento primario, aunque puede haber casos en los que tenga sentido que una operación se aplique al elemento primario y a todos sus elementos secundarios. En este caso, proporcione una interfaz de usuario adicional durante la operación, como una casilla de verificación o un cuadro de diálogo de confirmación para que la opción "aplicar a todos los elementos secundarios" sea explícita para el usuario.

##### <a name="renaming"></a>Cambiar nombre
 Si los nodos del árbol admiten el cambio de nombre, el cambio de nombre debe realizarse en su lugar. La operación en el lugar debe ser el estándar en todos los controles de árbol en Visual Studio. Proporcione un comando de cambio de nombre que active inmediatamente el modo de edición in situ, con la selección de texto que cubre todo el nombre del nodo, listo para aceptar la entrada del usuario. Si el nodo representa un archivo, el nombre de archivo debe contener la extensión. El resaltado de selección debe incluir solo el cuerpo del nombre de archivo y no la extensión.

|Entrada|Resultado|
|-----------|------------|
|Entrar (tecla)|Confirma la operación de cambio de nombre|
|Tecla Esc|Cancela la operación de cambio de nombre|
|Hacer clic fuera de la región de edición in situ|Confirma la operación de cambio de nombre|
|Deshacer|Proporcionar fácil deshacer para cancelar la operación de cambio de nombre|

#### <a name="selection-within-lists-and-grid-controls"></a>Selección dentro de listas y controles de cuadrícula
 El concepto clave en la selección de lista es que se basa en filas, lo que significa que cuando se realiza una selección, toda la fila se selecciona como una unidad. Por el contrario, las cuadrículas pueden permitir que se seleccionen celdas específicas sin afectar a ningún otro aspecto de la fila. Las cuadrículas también pueden contener una jerarquía de filas anidadas (como en un TreeGrid) que permiten seleccionar y anular la selección de ramas enteras de la jerarquía mediante la interacción con las filas primarias. La selección en las listas se muestra con un color de resaltado simple en toda la fila de datos. El foco se muestra mediante un borde punteado de un solo píxel alrededor de la fila o celda editable actual (fila si todas las celdas son de solo lectura).

> [!NOTE]
> **El enfoque** y la **selección** son conceptos diferentes. *Focus* es una indicación de qué elemento de interfaz de usuario está destinado a recibir entradas no dirigidas explícitamente a otro objeto, mientras que la *selección* hace referencia al estado de la inclusión de un objeto en un conjunto de objetos en el que pueden tener lugar operaciones posteriores.

 Las selecciones en las listas pueden ser contiguas, desarticuladas o regiones. Cuando se permiten varias selecciones, siempre se debe admitir la selección contigua y desarticulada, mientras que la compatibilidad con selecciones de región (cuadro) es opcional. Las selecciones de región se inician arrastrando en el espacio en blanco del cuerpo de la lista.

| Object | Número de selección |
|--------|------------|
| List | Contiguos |
| List | Desunido |
| List | Region |

 Al hacer clic una vez en una lista, se selecciona la fila en la que se produjo el clic. Si el usuario hace clic en una celda de lista que admite la edición in situ, la celda también se activa inmediatamente para la edición in situ. De lo contrario, toda la fila se selecciona inmediatamente y muestra un resaltado.

 Arrastrar en el cuerpo de la lista hace una de tres cosas:

- Inicia una selección de región si la lista lo admite y el ratón hacia abajo está en el espacio en blanco

- Inicia una operación de arrastrar/soltar si la celda o fila de lista admite ser un origen de arrastre

- Selecciona la fila actual

##### <a name="in-place-editing"></a>Edición in situ
 Cuando se permite la edición in situ, hay dos modelos básicos: control de edición simple y selector de propiedades. Con un control de edición simple, el contenido se resalta y está listo para la entrada del usuario tan pronto como se activa la edición in situ. Cuando se implementa un selector de propiedades, el botón que invoca el selector de propiedades se muestra una vez que se activa el modo de edición en contexto y la selección actual no se resalta. El botón del selector debe estar justificado a la derecha en la celda. Para obtener ejemplos de edición in situ, vea la **ventana Propiedades** y **la lista** de tareas en Visual Studio.

##### <a name="keyboard-support"></a>Compatibilidad con el teclado
 La compatibilidad con teclado para la selección en listas y cuadrículas sigue las convenciones estándar de Windows:

- Las teclas de flecha navegan por la lista, seleccionando cada fila/celda a medida que se mueve el foco.

- Mayús + flecha realiza una selección contigua en la dirección de las teclas de flecha.

- Ctrl + flecha seguida de barra espaciadora alterna entre agregar y eliminar elementos de lista de la selección, creando una selección desarticulada.

- Para las cuadrículas que contienen jerarquías anidadas, la tecla Flecha derecha expande una fila primaria y la tecla Flecha izquierda contrae una.

- La tecla Tabulador mueve el foco entre las celdas de la fila actual si las celdas son editables.

- La tecla Intro realiza el comando predeterminado en el elemento de la lista (a menudo **Abrir**).

- La tecla F2 activa la edición in situ para la celda seleccionada actualmente.

## <a name="persistence-and-saving-settings"></a><a name="BKMK_PersistenceAndSavingSettings"></a>Configuración de persistencia y ahorro

### <a name="overview"></a>Información general
 Aunque cada componente de software de Visual Studio suele ser responsable de su propio estado y persistencia, Visual Studio guarda automáticamente la configuración en algunos casos, como con los tamaños y las posiciones de las ventanas. La siguiente tabla es una combinación de ajustes guardados automáticamente y ajustes que requieren que se realice una acción explícita del usuario o programada.

|Object|Qué ahorrar|Cuándo guardar|Dónde ahorrar|
|------------|------------------|------------------|-------------------|
|Objeto seleccionable (por ejemplo, una línea de código)|Un punto de interrupción en una línea de código<br /><br /> Un acceso directo de usuario asociado a la línea de código|Cuando se guarda el proyecto|El archivo de opciones de **usuario (.suo)** para el proyecto|
|Diálogo|La ubicación del diálogo, si se hubiera movido<br /><br /> La vista que el usuario utilizó por última vez en el cuadro de diálogo|Cuando se cierra el cuadro de diálogo<br /><br /> Cuando finaliza la sesión de Visual Studio|En la memoria<br /><br /> Registro en **HKEY_Current_User**|
|Periodo|El tamaño y la ubicación de la ventana|Cuando se cierra la ventana<br /><br /> Cuando cambia el modo de Visual Studio<br /><br /> Cuando finaliza la sesión de Visual Studio|El archivo de opciones de **usuario (.suo)** para el proyecto<br /><br /> Archivo de opciones personalizadas para la configuración de la ventana|
|Documento|La selección actual en el documento<br /><br /> La vista del documento<br /><br /> Los últimos lugares que el usuario visitó|Cuando se guarda el documento|El archivo de opciones de **usuario (.suo)** para el proyecto|
|proyecto|Referencias a archivos<br /><br /> Referencias a directorios en disco<br /><br /> Referencias a otro software<br /><br /> Componentes<br /><br /> Información del estado sobre el propio proyecto|Cuando se guarda el proyecto|El archivo del proyecto|
|Solución|Referencias a proyectos<br /><br /> Referencias a archivos|Cuando se guarda el proyecto o la solución|El archivo de **solución (.sln)**|
|Configuración en **Herramientas > Opciones**|Personalizaciones del teclado<br /><br /> Personalizaciones de la barra de herramientas<br /><br /> Esquemas de color|Cuando se cierra el cuadro de diálogo **Herramientas > Opciones**<br /><br /> Cuando finaliza la sesión de Visual Studio|Registro en **HKEY_Current_User**|

 Lo que el usuario está haciendo, y cuando lo está haciendo, dicta si una configuración se está guardando en la memoria (durante la sesión), se guarda en el disco (entre sesiones como una configuración del Registro), como parte del propio archivo de proyecto o solución, como parte del archivo de opciones de **solución (.suo)** o como un archivo de configuración personalizado que solo ese componente de software conoce. La tabla anterior muestra varios eventos en los que se puede guardar la configuración. Sin embargo, hay otras veces en las que es posible que desee guardar el estado:

- Cuando el usuario cambia de ubicación dentro de un cuadro de diálogo o ventana

- Cuando el usuario transfiere el foco a otra ventana

- Cuando el usuario cambia de diseño a modo de depuración

- Cuando el usuario cierra la sesión de su cuenta

- Cuando el equipo entra en hibernación o se apaga

- Cuando el ordenador/disco duro está a punto de ser reformateado y configurado de nuevo

### <a name="window-configurations"></a>Configuraciones de ventanas
 Una configuración de ventana es la presentación básica del entorno de desarrollo - es un esquema que consiste en la lista de ventanas de herramientas presentes y la forma en que se organizan. Para las ventanas administradas por el IDE (ventanas IDE), la información de diseño se conserva por usuario, por lo que cuando un usuario inicia el IDE, el diseño de ventana aparece igual que cuando salió por última vez de Visual Studio. El estado y la posición de las ventanas IDE se conservan en un archivo de opciones personalizado en formato XML. Las ventanas de herramientas creadas por paquetes cargados en el IDE conservan su información de estado en el registro y pueden o no ser por usuario.

#### <a name="profile-specific-layouts"></a>Diseños específicos del perfil
 Cada perfil incluye diseños de ventana de herramientas, organizados de una manera familiar para personas de desarrolladores específicos (los desarrolladores de Visual C++ esperan ver el **Explorador** de soluciones en el lado izquierdo del IDE, mientras que los desarrolladores de C- esperan ver el **Explorador** de soluciones a la derecha). Los diseños de ventana específicos del perfil se cargan después de que el usuario elija un perfil al iniciarse. Un autor de paquete debe determinar el diseño de ventana más adecuado para la experiencia de su cliente, sabiendo que los cambios que el usuario realice en la configuración de la ventana se conservarán.

## <a name="touch-input"></a><a name="BKMK_TouchInput"></a>Entrada táctil
 Los usuarios utilizan cada vez más productos de desarrollo de Microsoft en dispositivos táctiles. Sin embargo, hay barreras que dificultan el uso de herramientas de desarrollo en dispositivos táctiles. Los usuarios esperarán que nuestros productos proporcionen una experiencia táctil fiable y precisa. La intención de estas directrices es informar a las decisiones sobre qué capacidades táctiles incorporar y fomentar una experiencia táctil coherente en Visual Studio y productos relacionados.

### <a name="levels-of-experience"></a>Niveles de experiencia
 Los siguientes niveles de experiencia están destinados a servir como una guía para ayudar a los equipos a decidir qué capacidades táctiles ofrecer en función del nivel deseado de interés de inversión en contacto.

- La **experiencia básica** es para los equipos que quieren proporcionar capacidades táctiles para que no haya callejones sin salida a lo largo de su trabajo.

- La **experiencia optimizada** es para los equipos que desean proporcionar las capacidades táctiles más comunes (por ejemplo, las que normalmente están disponibles en aplicaciones de explorador de Internet).

- La **experiencia elevada** es para los equipos que desean agregar capacidades como gestos u otras capacidades opcionales que pueden hacer que su aplicación sea amigable con el tacto primero.

||Experiencia básica|Experiencia optimizada|Experiencia elevada|
|-|----------------------|--------------------------|-------------------------|
|Permite a los usuarios ...|Corregir código y lectura a nivel de solución/proyecto sin callejones sin salida|Realizar tareas de mantenimiento, refactores y navegación|Opere con una experiencia consistente, intuitiva y fluida con confianza|
|Editor|Toque panorámica y selección<br /><br /> Desplazamientoto de la barra de desplazamiento para saltar y pulse +arrastrar|Zoom de pellizco<br /><br /> Desplazamiento rápido<br /><br /> Número de selección<br /><br /> Fácil uso del menú contextual||
|Ventanas de herramientas superiores|Lista de panoramización<br /><br /> Selección de elementos<br /><br /> Desplazamientoto de la barra de desplazamiento para saltar y pulse +arrastrar|Fácil desplazamiento y selección de elementos||
|Basado en ventanas||Ventana de cambio de tamaño<br /><br /> Acceso rápido||
|Documento bien||Fácil navegación entre archivos abiertos||
|Gestos||Asegúrese de que los gestos comunes funcionen en todo el IDE|Acciones basadas en gestos<br /><br /> Soporte de arrastrar y soltar y diseñadores|
|Otras consideraciones|||Teclado en pantalla personalizado|

#### <a name="gestures"></a>Gestos
 Los gestos proporcionan a los usuarios un acceso directo a los comandos que, de lo contrario, podrían requerir una interacción más complicada. Consulte las directrices de Windows sobre [gestos táctiles comunes para aplicaciones](/windows/desktop/wintouch/windows-touch-gestures-overview)de escritorio y siga esta guía para la mayoría de los gestos, incluidos los gestos simples, como el desplazamiento panorámico y el zoom.
