---
title: "Patrones compuestos para Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e48ecfb2-f4b5-4d3a-b4a2-7a4d62fa4ec0
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# Patrones compuestos para Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Los patrones compuestos combinan elementos de interacción y diseño de configuraciones distintas. Algunos de los patrones compuestos más importantes en Visual Studio con respecto a la coherencia incluyen:  
  
-   [Visualización de datos](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_DataVisualization)  
  
-   [Interfaz de Usuario y leerlo de objeto](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)  
  
-   [Modelos de selección](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)  
  
-   [Persistencia y guardar la configuración](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)  
  
-   [Entrada táctil](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)  
  
##  <a name="a-namebkmkdatavisualizationa-data-visualization"></a><a name="BKMK_DataVisualization"></a> Visualización de datos  
  
### <a name="overview"></a>Información general  
 Los gráficos son una manera visual para agregar y visualizar datos con el fin de mejorar la toma de decisiones. Pueden ayudar a los usuarios que se enfrentan con gran cantidad de datos, pero lo que significa poco vea lo que merece atención y qué necesita una acción.  
  
 El usuario se beneficiará de un gráfico si se cumple alguna de las condiciones siguientes:  
  
-   ¿El gráfico ayudará a los usuarios identificar las tareas que pueden actuar en?  
  
-   ¿El gráfico permiten a los usuarios las consecuencias de posibles cambios de previsión?  
  
-   ¿El gráfico ayudará a los usuarios descubrir tendencias e identificar patrones?  
  
-   ¿El gráfico permite a los usuarios tomar decisiones mejor?  
  
-   ¿El gráfico ayudará a responder a preguntas específicas que los usuarios pueden tener en el contexto determinado?  
  
#### <a name="general-rules-for-charts"></a>Reglas generales para gráficos  
  
-   Claramente los datos de etiqueta. Ilustraciones sin explicación sólo son prácticamente imágenes.  
  
-   Iniciar ejes en cero para evitar sesgar proporciones. Tamaño de longitud y barra de línea son importantes indicaciones visuales para comprender las relaciones entre los puntos de datos.  
  
-   Crear gráficos, no infografías. Infografías son artísticos representaciones de datos, y su objetivo principal es storytelling visual. Gráficos pueden (y deben) ser visualmente atractivas, pero permitir que los datos hablen por sí mismos.  
  
-   Evite skeumorphism, gráficos de barras gráficas, contraste hashmarks y otros toques infografía.  
  
-   No utilice efectos 3D como elemento decorativo. Utilizar solo si se realmente parte integral de la capacidad del usuario para comprender la información.  
  
-   Evite el uso de varias líneas y rellenos, ya que más de dos colores pueden este tipo de gráfico difícil de leer e interpretar correctamente.  
  
-   No use un gráfico (o cualquier ilustración) como el único medio de comprender un concepto o interactuar con los datos. Esto presenta dificultades para los usuarios con discapacidades visuales.  
  
-   No utilice gráficos como elementos decorativos o innecesarias en una página. En otras palabras, si no agrega un gráfico de que los usuarios ayuda o valor solucionar un problema, no usarlo.  
  
### <a name="chart-types"></a>Tipos de gráficos  
 Tipos de gráficos que se utilizan en Visual Studio incluyen gráficos de barras, gráficos de líneas, un gráfico circular modificado conocido como un gráfico de anillos o "gráfico de anillos", las escalas de tiempo, de dispersión (también denominados "gráficos del clúster") de gráficos y diagramas de Gantt. Cada tipo de gráfico es útil para la comunicación de un tipo diferente de información.  
  
### <a name="other-charting-considerations"></a>Otras consideraciones sobre la creación de gráficos  
  
#### <a name="color"></a>Color  
 Hay una paleta específica de los gráficos de colores definidos para su uso en Visual Studio. La paleta está accesible para los tipos principales de daltonismo y los colores se pueden diferenciar incluso cuando se utiliza como sectores muy estrechos de color. Puede usar estos colores en cualquier combinación de cualquier tipo de gráfico o en la interfaz de Usuario. No es necesario utilizar todos los colores de siete si no necesita tantos colores distintos. Estos colores no se diseñaron para usarse con los elementos de primer plano, por lo que no incluya texto o glifos sobre estos colores. Estos tonos deben codificado de forma rígida y expone a la personalización del usuario en **Herramientas > opciones** (consulte [exponer colores para los usuarios finales](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)).  
  
|Muestra|Hexadecimal|RGB|  
|------------|---------|---------|  
|![Muestra 71B252](../../extensibility/ux-guidelines/media/0711_71b252.png "0711_71B252")|#71B252|113,178,82|  
|![Muestra BF3F00](../../extensibility/ux-guidelines/media/0711_bf3f00.png "0711_BF3F00")|#BF3F00|191,63,0|  
|![Muestra FCB714](../../extensibility/ux-guidelines/media/0711_fcb714.png "0711_FCB714")|#FCB714|252,183,20|  
|![Muestra 903F8B](../../extensibility/ux-guidelines/media/0711_903f8b.png "0711_903F8B")|#903F8B|144,63,139|  
|![Muestra 117AD1](../../extensibility/ux-guidelines/media/0711_117ad1.png "0711_117AD1")|#117AD1|17,122,209|  
|![Muestra 79D7F2](../../extensibility/ux-guidelines/media/0711_79d7f2.png "0711_79D7F2")|#79D7F2|121,215,242|  
|![Muestra B5B5B5](../../extensibility/ux-guidelines/media/0711_b5b5b5.png "0711_B5B5B5")|#B5B5B5|181,181,181|  
  
##  <a name="a-namebkmkonobjectuia-on-object-ui-and-peeking"></a><a name="BKMK_OnObjectUI"></a> Interfaz de Usuario y leerlo de objeto  
 Esta sección proporciona contexto para leerlo, también conocido como vista de inspección de código, un tipo de objeto de interfaz de Usuario exclusivo de Visual Studio.  
  
### <a name="overview"></a>Información general  
  
-   Interfaz de Usuario de objeto debe dar al usuario más información o interactividad sin apartarse de su tarea principal.  
  
-   El patrón principal para la interfaz de Usuario de objeto en Visual Studio se conoce como "información en el momento de atención".  
  
-   Interfaz de Usuario de objeto en Visual Studio es ya sea en línea o flotante y duradero o transitoria.  
  
    -   Vista de inspección de código, un tipo de interfaz de Usuario de objeto en Visual Studio, es duradera y en línea.  
  
    -   CodeLens, un tipo de interfaz de Usuario de objeto en Visual Studio, es transitorio y flotante  
  
 Comprender cómo funciona un fragmento de código, o buscar detalles sobre dicho código, a menudo requiere un programador cambiar el contexto e ir a otro contenido o en otra ventana. Estos cambios de contexto pueden ser perjudiciales, ya que los usuarios pueden perder centrarse en su tarea original si abandonan su ventana principal. Además, la obtención de que copia original de contexto puede ser difícil, especialmente si el cambio entre ventanas provocó el código original para estar oscurecidas por otras interfaces de Usuario.  
  
 Interfaz de Usuario en el objeto sigue un patrón denominado "información en el momento de atención". Estos mensajes, ventanas emergentes y cuadros de diálogo de proporcionan a los usuarios información adicional relevante que agrega alguna aclaración o interactividad sin perder el foco en su tarea principal. Algunos ejemplos de interfaz de Usuario de objeto son ventanas emergentes que aparecen cuando un usuario desplaza el puntero sobre un icono en el área de notificación, la línea ondulada roja bajo una palabra mal escrita y la vista de peek introducidas en Visual Studio 2013.  
  
### <a name="decision-points"></a>Puntos de decisión  
 En Visual Studio, hay varias maneras de utilizar este modelo de información en el momento de atención. Elegir el mecanismo adecuado e implementación de una manera coherente y predecible es esencial para la experiencia general. De lo contrario, los usuarios podrían presentarse con una experiencia incoherente o confusa que se resienta el foco desde el propio contenido.  
  
#### <a name="relationships-between-master-and-detail-content"></a>Relaciones entre maestro y detalles de contenido  
 Información en el momento de la atención se utiliza para mostrar una relación entre el contenido que el usuario está centrado en (el contenido de "master") y adicionales relacionados (el contenido de "Detalles"). En este modelo, el contenido de detalle es claramente relacionada con el contenido que está trabajando con el usuario y se puede mostrar cerca del contenido principal. Información adicional o información que no se pueden resumir sin sobrecargar el contenido principal debe seguir otro patrón, como una ventana de herramientas.  
  
-   **Siempre** Mostrar el contenido de detalle cerca del contenido principal.  
  
-   **Siempre** Asegúrese de que el contenido de detalle permite un usuario permanezcan centrados en el contenido principal. A menudo, la mejor manera de lograr esto es representar el contenido de detalle como cerca el contenido principal como sea posible. Esto puede hacerse al representar el contenido de detalle en una ventana emergente junto al contenido principal o al representar el detalle contenido en línea debajo del contenido principal.  
  
-   **Nunca** utilizar la información en el momento de la atención que lleva al usuario fuera el contenido principal. Si los usuarios necesitan ver el contenido de detalle por separado, exponer una acción explícita que permite al usuario hacer esto.  
  
#### <a name="design-details"></a>Detalles de diseño  
 Una vez que haya determinado que la interfaz de Usuario de objeto es la elección correcta, hay cuatro consideraciones de diseño principal:  
  
1.  **Persistencia:** el contenido debe ser duradero o temporal?   
    ¿Se desean mantener visible para hacer referencia a o interactuar con la información? ¿O bien, los usuarios desearán rápidamente Eche un vistazo a la información y, a continuación, continúe con su tarea principal?  
  
2.  **¿Tipo de contenido:** el contenido será informativo, procesables o navegación?   
    ¿El usuario necesita información adicional sobre el contenido principal? ¿El usuario necesita completar una tarea que afecta al contenido principal? ¿O bien, el usuario deberá dirigirse a otro recurso?  
  
3.  **¿Tipo de indicador:** tiene un indicador de ambiente sentido?   
    ¿Puede la información de resumen de una manera útil y mostrar sin sobrecargar el contenido principal?  
  
4.  **Movimientos:** gestos de lo que se usará para invocar y descartar la interfaz de Usuario?   
    ¿Cómo mostrar el contenido de detalle y enviarlo inmediatamente al usuario? ¿Existe valor al agregar un gesto como fijación para cambiar entre los estados transitorios y duraderos?  
  
 Cada uno de estos puntos de cuatro decisión tendrá un impacto en los principales componentes de interfaz de Usuario del objeto.  
  
### <a name="on-object-ui-components"></a>Componentes de interfaz de Usuario de objeto  
  
1.  Tipo de contenedor (ranura de contenido)  
  
    -   Flotante  
  
    -   Alineado  
  
2.  Tipo de contenido  
  
    -   Información: los datos que pueden ser estática o dinámica  
  
    -   Procesables: comandos que cambian el contenido principal  
  
    -   Navegación: vínculos que llevará al usuario a otra ventana o aplicación, como MSDN  
  
3.  Gestos  
  
    -   Invocación  
  
    -   Despido  
  
    -   Fijar  
  
    -   Otras interacciones  
  
4.  Modelo de persistencia y confirmación  
  
    -   Transitorio  
  
    -   Durable  
  
    -   Automático  
  
    -   A petición  
  
5.  Indicadores de ambientales (opcionales)  
  
    -   Subrayado de subrayado  
  
    -   Icono de etiqueta inteligente  
  
    -   Otros indicadores de ambientales  
  
#### <a name="container-content-presenter-type"></a>Tipo de contenedor (ranura de contenido)  
 Hay dos opciones principales presentar contenido en el momento de atención:  
  
1.  **En línea:** espacio para el nuevo contenido hace que un moderador en línea, como la vista de lectura que se introdujo en el Editor de código de Visual Studio 2013, desplazando el contenido existente.  
  
    -   **Prefiere** presenta los moderadores en línea si espera que los usuarios desearán dedicar una cantidad considerable de tiempo que hace referencia a o interactuar con el contenido.  
  
    -   **Evitar** alineado presentadores si espera que los usuarios desearán Eche un vistazo a la información presente y luego continúe con su tarea principal con una interrupción mínima.  
  
2.  **Flotante:** un presentador flotante se coloca lo más cerca del contenido seleccionado como sea posible, pero no modifica el diseño del contenido existente. Se pueden emplear varias estrategias, como mostrar un panel flotante contenido sobre el más cercano disponible espacio en blanco del símbolo seleccionado.  
  
    -   **Prefiere** flotante presentadores si espera que los usuarios desearán Eche un vistazo a la información presente y luego continúe con su tarea principal con una interrupción mínima.  
  
    -   **Evitar** flotante presentadores si espera que los usuarios desearán dedicar una cantidad considerable de tiempo que hace referencia a o interactuar con el contenido que está presente.  
  
#### <a name="content-type"></a>Tipo de contenido  
 Hay tres tipos principales de contenido que se pueden mostrar dentro de cualquier contenedor de la interfaz de Usuario en el objeto. Se puede mostrar cualquier combinación de estos tipos de información. Los tres tipos son:  
  
1.  **Informativo:** contenedores de la interfaz de Usuario mostrará algún tipo de contenido informativo a objeto de más. El contenido puede representar la información sobre el estado actual del entorno, o puede representar información sobre un estado futuro potencial del entorno. Por ejemplo, podría utilizarse para mostrar el efecto de un comando concreto, como una refactorización en el código existente.  
  
    -   **Siempre** usar la representación canónica de la información que mostrar. Por ejemplo, el código debe ser similar a código, junto con el resaltado de sintaxis y debe respetar la fuente y otras opciones de entorno que el usuario ha establecido.  
  
    -   **Siempre** considere la posibilidad de admitir las acciones sobre el contenido informativo que sería posible si esa información se presenta como contenido principal. Por ejemplo, si el código existente dentro de un contenedor de la interfaz de Usuario de objeto a presentar, considerar admitir la capacidad de examinar y modificar ese código.  
  
    -   **Siempre** considerar usar un color de fondo diferente si presentar contenido informativo que representa un estado futuro potencial.  
  
2.  Procesables: algunos contenedores de la interfaz de Usuario en el objeto proporcionará la capacidad de realizar alguna acción sobre el contenido principal, como realizar una operación de refactorización.  
  
    -   **Siempre** colocar comandos útiles por separado desde el contenido informativo.  
  
    -   **Siempre** Habilitar y deshabilitar acciones cuando corresponda.  
  
    -   **Siempre** consulte las directrices estándar para representar comandos dentro de los cuadros de diálogo.  
  
    -   **Siempre** mantener el número de acciones que se exponen en un contenedor de la interfaz de Usuario en el objeto en absoluto mínimo. Interactuar con la interfaz de Usuario de objeto debe ser una experiencia ligera y rápida. El usuario no es necesario dedicar energía acerca de cómo administrar el contenedor de objeto de interfaz de Usuario.  
  
    -   **Siempre** considerar cómo y cuándo se cierra o descartar un contenedor de la interfaz de Usuario en el objeto. Como práctica recomendada, cualquier acción que concluye el cuadro de diálogo entre el maestro y el contenido de detalle también debe cerrar el contenedor de la interfaz de Usuario en el objeto cuando se invoca la acción.  
  
3.  **Navegación:** algunos en objetos contenedores de interfaz de Usuario incluyen vínculos que llevará al usuario a otra ventana o aplicación, como abrir un artículo MSDN en el explorador web del usuario.  
  
    -   **Siempre** anteponer cualquier vínculo de navegación con "Abrir" para que los usuarios no sorprenderá algunos otros contenidos que se navega.  
  
    -   **Siempre** separar los vínculos de navegación de vínculos útiles.  
  
#### <a name="ambient-indicators-optional"></a>Indicadores de ambientales (opcionales)  
 Indicadores de ambientales pueden ser sutil, incluido el texto que se presentan en un color de contraste del resto del código, u obvio, incluidos los símbolos de tickler como subrayado subrayado e iconos de etiqueta inteligente. Indicadores de ambientales comunican la disponibilidad de información adicional relevante. Idealmente, proporcionan información útil incluso sin solicitar al usuario interactuar con ellos.  
  
-   **Siempre** colocar un indicador de ambiente de manera que no distraer o agobiar al usuario. Si no es posible colocar un indicador de ambiente de tal manera, considere la posibilidad de otra solución.  
  
-   **Siempre** colocar de lo más parecido posible al contenido que está relacionado con el indicador de ambiente.  
  
-   **Siempre** intenta crear un indicador que resume la información disponible. Considere la posibilidad de proporcionar un recuento del número de elementos de datos disponibles (por ejemplo, "3 referencias" en lugar de simplemente "Referencias") o pensar en alguna otra forma de resumir los datos.  
  
    -   En casos donde los datos de un indicador no siempre se calculan y se muestran, considere inmediatamente comentarios progresiva tal como se calculan los valores. Por ejemplo, considere la posibilidad de animar los cambios que reflejan las actualizaciones de los datos disponibles, similares a la forma en que se actualiza el icono dinámico de correo electrónico en Windows Phone como el número de mensajes no leídos aumenta.  
  
-   **Nunca** Agregar indicadores más de un usuario puede razonablemente una parte determinada del contenido. Indicadores de ambientales debe útiles sin necesidad de intervención del usuario. Indicadores de perderán su ambiente si necesitan un desbordamiento y otros controles de administración para importarlos a la vista.  
  
#### <a name="gestures"></a>Gestos  
 Un aspecto clave que permite al usuario mantener el foco en el contenido principal es compatible con los movimientos de la derecha para abrir y descartar el contenido de detalle adicionales.  
  
-   **Siempre** solicitar al usuario que realice algunas gesto explícito para abrir el contenido adicional. Movimientos abiertos comunes incluyen:  
  
    -   **Al mantener el mouse:** información sobre herramientas o contenido informativo no interactivo  
  
    -   **Comando explícito:** moderador en línea  
  
    -   **Haga doble clic en el indicador de ambiente:** ventana emergente de CodeLens  
  
-   **Siempre** Descartar el contenido de detalle cuando el usuario presiona la tecla Esc.  
  
-   **Siempre** tenga en cuenta el contexto de la interfaz de Usuario en el objeto. Moderadores de contenido que permiten la interacción dentro del contenedor, cuidadosamente considere si se debe mostrar información adicional al mantener el mouse, que suele ser perjudiciales para el flujo de trabajo del usuario.  
  
-   **Nunca** Mostrar contenido al mantener el mouse que parece ser editable o invita a la interacción del usuario. Este comportamiento puede frustrar a los usuarios al intentar mover el cursor sobre el contenido de detalle, como es el comportamiento estándar para una información sobre herramientas descartar inmediatamente cuando el cursor ya no está por encima del patrón contenido que lo generó.  
  
##  <a name="a-namebkmkselectionmodelsa-selection-models"></a><a name="BKMK_SelectionModels"></a> Modelos de selección  
  
### <a name="overview"></a>Información general  
 Un modelo de selección es el mecanismo utilizado para indicar y confirmar operaciones en uno o más objetos de interés dentro de la interfaz de usuario. Este tema describen los patrones de interacción de selección en los editores de documento de Visual Studio: editores de texto, superficies de diseño y modelado de superficies.  
  
 Los usuarios deben tener una forma de indicar a Visual Studio qué están trabajando, y Visual Studio debe responder de forma predecible con comentarios a los usuarios sobre lo que funciona en. Puede dar lugar a una falta de comunicación entre el usuario y la interfaz de usuario o de diferencias en el usuario no advertir una acción, que puede tener consecuencias no deseadas. A menudo, el error pasa desapercibido hasta que el usuario ve algo falta o ha cambiado. Los modelos de selección son, por tanto, una de las partes más importantes de diseño de la interfaz de usuario. Aunque los modelos de selección en Visual Studio son coherentes con Windows, hay pequeñas variaciones.  
  
 En Visual Studio, como en Windows, los modelos de selección difieren dependiendo del contexto en el que se produce la interacción. Las selecciones pueden producirse en cuatro tipos de objetos:  
  
-   Texto  
  
-   Objetos gráficos  
  
-   Listas y árboles  
  
-   Cuadrículas  
  
 En estos objetos, hay tres tipos de selecciones:  
  
-   Contiguos  
  
-   Discontinuas  
  
-   Región  
  
#### <a name="scope"></a>Ámbito  
 El componente más importante de selección es asegurarse de que el usuario sabe en qué ventana trabajan (activación) y dónde está el enfoque encuentra (selección). Visual Studio extiende la funcionalidad de administración de la ventana de Windows, pero el esquema de activación es el mismo: interactuar con una ventana trae el foco a la ventana. Visual Studio tiene dos indicadores para la activación: uno para las ventanas de documento y uno para ventanas de herramientas.  
  
 Para las ventanas de documento, la ventana activa se indica mediante una ficha de la ventana de documento que llegan a la parte delantera y cambiar su color de fondo:  
  
 ![Selección de pestaña activa en Visual Studio](../../extensibility/ux-guidelines/media/0713-01_activetab.png "0713-01_ActiveTab")  
  
 **Selección de pestaña activa**  
  
 Ventanas de herramientas, la ventana activa se indica mediante un cambio en el color del área de la barra de título de la ventana de herramientas:  
  
 ![Selección de ventana de herramientas activa en Visual Studio](../../extensibility/ux-guidelines/media/0713-02_activetoolwindow.png "0713-02_ActiveToolWindow")  
  
 **Mostrar selección primaria de un nodo de ventana de herramientas activa**  
  
 ![Selección de ventana de herramientas inactiva en Visual Studio](../../extensibility/ux-guidelines/media/0713-03_inactivetoolwindow.png "0713-03_InactiveToolWindow")  
  
 **Ventana de herramientas inactiva, mostrando latente selección de nodo**  
  
 Una vez que una ventana está activa, se indica su enfoque según los modelos de selección descritos en esta sección de las instrucciones.  
  
#### <a name="context"></a>Contexto  
 Visual Studio fue diseñado para conservar un concepto seguro de contexto, realizar el seguimiento de donde el usuario está trabajando. Sólo una ventana está activa, ya sea en una ventana de documento o de herramientas. Sin embargo, la ventana de documento de nivel superior siempre conserva una selección latente. Aunque el enfoque puede ser en una ventana de herramientas, la ventana de documento que estuvo activo muestra una selección, incluso en un estado inactivo. Esto se hace para conservar el contexto del usuario en el documento que estaba editando, muestra que Visual Studio ha conservado su estado de forma que puede volver y cambiar fácilmente entre ventanas de herramientas y ventanas de documento.  
  
### <a name="text-selection"></a>Selección de texto  
 Editores de Visual Studio que están estrictamente textuales, como el editor de texto integrada, utilizan el mismo modelo de selección de texto y apariencia se describe en el [del Mouse y punteros](https://msdn.microsoft.com/en-us/library/dn742466.aspx) página de Windows User Experience Interaction Guidelines en MSDN. El foco de entrada en el editor de texto se indica mediante una barra vertical que llama el punto de inserción. El punto de inserción es un solo píxel grueso y color como el inverso de todo lo que aparece detrás de él. Parpadea según la frecuencia establecida el **velocidad de intermitencia del Cursor** en el **velocidad** ficha de la **teclado** applet del Panel de Control.  
  
#### <a name="contiguous-and-disjoint-selection"></a>Selección contigua y no contiguo  
 Selección del Editor de texto sólo es contiguo. No se permiten las selecciones, pero deben incluirse en los editores de objeto gráfico de texto inconexos. Cuando el puntero del mouse está sobre un área de texto, el cursor cambia a un rayo. Un solo clic, coloca el punto de inserción en el editor de texto en la ubicación de clic. Manteniendo presionado el botón del mouse inicia un resalte de la selección y soltar el botón del mouse finaliza el resalte de la selección.  
  
#### <a name="region-selection-box-selection"></a>Selección de región (selección de cuadro)  
 Visual Studio admite las selecciones de la región en el editor de texto, y esto se conoce como selección del cuadro. Selección del cuadro permite al usuario seleccionar un área de texto que sigue la secuencia de texto normal. Al igual que con la selección de texto estándar, la selección debe ser contigua. Selección del cuadro inicia manteniendo presionada la tecla Alt mientras arrastra el mouse. También puede iniciarse cuadro selección manteniendo presionadas las teclas de desplazamiento y Alt mientras utiliza las teclas de flecha para indicar el área de selección. Selección de cuadro utiliza el resaltado de selección normal y muestra el cursor parpadea al final del área de selección del punto de inserción.  
  
 ![Configuración regional &#40; cuadro &#41; selección en Visual Studio](../../extensibility/ux-guidelines/media/0713-04_boxselection.png "0713-04_BoxSelection")  
  
 **Selección de región (cuadro) en Visual Studio**  
  
#### <a name="text-selection-appearance"></a>Apariencia de la selección de texto  
 Pueden personalizar los colores utilizados para la selección activa e inactiva en el editor. Para personalizar la apariencia visual del editor, un usuario puede ir a **Herramientas > opciones**, y después haga clic en **entorno > fuentes y colores > Editor de texto**.  
  
### <a name="graphical-selection"></a>Selección de gráfico  
  
#### <a name="interaction"></a>Interacción  
 Selección de objetos gráficos puede ser complicado y depende de una serie de factores:  
  
-   **El modelo del editor selección primaria.** Los editores que contienen objetos gráficos también se pueden usar para modificar texto o cuadrículas. Por ejemplo, el editor podría ser un editor de texto que también admite la colocación de objetos gráficos, como el Diseñador XAML de Visual Studio. Compatibilidad con varios tipos de objeto puede afectar a cómo el usuario selecciona grupos consta de distintos tipos de objetos.  
  
-   **Compatibilidad con los Estados de selección primaria y secundaria.** Un editor puede proporcionar la selección primaria y secundaria Estados para que los objetos se pueden editar unísono, alineados entre sí, cambiar el tamaño, y así sucesivamente.  
  
-   **Compatibilidad de edición en contexto.** Editores también pueden permitir que el contenido de sus objetos gráficos que desea editar. Por ejemplo, una forma de rectángulo también podría contener texto en el interior que el usuario puede cambiar. Además, ese texto se podría centrado o justificado. Edición en contexto implica un nivel más detallado de la interacción del usuario y, por tanto, requiere un conjunto adecuado de indicaciones visuales para presentar información de estado al usuario.  
  
#### <a name="mouse-interaction"></a>Interacción con el mouse  
  
|Entrada|Resultado|  
|-----------|------------|  
|Haga clic en un objeto no seleccionado|Selecciona el objeto y muestra una línea discontinua y controladores de selección, si el objeto es de tamaño variable.|  
|Haga clic en un objeto seleccionado|Activa la edición en contexto, si lo admite el objeto. Haga clic fuera del objeto, desactiva el modo de edición en contexto.|  
|Haga doble clic en un objeto|Se abre el código detrás del objeto para su edición y podría insertar un controlador de eventos predeterminado, si procede.|  
|Seleccione un objeto|Cambia el puntero hasta el cursor de movimiento. Puede cambiar la apariencia del objeto, como su luminosidad o color.|  
|Seleccione un controlador de selección|Cambia el puntero hasta el cursor de cambio de tamaño. Para los objetos que admiten la rotación, algunos controladores de selección pueden cambiar el puntero a un cursor Girar como el puntero diferente (por ejemplo, si se mueve más lejos) en relación con el controlador de selección.|  
|Arrastrar|Incluso si el objeto no se ha seleccionado anteriormente, cambia el puntero hasta el cursor de movimiento y mueve el objeto.|  
|Editor pierde el foco|Desactiva el modo de edición en contexto, aunque el objeto mantiene el contenido y el aspecto que tenía durante su último estado de operación o selección.|  
|Selección de objetos|Indicado por un borde, línea de puntos u otro tratamiento visualmente distinto para resaltar el límite del objeto.|  
|Cambiar el tamaño de un objeto seleccionado|Indicado por controladores de selección.<br /><br /> Un objeto redimensionable tiene ocho controladores, que representa cada dirección en la que puede cambiarse. Si el objeto sólo puede cambiarse en determinadas direcciones, pueden utilizarse menos identificadores. Cuando el usuario cambia el tamaño de un objeto hasta donde ocho controladores no sería interactivos, pueden usar cuatro identificadores. Tamaños de identificador deben asociarse a las métricas de borde y el borde de ventana con el **GetSystemMetrics** función de la API de tamaño proporcional a la resolución de pantalla.<br /><br /> ![Controladores de tamaño](../../extensibility/ux-guidelines/media/0713-05_resizehandles.png "0713-05_ResizeHandles")|  
|Girar un objeto seleccionado|![Controladores de giro](../../extensibility/ux-guidelines/media/0713-06_rotate.png "0713-06_Rotate")|  
  
#### <a name="keyboard-interaction"></a>Interacción con el teclado  
  
|Entrada|Resultado|  
|-----------|------------|  
|Pestaña|Mueve el indicador de foco entre el orden lógico de objetos en el editor. Esto puede ser de izquierda a derecha o de arriba a abajo según **TabIndex** (o equivalente) valor de propiedad, orden de creación de objetos y el propósito general del editor. Mayús + Tab se invierte la dirección del indicador de foco.|  
|Barra espaciadora|Activa el modo de panorámica mientras se mantiene la pulsación de tecla. Entrada de mouse adicional es necesario para desplazar la posición de la ventanilla.|  
|Ctrl+Barra espaciadora|Activa el modo de zoom mientras se mantiene la pulsación de tecla. Entrada de mouse adicional se requiere para aumentar y disminuir el factor de zoom.|  
|Ctrl + Alt + signo menos|Disminuye el factor de zoom en un nivel.|  
|Ctrl + Alt + signo más|Aumenta el factor de zoom en un nivel.|  
|MAYÚS o Ctrl|Agrega el objeto al grupo de selección. CTRL también le permite quitar los objetos individualmente desde el grupo de selección.|  
|Entrar|Realiza el comando predeterminado para el objeto (normalmente abrir o editar).|  
|F2|Activa la edición en contexto para el objeto.|  
|Teclas de dirección|Mueve los objetos seleccionados en la dirección de la tecla presionada, en incrementos pequeños (por ejemplo, de 1 píxel en un momento)|  
|CTRL + teclas de dirección|Mueve los objetos seleccionados en la dirección de la tecla presionada, en incrementos mayores (por ejemplo, 10 píxeles cada vez)|  
|Mayús + flecha claves|Cambia el tamaño de los objetos seleccionados en la dirección correspondiente, en incrementos pequeños (por ejemplo, de 1 píxel en un momento)|  
|Ctrl + Mayús + teclas de dirección|Cambia el tamaño de los objetos seleccionados en la dirección correspondiente, en incrementos mayores (por ejemplo, 10 píxeles cada vez)|  
  
 Cuando los usuarios modificar controles en su lugar, tendría sentido para los objetos a automáticamente el tamaño de la entrada del usuario. Por ejemplo, si el usuario edita un control de etiqueta, la etiqueta debe crecer para mostrar el texto que escribió el usuario. Si no es así, el usuario debe cambiar manualmente el control después de editar el texto. Si el usuario tiene una gran cantidad de controles, se convierte en una tarea improductivo y básicas.  
  
#### <a name="graphical-containers"></a>Contenedores de gráficos  
 En algunos casos, editores gráficos proporcionan contenedores para otros objetos gráficos, como el control de Panel de Windows Forms o el diseño de cuadrícula en el Diseñador HTML. Si el editor proporciona contenedores para otros objetos gráficos, se debe usar el siguiente modelo de selección para el contenedor solo (objetos en el seguimiento de contenedor del modelo estándar como se describe anteriormente):  
  
|Entrada|Resultado|  
|-----------|------------|  
|Hacer clic en el contenedor|Selecciona el objeto contenedor sin directamente si se selecciona cualquiera de los objetos contenidos. El contenedor se puede mover o cambiar de tamaño con estándar mouse y teclado (como se describió anteriormente). Objetos contenidos se mueven en relación al contenedor, pero los objetos contenidos no cambian de tamaño a menos que se seleccionan directamente.|  
|Mantenga el mouse sobre el área de límite del contenedor|El mouse se convierte en el cursor de movimiento, que indica que el contenedor se puede mover.|  
|Arrastre el control región del límite del contenedor|Cambia el mouse al cursor de movimiento y mueve el contenedor (y los objetos contenidos dentro de). El contenedor no se pueden mover sin primero seleccionado con un solo clic.|  
|Hacer clic en un objeto dentro del contenedor|Anula el contenedor (si está seleccionada) y selecciona sólo el objeto ha hecho clic.|  
|Mayús + clic o Ctrl + clic en un objeto contenido o el contenedor|Agrega el objeto ha hecho clic en un grupo de selección o selección existente. Si el objeto que se ha hecho clic ya es miembro del grupo de selección, se quita del grupo de selección.|  
  
 Los objetos contenidos deben respetar el modelo de selección básica como se describe en la sección anterior. Pruebas de facilidad de uso del Diseñador de Windows Forms, espera que los usuarios acceso ininterrumpido a los objetos contenidos sin intervención de pasos (impuestas por el objeto de contención).  
  
#### <a name="disjoint-and-region-selections"></a>Discontinuas y las selecciones de región  
 Editores de objeto gráfico deben admitir selecciones discontinuas. Tenga en cuenta que este gráfico no muestra la apariencia del control para Visual Studio. Consulte [apariencia de selección de objeto gráfico](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_GraphicalObjectSelectionAppearance) para obtener especificaciones detalladas visuales.  
  
 ![Selectores de región y discontinuos](../../extensibility/ux-guidelines/media/0713-07_disjointregionselectors.png "0713-07_DisjointRegionSelectors")  
  
 **Selección discontinua**  
  
 Editores gráficos también deben proporcionar las selecciones de la región con un indicador de selección de tipo de marquesina. Si el editor de gráficos admite otros tipos de objeto (como texto), a continuación, selecciones de región podrían no ser posibles dependiendo de las restricciones de esos otros tipos de objeto.  
  
 ![Selección de recuadro](../../extensibility/ux-guidelines/media/0713-08_marqueeselection.png "0713-08_MarqueeSelection")  
  
 **Selección de recuadro**  
  
#### <a name="primary-and-secondary-selections"></a>Selecciones principal y secundaria  
 Algunos editores de objeto gráfico permiten al usuario editar o alinear objetos en grupos. En este caso, debe introducirse el concepto de selecciones principal y secundaria. La selección principal es el objeto al que todos los demás objetos responden para operaciones de grupo. El objeto que el usuario selecciona primero se convierte en el control principal y selecciones posteriores se convierten en las selecciones secundarias. La selección primaria tiene un tratamiento distinto visual de las selecciones para indicar el objeto que es el principal secundarios:  
  
 ![Selección primaria y secundaria](../../extensibility/ux-guidelines/media/0713-09_primarysecondary.png "0713-09_PrimarySecondary")  
  
 **Selección primaria con dos selecciones secundarias**  
  
####  <a name="a-namebkmkgraphicalobjectselectionappearancea-graphical-object-selection-appearance"></a><a name="BKMK_GraphicalObjectSelectionAppearance"></a> Apariencia de la selección de objeto gráfico  
 Los controladores de selección son cuadrados dibujados en un patrón rectangular alrededor del cuadro de límite del objeto. El gráfico siguiente muestra ejemplos de los diferentes Estados que puede tener un objeto gráfico con el identificador, el tamaño y la apariencia de edición en contexto. El tamaño de los identificadores debe asociarse a borde de ventana y borde métricas usando la **GetSystemMetrics** API.  
  
|Estado|Apariencia|Detalles visuales|  
|-----------|----------------|--------------------|  
|**No seleccionado**|Default|![Estado de botón predeterminado](../../extensibility/ux-guidelines/media/0713-10_defaultstate.png "0713-10_DefaultState")||  
|**Selección primaria**|Resizable|![Selección primaria con controladores de tamaño](../../extensibility/ux-guidelines/media/0713-11_primaryresize.png "0713-11_PrimaryResize")|![Selección primaria con cambiar el tamaño de los identificadores de &#40; ampliada &#41;](../../extensibility/ux-guidelines/media/0713-12_primaryresizezoom.png "0713-12_PrimaryResizeZoom")|  
|**Selección primaria**|No puede cambiar el tamaño|![Selección primaria sin controladores de tamaño](../../extensibility/ux-guidelines/media/0713-13_primarynoresize.png "0713-13_PrimaryNoResize")|![Selección primaria sin cambiar el tamaño de los identificadores de &#40; ampliada &#41;](../../extensibility/ux-guidelines/media/0713-14_primarynoresizezoom.png "0713-14_PrimaryNoResizeZoom")|  
|**Selección primaria**|Bloqueado|![Selección primaria bloqueada](../../extensibility/ux-guidelines/media/0713-15_primarylocked.png "0713-15_PrimaryLocked")|![Selección primaria bloqueada &#40; ampliada &#41;](../../extensibility/ux-guidelines/media/0713-16_primarylockedzoom.png "0713-16_PrimaryLockedZoom")|  
|**Selección secundaria**|Resizable|![Selección primaria con controladores de tamaño](../../extensibility/ux-guidelines/media/0713-17_secondaryresize.png "0713-17_SecondaryResize")|![Selección secundaria con cambiar el tamaño de los identificadores de &#40; ampliada &#41;](../../extensibility/ux-guidelines/media/0713-18_secondaryresizezoom.png "0713-18_SecondaryResizeZoom")|  
|**Selección secundaria**|No puede cambiar el tamaño|![Selección secundaria sin controladores de tamaño](../../extensibility/ux-guidelines/media/0713-19_secondarynoresize.png "0713-19_SecondaryNoResize")|![Selección secundaria sin tamaño &#40; ampliada &#41;](../../extensibility/ux-guidelines/media/0713-20_secondarynoresizezoom.png "0713-20_SecondaryNoResizeZoom")|  
|**Selección secundaria**|Bloqueado|![Selección secundaria bloqueada](../../extensibility/ux-guidelines/media/0713-21_secondarylocked.png "0713-21_SecondaryLocked")|![Selección secundaria bloqueada &#40; ampliada &#41;](../../extensibility/ux-guidelines/media/0713-22_secondarylockedzoom.png "0713-22_SecondaryLockedZoom")|  
|**Interfaz de Usuario activo**|Default|![Estado activo de interfaz de usuario](../../extensibility/ux-guidelines/media/0713-23_uiactive.png "0713-23_UIActive")|![Interfaz de Usuario de estado activo &#40; ampliada &#41;](../../extensibility/ux-guidelines/media/0713-24_uiactivezoom.png "0713-24_UIActiveZoom")|  
  
### <a name="view-selection-models"></a>Modelos de selección de vista  
  
#### <a name="tree-view"></a>Vista de árbol  
 Se muestra la selección en una vista de árbol con un simple resaltado. Si el usuario hace clic en un nombre de nodo o un icono de nodo, el nodo deja de estar seleccionado. Los glifos triangulares a la izquierda del nodo expandir o contraer el control de árbol pero no afectan a la selección del usuario, con una excepción: al contraer un nodo primario cuando la selección está en un elemento secundario de ese nodo, la selección se desplaza al elemento primario.  
  
 ![Vista de árbol típica de Visual Studio](../../extensibility/ux-guidelines/media/0713-25_treeview.png "0713-25_TreeView")  
  
 **Vista de árbol típica de Visual Studio**  
  
 Vistas de árbol pueden admitir selecciones contiguas y no contiguas, incluso a través de varios niveles del árbol. Contiguos o no contiguos varias selecciones deben realizarse en los nodos de árbol visible. Si un nodo está contraído, se pierde la selección separada y el nodo que se contrajo Obtiene la selección. De esta manera, el usuario puede ver los nodos que se verán afectados por una operación. Cuando se contraen los nodos, sea poco claro qué nodos podrían verse afectadas.  
  
 Cuando se selecciona un nodo primario, debe aplicar la operación en el elemento primario, aunque puede haber casos donde tenga sentido para una operación aplicar al elemento primario y todos sus elementos secundarios. En este caso, proporcionan la interfaz de Usuario adicional durante la operación, como una casilla de verificación o cuadro de diálogo de confirmación para que la opción "aplicar a todos los elementos secundarios" explícita para el usuario.  
  
##### <a name="renaming"></a>El cambio de nombre  
 Si los nodos del árbol permite cambiar el nombre, el cambio de nombre debe realizarse en su lugar. La operación en el contexto debe ser el estándar en todos los controles de árbol en Visual Studio. Proporciona un comando de cambio de nombre que se activa inmediatamente el modo de edición en contexto, con la selección de texto que abarcan todo el nombre del nodo, preparado para aceptar la entrada del usuario. Si el nodo representa un archivo, el nombre de archivo debe contener la extensión. Resaltado de la selección debe incluir sólo el cuerpo del nombre de archivo y no la extensión.  
  
|Entrada|Resultado|  
|-----------|------------|  
|Entrar (tecla)|Confirma la operación de cambio de nombre|  
|Tecla ESC|Cancela la operación de cambio de nombre|  
|Haga clic fuera de la región de edición|Confirma la operación de cambio de nombre|  
|Deshacer|Proporcionar fácil deshacer para cancelar la operación de cambio de nombre|  
  
#### <a name="selection-within-lists-and-grid-controls"></a>Selección de listas y controles de cuadrícula  
 El concepto clave en la selección de la lista es la que está basado en la fila, lo que significa que cuando se realiza una selección toda la fila está seleccionada como una unidad. Por el contrario, las cuadrículas pueden permitir que determinadas celdas que se seleccionen sin afectar a cualquier otro aspecto de la fila. Cuadrículas también podrían contener una jerarquía de filas anidadas (como en un control TreeGrid) que permiten todas ramas de la jerarquía se seleccionen y se anula la selección al interactuar con las filas primarias. Selección de listas se muestra mediante un color de resaltado simple en toda la fila de datos. El foco se muestra un borde de puntos de píxel alrededor de la fila actual de editable o celda (fila si todas las celdas son de sólo lectura).  
  
> [!NOTE]
>  **Enfoque** y **selección** son conceptos diferentes. *Enfoque* es una indicación de la interfaz de Usuario del elemento que se destina para recibir entrada dirigido no explícitamente a otro objeto, mientras que *selección* se refiere al estado de inclusión de un objeto en un conjunto de objetos en el que podrán realizarse operaciones posteriores.  
  
 Las selecciones en las listas pueden ser contiguas, separado, o la región. Cuando selecciones múltiples están permitidos, contiguo y siempre debe ser compatible selección separado aunque la compatibilidad para las selecciones de región (cuadro) son opcional. Las selecciones de la región se inician arrastrando en el espacio en blanco del cuerpo de la lista.  
  
|Objeto|Selección|  
|------------|---------------|  
|Lista|Contiguos|Siempre se admite (cuando se permiten varias selecciones).|  
|Lista|Discontinuas|Siempre se admite (cuando se permiten varias selecciones).|  
|Lista|Región|Compatibilidad opcional. Iniciar arrastrando el mouse en el espacio en blanco del cuerpo de la lista.|  
  
 Al hacer clic una vez en una lista, selecciona la fila donde se hizo clic. Si el usuario haga clic en una celda de la lista que admite la edición en contexto, la celda se activa inmediatamente para su edición en contexto. En caso contrario, toda la fila se selecciona inmediatamente y muestra resaltado.  
  
 Arrastrar en el cuerpo de la lista, realiza una de estas tres cosas:  
  
-   Inicia una selección de región, si lo admite la lista y el mouse hacia abajo en el espacio en blanco  
  
-   Inicia una operación de arrastrar y colocar, si la fila o celda de la lista admite que se va a un origen de arrastre  
  
-   Selecciona la fila actual  
  
##### <a name="in-place-editing"></a>Edición en contexto  
 Cuando se permite la edición en contexto, existen dos modelos básicos: selector de control y la propiedad de edición sencilla. Con un control de edición sencilla, el contenido está resaltada y listo para la entrada en cuanto se activa la edición en contexto del usuario. Cuando se implementa un selector de propiedades, se muestra el botón que invoca el selector de propiedad una vez que se activa el modo de edición en contexto y la selección actual no está resaltada. El botón de selector debe estar justificado a la derecha de la celda. Para obtener ejemplos de edición en contexto, vea la **ventana propiedades** y **lista de tareas** en Visual Studio.  
  
##### <a name="keyboard-support"></a>Compatibilidad con el teclado  
 Compatibilidad con el teclado para la selección de listas y cuadrículas sigue las convenciones estándar de Windows:  
  
-   Teclas de dirección desplazarse por la lista, seleccione cada celda de fila cuando se mueve el foco.  
  
-   Mayús + flecha realiza una selección contigua en el sentido de las teclas de dirección.  
  
-   Ctrl + flecha seguido de barra espaciadora alterna entre agregar y quitar elementos de la lista de la selección, la creación de una selección no contiguo.  
  
-   En las cuadrículas que contienen jerarquías anidadas, la tecla flecha derecha expande una fila primaria y la tecla flecha izquierda contrae uno.  
  
-   La tecla Tab mueve el foco entre las celdas de la fila actual si se pueden modificables las celdas.  
  
-   La tecla ENTRAR ejecuta el comando de forma predeterminada en el elemento de la lista (a menudo **abiertos**).  
  
-   La tecla F2 activa la edición en contexto para la celda seleccionada actualmente.  
  
##  <a name="a-namebkmkpersistenceandsavingsettingsa-persistence-and-saving-settings"></a><a name="BKMK_PersistenceAndSavingSettings"></a> Persistencia y guardar la configuración  
  
### <a name="overview"></a>Información general  
 Aunque cada componente de software en Visual Studio es suele ser responsable de su propio estado y persistencia, Visual Studio guarda la configuración en algunos casos, como con posiciones y tamaños de ventana. La tabla siguiente es una combinación de opciones guardadas automáticamente y que requieren un usuario explícito o programar la acción a emprender.  
  
|Objeto|Lo que debe guardar|Cuándo se debe guardar|Dónde guardar|  
|------------|------------------|------------------|-------------------|  
|Objetos seleccionables (por ejemplo, una línea de código)|Un punto de interrupción en una línea de código<br /><br /> Un acceso directo de usuario asociado a la línea de código|Cuando se guarda el proyecto|El **Opciones de usuario (.suo)** archivo de proyecto|  
|Cuadro de diálogo|La ubicación del cuadro de diálogo, si se han movido<br /><br /> La vista que el usuario utilizó por última vez en el cuadro de diálogo|Cuando se cierra el cuadro de diálogo<br /><br /> Cuando finaliza la sesión de Visual Studio|En la memoria<br /><br /> Registro en **HKEY_Current_User**|  
|Ventana|El tamaño y la ubicación de la ventana|Cuando se cierra la ventana<br /><br /> Cuando se cambia el modo de Visual Studio<br /><br /> Cuando finaliza la sesión de Visual Studio|El **Opciones de usuario (.suo)** archivo de proyecto<br /><br /> Archivo de opciones personalizadas para la configuración de la ventana|  
|Documento|La selección actual en el documento<br /><br /> La vista del documento<br /><br /> El último varios lugares visitado el usuario|Cuando se guarda el documento|El **Opciones de usuario (.suo)** archivo de proyecto|  
|Proyecto|Referencias a archivos<br /><br /> Referencias a los directorios en disco<br /><br /> Referencias a otro software<br /><br /> Componentes<br /><br /> Información de estado sobre el propio proyecto|Cuando se guarda el proyecto|El archivo de proyecto|  
|Solución|Referencias a proyectos<br /><br /> Referencias a archivos|Cuando se guarda el proyecto o solución|El **solución (.sln)** archivo|  
|Configuración de **Herramientas > Opciones**|Personalizaciones del teclado<br /><br /> Personalizaciones de la barra de herramientas<br /><br /> Combinaciones de colores|Cuando el **Herramientas > opciones** cierra el cuadro de diálogo<br /><br /> Cuando finaliza la sesión de Visual Studio|Registro en **HKEY_Current_User**|  
  
 ¿Qué está haciendo el usuario y cuando hacen, determina si se guarda una configuración en memoria (durante la sesión), que se guarda en disco (entre sesiones como una configuración del registro), como parte del proyecto o solución de archivo, como parte de la **Opciones de solución (.suo)** de archivos o como una configuración personalizada de archivos que sólo ese componente de software se conoce. La tabla anterior muestra varios eventos en el que se puede guardar la configuración. Sin embargo, existen otras ocasiones en que desee guardar el estado:  
  
-   Cuando el usuario cambia la ubicación dentro de un cuadro de diálogo o ventana  
  
-   Cuando el usuario transfiere el foco a otra ventana  
  
-   Cuando el usuario cambia de diseño en modo de depuración  
  
-   Cuando el usuario cierra su cuenta  
  
-   Cuando el equipo entra en modo de hibernación o se cierra  
  
-   Cuando la unidad de disco duro equipo está a punto de ser vuelve a dar formato y vuelva a configurar  
  
### <a name="window-configurations"></a>Configuraciones de ventanas  
 Una configuración de ventana es la presentación básica del entorno de desarrollo, es un esquema que constan de la lista de ventanas de herramientas está presentes y el modo en que se organizan. Para windows administrada por el IDE (windows IDE), información de diseño se conserva por usuario, por lo que cuando un usuario inicie el IDE, el diseño de ventana aparece igual al último salido de Visual Studio. Se conserva el estado y la posición de las ventanas IDE en un archivo de opciones personalizadas en formato XML. Ventanas de herramientas que se crean paquetes cargados en el IDE conservan su información de estado en el registro y pueden o no pueden por usuario.  
  
#### <a name="profile-specific-layouts"></a>Diseños de perfil específicos  
 Cada perfil incluye diseños de ventana de herramienta, organizados de una manera familiar para los roles de desarrollador específica (los desarrolladores de Visual C++ esperan ver el **el Explorador de soluciones** en el lado izquierdo del IDE, mientras que los desarrolladores de C# esperan ver el **el Explorador de soluciones** a la derecha). Diseños de ventana específica del perfil se cargan después de que el usuario elige un perfil en el inicio. El autor de un paquete debe determinar el diseño de ventana más adecuado para la experiencia de sus clientes, sabiendo que, a continuación, se conservarán los cambios que realiza el usuario a la configuración de la ventana.  
  
##  <a name="a-namebkmktouchinputa-touch-input"></a><a name="BKMK_TouchInput"></a> Entrada táctil  
 Los usuarios utilizan cada vez más productos de desarrollo de Microsoft en los dispositivos táctiles. Sin embargo, existen obstáculos que dificultan la utilice herramientas de desarrollo de dispositivos táctiles. Los usuarios esperarán los productos para proporcionar una experiencia táctil precisas y confiables. El propósito de estas directrices es informar a las decisiones acerca de qué funciones táctiles para incorporar y fomentar una experiencia táctil coherente entre Visual Studio y productos relacionados.  
  
### <a name="levels-of-experience"></a>Niveles de experiencia  
 Los siguientes niveles de experiencia están diseñados para servir como guía para ayudar a los equipos decidir qué funciones táctiles para ofrecer según su nivel deseado de interés de la inversión en contacto.  
  
-   El **experiencia básica** es para los equipos que desee proporcionar interacción capacidades, por lo que no hay ningún callejones a lo largo de su trabajo.  
  
-   El **optimizado experiencia** es para equipos que desee proporcionar al máximo las capacidades táctiles (por ejemplo, los normalmente disponibles en las aplicaciones de explorador de internet).  
  
-   El **elevados experiencia** es para equipos que desean agregar capacidades tales como gestos u otras capacidades opcionales que pueden hacer que su aplicación táctiles descriptivo.  
  
||Experiencia básica|Experiencia optimizada|Experiencia con privilegios elevados|  
|-|----------------------|--------------------------|-------------------------|  
|Permite a los usuarios...|Corrija el código y solución/proyecto leer sin callejones|Realizar tareas de mantenimiento, refactorizaciones y navegación|Trabajar en una experiencia coherente, intuitivo y fluida con confianza|  
|Editor|Selección y táctil panorámica<br /><br /> Barra de desplazamiento táctil para saltar y presione + arrastrar|Acercar alejar<br /><br /> Desplazamiento rápido<br /><br /> Selección<br /><br /> Fácil usar del menú contextual||  
|Ventanas de herramientas superior|Lista panorámica<br /><br /> Selección de elementos<br /><br /> Barra de desplazamiento táctil para saltar y presione + arrastrar|Elemento fácil desplazamiento y selección||  
|Ventana||Cambiar el tamaño de ventana<br /><br /> Acceso rápido||  
|Documento bien||Facilitar el desplazamiento entre archivos abiertos||  
|Gestos||Asegúrese de gestos comunes funcionan en el IDE|Acciones de gestos<br /><br /> Compatibilidad con arrastrar y colocar y diseñadores|  
|Otras consideraciones|||Teclado en pantalla personalizado|  
  
#### <a name="gestures"></a>Gestos  
 Gestos de proporcionan a los usuarios un acceso directo a los comandos que de lo contrario, podrían requerir una interacción más complicada. Consulte las instrucciones de Windows en [gestos táctiles para aplicaciones de escritorio](http://msdn.microsoft.com/en-us/library/windows/desktop/dd940543\(v=vs.85\).aspx), y siga estas instrucciones para la mayoría de los gestos, incluidos los movimientos simples como panorámica y zoom.