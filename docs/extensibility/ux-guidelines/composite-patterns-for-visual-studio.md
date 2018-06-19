---
title: Patrones compuestos para Visual Studio | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: e48ecfb2-f4b5-4d3a-b4a2-7a4d62fa4ec0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6515b5aefc0536ea92f09a92b1a17050b820008d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31148956"
---
# <a name="composite-patterns-for-visual-studio"></a>Patrones compuestos para Visual Studio
Patrones compuestos combinan elementos de interacción y diseño de configuraciones. Algunos de los patrones compuestos más importantes en Visual Studio con respecto a la coherencia incluyen:  
  
-   [Visualización de datos](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_DataVisualization)  
  
-   [Interfaz de usuario en el objeto y el examen](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)  
  
-   [Modelos de selección](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)  
  
-   [Persistencia y guardar la configuración](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)  
  
-   [Entrada táctil](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)  
  
##  <a name="BKMK_DataVisualization"></a> Visualización de datos  
  
### <a name="overview"></a>Información general  
 Los gráficos son una forma visual para agregar y visualizar datos con el fin de mejorar la toma de decisiones. Pueden ayudar a los usuarios que se enfrentan con una gran cantidad de datos, pero lo que significa poco vea lo que merecen atención y lo que podría necesitar una acción.  
  
 El usuario puede beneficiarse de un gráfico si se cumple alguna de las condiciones siguientes:  
  
-   ¿El gráfico ayudarán a los usuarios identificar las tareas que pueden actuar en?  
  
-   ¿Permitirá el gráfico a los usuarios prever las consecuencias de posibles cambios?  
  
-   ¿El gráfico para los usuarios detectar tendencias e identificar patrones?  
  
-   ¿Permitirá el gráfico a los usuarios a tomar mejores decisiones?  
  
-   ¿El gráfico ayudará a responder a una pregunta específica que los usuarios podrían tener en el contexto determinado?  
  
#### <a name="general-rules-for-charts"></a>Reglas generales para gráficos  
  
-   Claramente los datos de etiqueta. Ilustraciones sin explicación son simplemente queda imágenes.  
  
-   Iniciar ejes en cero para evitar sesgar proporciones. Tamaño de longitud y barra de línea son importantes indicaciones visuales para entender las relaciones entre los puntos de datos.  
  
-   Crear gráficos, no infografías. Infografías son artísticos representaciones de datos, y su objetivo principal es storytelling visual. Los gráficos pueden (y deben) ser visualmente atractivo, pero permiten que los datos hablen por sí mismos.  
  
-   Evite skeumorphism, gráficos de barras gráficos, contraste hashmarks y otros infografía los últimos retoques.  
  
-   No utilice efectos 3D como un elemento decorativo. Utilizar estas opciones solo si se realmente parte integral de la capacidad del usuario para comprender la información.  
  
-   Evite el uso de varias líneas y rellenos, tal y como más de dos colores pueden hacer que este tipo de gráfico que resulte difícil leer e interpretar correctamente.  
  
-   No use un gráfico (o cualquier ilustración) como el único medio de descripción de un concepto o interactuar con los datos. Esto presenta dificultades para los usuarios con discapacidades visuales.  
  
-   No use gráficos como innecesarias o decorativos elementos en una página. En otras palabras, si un gráfico no agrega que ningún valor o ayuda usuarios resolución un problema, no usarlo.  
  
### <a name="chart-types"></a>Tipos de gráficos  
 Tipos de gráficos que se usa en Visual Studio incluyen gráficos de barras, gráficos de líneas, un gráfico circular modificado que se conoce como un gráfico de anillos o "gráfico de anillos," escalas de tiempo, dispersión trazados (también denominadas "gráficos del clúster") y los diagramas de Gantt. Cada tipo de gráfico es útil para la comunicación de un tipo diferente de información.  
  
### <a name="other-charting-considerations"></a>Otras consideraciones de creación de gráficos  
  
#### <a name="color"></a>Color  
 Hay una paleta específica de los gráficos de colores definidos para su uso en Visual Studio. La paleta es accesible para los tipos principales de ciegos de color y los colores se pueden diferenciar incluso cuando se utiliza como sectores muy limitados de color. Puede usar estos colores en cualquier combinación de cualquier tipo de gráfico en la interfaz de usuario. No es necesario utilizar todos los colores de siete si no es necesario que muchos colores distintos. Estos colores no se diseñaron para su uso con los elementos de primer plano, por lo que no se debe colocar el texto o glifos encima de estos colores. Estos matices deben codificado de forma rígida y expone a la personalización del usuario en **Herramientas > opciones** (consulte [exponer colores para los usuarios finales](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)).  
  
|Muestra|Hex|RGB|  
|------------|---------|---------|  
|![Muestrario 71B252](../../extensibility/ux-guidelines/media/0711_71b252.png "0711_71B252")|#71B252|113,178,82|  
|![Muestrario BF3F00](../../extensibility/ux-guidelines/media/0711_bf3f00.png "0711_BF3F00")|#BF3F00|191,63,0|  
|![Muestrario FCB714](../../extensibility/ux-guidelines/media/0711_fcb714.png "0711_FCB714")|#FCB714|252,183,20|  
|![Muestrario 903F8B](../../extensibility/ux-guidelines/media/0711_903f8b.png "0711_903F8B")|#903F8B|144,63,139|  
|![Muestrario 117AD1](../../extensibility/ux-guidelines/media/0711_117ad1.png "0711_117AD1")|#117AD1|17,122,209|  
|![Muestrario 79D7F2](../../extensibility/ux-guidelines/media/0711_79d7f2.png "0711_79D7F2")|#79D7F2|121,215,242|  
|![Muestrario B5B5B5](../../extensibility/ux-guidelines/media/0711_b5b5b5.png "0711_B5B5B5")|#B5B5B5|181,181,181|  
  
##  <a name="BKMK_OnObjectUI"></a> Interfaz de usuario en el objeto y el examen  
 Esta sección proporciona el contexto para leerlo, también conocido como vista de peek de código, un tipo de interfaz de usuario de objeto único a Visual Studio.  
  
### <a name="overview"></a>Información general  
  
-   Interfaz de usuario en objeto debe dar al usuario más información o interactividad sin apartarse de su tarea principal.  
  
-   El patrón principal de interfaz de usuario del objeto en Visual Studio se conoce como "información en el momento de atención".  
  
-   Interfaz de usuario en el objeto en Visual Studio es ya sea en línea o flotante y perdurables o transitoria.  
  
    -   Vista de peek de código, un tipo de interfaz de usuario del objeto en Visual Studio, es duradera y en línea.  
  
    -   CodeLens, un tipo de interfaz de usuario del objeto en Visual Studio, es transitorio y flotante  
  
 Entender cómo funciona un fragmento de código, o buscar detalles sobre ese código, a menudo requiere un programador cambiar el contexto y vaya a otro tipo de contenido o en otra ventana. Estos desplazamientos de contexto pueden ser perjudiciales, porque los usuarios pueden perder el foco en su tarea original si deja en su ventana principal. Además, la obtención de que copia original de contexto puede ser difícil, especialmente si el cambio entre ventanas provocó el código original para verse oscurecidas por otra interfaz de usuario.  
  
 Interfaz de usuario en el objeto sigue un patrón denominado "información en el momento de atención". Estos mensajes, ventanas emergentes y cuadros de diálogo proporcionan a los usuarios información adicional relevante que agrega alguna aclaración o interactividad sin perder el foco en su tarea principal. Algunos ejemplos de interfaz de usuario de objeto son ventanas emergentes que aparecen cuando un usuario desplace el puntero sobre un icono en el área de notificación, la línea ondulada roja debajo de una palabra mal escrita, la vista de peek introdujo en Visual Studio 2013.  
  
### <a name="decision-points"></a>Puntos de decisión  
 En Visual Studio, hay varias formas de usar este patrón de información en el momento de atención. Elegir el mecanismo adecuado e implementar de forma coherente y predecible son esencial para la experiencia global. En caso contrario, los usuarios pueden presentarse una experiencia incoherente o confusa que implica menoscabo alguno foco desde el propio contenido.  
  
#### <a name="relationships-between-master-and-detail-content"></a>Relaciones entre maestro y detalles de contenido  
 Información en el momento de atención se usa para mostrar una relación entre el contenido que el usuario está centrado en (el contenido de "master") y adicionales relacionados con contenido (el contenido de "Detalles"). En este modelo, el contenido de detalle está claramente relacionado con el contenido que el usuario está trabajando con y se puede mostrar cerca el contenido principal. Información adicional o información que no se pueden resumir sin abrumar el contenido principal debe seguir otro patrón, como una ventana de herramientas.  
  
-   **Siempre** mostrar el contenido de detalle cerca el contenido principal.  
  
-   **Siempre** Asegúrese de que el contenido de detalle todavía permite que un usuario permanezca centrado en el contenido principal. A menudo, la mejor manera de lograrlo es representar el contenido de detalle como cerca el contenido principal como sea posible. Esto puede hacerse representar el contenido de detalle en una ventana emergente junto al contenido principal, o bien el detalle contenido en línea debajo el contenido principal de representación.  
  
-   **Nunca** usar información en el momento de la atención que lleva al usuario fuera el contenido principal. Si los usuarios necesitan ver el contenido de detalle por separado, exponer una acción explícita que permite al usuario hacer esto.  
  
#### <a name="design-details"></a>Detalles de diseño  
 Una vez que haya determinado que la interfaz de usuario en el objeto es la elección correcta, existen cuatro consideraciones de diseño principal:  
  
1.  **Persistencia:** se espera el contenido sea duradero o temporales?   
    ¿Los usuarios desee mantener visible para hacer referencia a o para interactuar con la información? ¿O bien, los usuarios desearán rápidamente Eche un vistazo a la información y, a continuación, continúe con su tarea principal?  
  
2.  **¿Tipo de contenido:** el contenido será informativo, navegación o procesable?   
    ¿El usuario necesita información adicional sobre el contenido principal? ¿El usuario necesita para completar una tarea que afecta al contenido del principal? ¿O bien, necesita el usuario para que se dirijan a otro recurso?  
  
3.  **¿Tipo de indicador:** tiene un indicador de ambiente sentido?   
    ¿Puede la información de resumen en una forma útil y mostrar sin abrumar el contenido principal?  
  
4.  **Movimientos:** qué gestos que se usarán para invocar y descartar la interfaz de usuario?   
    ¿Cómo mostrar el contenido de detalle y enviarlo inmediatamente el usuario? ¿Hay valor en Agregar un gesto como anclaje para alternar entre los estados transitorios y duraderos?  
  
 Cada uno de estos puntos de cuatro decisión tendrá un impacto en los principales componentes de interfaz de usuario del objeto.  
  
### <a name="on-object-ui-components"></a>Componentes de interfaz de usuario en objeto  
  
1.  Tipo de contenedor (moderador contenido)  
  
    -   Flotante  
  
    -   Alineado  
  
2.  Tipo de contenido  
  
    -   Informativo: datos que pueden ser estática o dinámica  
  
    -   Procesables: comandos que cambian el contenido principal  
  
    -   Navegación: vínculos que guiará al usuario a otra ventana o aplicación, como MSDN  
  
3.  Gestos  
  
    -   Invocación  
  
    -   Despido  
  
    -   Fijar  
  
    -   Otras interacciones  
  
4.  Modelo de persistencia y la confirmación  
  
    -   Transitorio  
  
    -   Durable  
  
    -   Automático  
  
    -   A petición  
  
5.  Indicadores de ambiente (opcionales)  
  
    -   Subrayado ondulado  
  
    -   Icono de etiqueta inteligente  
  
    -   Otros indicadores de ambiente  
  
#### <a name="container-content-presenter-type"></a>Tipo de contenedor (moderador contenido)  
 Hay dos opciones principales disponibles para presentar contenido en el momento de atención:  
  
1.  **En línea:** un presentador en línea, como la vista de información que se introdujo en el Editor de código de Visual Studio 2013, para crear espacio para el contenido nuevo trasladando el contenido existente.  
  
    -   **Prefiere** alineado moderadores si espera que los usuarios desearán dedicar una cantidad considerable de tiempo que hace referencia a o interactuar con el contenido a presentar.  
  
    -   **Evitar** alineado moderadores si espera que los usuarios desearán Eche un vistazo a la información que presenta y luego continúe con su tarea principal con interrupciones mínimas.  
  
2.  **Flotante:** un presentador flotante se coloca lo más cerca del contenido seleccionado como sea posible, pero no modificar el diseño del contenido existente. Se pueden emplear diversas estrategias, como mostrar un panel flotante contenido sobre el más cercano disponible espacio en blanco para el símbolo seleccionado.  
  
    -   **Prefiere** flotante moderadores si espera que los usuarios desearán Eche un vistazo a la información que presenta y luego continúe con su tarea principal con interrupciones mínimas.  
  
    -   **Evitar** flotante moderadores si espera que los usuarios desearán que dedicar una cantidad considerable de tiempo que hace referencia a o interactuar con el contenido que está presente.  
  
#### <a name="content-type"></a>Tipo de contenido  
 Hay tres tipos principales de contenido que se pueden mostrar en cualquier contenedor de interfaz de usuario en el objeto. Se puede mostrar cualquier combinación de estos tipos de información. Los tres tipos son:  
  
1.  **Informativo:** contenedores de la interfaz de usuario mostrará algún tipo de contenido informativo a objeto de mayoría. El contenido puede representar la información sobre el estado actual del entorno o puede representar información sobre un estado futuro potencial del entorno. Por ejemplo, podría utilizarse para mostrar el efecto de un comando concreto, como una refactorización en el código existente.  
  
    -   **Siempre** usar la representación canónica de la información que mostrar. Por ejemplo, el código debería ser similar a código, junto con el resaltado de sintaxis y debe respetar la fuente y otras opciones de entorno que el usuario ha establecido.  
  
    -   **Siempre** considere la posibilidad de admitir todas las acciones sobre el contenido informativo que sería posible si esa misma información se presenta como contenido principal. Por ejemplo, si presentar el código existente en un contenedor de interfaz de usuario en el objeto, considere fervientemente admitir la capacidad de examinar y modificar ese código.  
  
    -   **Siempre** considere el uso de un color de fondo diferente si presentar contenido informativo que representa un estado futuro potencial.  
  
2.  Procesables: algunos contenedores de la interfaz de usuario en el objeto proporcionará la capacidad de realizar alguna acción sobre el contenido principal, como realizar una operación de refactorización.  
  
    -   **Siempre** colocar procesables comandos por separado desde el contenido informativo.  
  
    -   **Siempre** habilitar y deshabilitar las acciones cuando corresponda.  
  
    -   **Siempre** hacen referencia a las directrices estándar para representar comandos dentro de los cuadros de diálogo.  
  
    -   **Siempre** mantener mínimo el número de acciones que se exponen en un contenedor de la interfaz de usuario en el objeto en absoluto. Interactuar con la interfaz de usuario del objeto debe ser una experiencia ligera y rápida. El usuario no debe tener dedicar energía acerca de cómo administrar el contenedor de interfaz de usuario en el objeto.  
  
    -   **Siempre** tenga en cuenta cómo y cuándo se cierra o descartar un contenedor de la interfaz de usuario en el objeto. Como práctica recomendada, cualquier acción que concluye el cuadro de diálogo entre el maestro y detalles contenido también debe cerrar el contenedor de la interfaz de usuario en el objeto cuando se llama a esa acción.  
  
3.  **Navegación:** algunos en objetos contenedores de la interfaz de usuario incluyen vínculos que llevan al usuario a otra ventana o aplicación, como la apertura de un artículo MSDN en el explorador del usuario web.  
  
    -   **Siempre** anteponer cualquier vínculo de navegación con "Abierta" para que los usuarios no sorprenderá por algún otro tipo de contenido que se navega.  
  
    -   **Siempre** separar los vínculos de navegación de vínculos útiles.  
  
#### <a name="ambient-indicators-optional"></a>Indicadores de ambiente (opcionales)  
 Indicadores de ambiente pueden ser sutil, incluyendo el texto que se presentan en un color contraste respecto del resto del código, u obvio, incluidos los símbolos de tickler como un subrayado ondulado e iconos de etiqueta inteligente. Indicadores de ambiente comunican la disponibilidad de información adicional relevante. Idealmente, que proporcionan información útil incluso sin solicitar al usuario interactuar con ellos.  
  
-   **Siempre** colocar un indicador de ambiente para que no quede oculta o sobrecargando el usuario. Si no es posible colocar un indicador de ambiente de forma, considere la posibilidad de otra solución.  
  
-   **Siempre** coloca lo más cerca posible al contenido que está relacionado con el indicador de ambiente.  
  
-   **Siempre** intenta crear un indicador que resume la información hace que estén disponible. Considere la posibilidad de proporcionar un recuento del número de elementos de datos disponibles (por ejemplo, "3 referencias" en lugar de simplemente "Referencias") o de alguna otra manera para resumir los datos de reflexión.  
  
    -   En casos en que los datos de un indicador no siempre se calcula y muestra, inmediatamente se considera comentarios progresiva tal y como se calculan los valores. Por ejemplo, considere la posibilidad de animar cambios que reflejan las actualizaciones de los datos disponibles, de forma similares a la forma en que el icono dinámico de correo electrónico en Windows Phone se actualiza cuando el número de mensajes de correo electrónico no leído aumenta.  
  
-   **Nunca** agregar indicadores más de un usuario puede razonablemente llevar a cabo una parte determinada del contenido. Indicadores de ambiente deben ser útiles sin necesidad de intervención del usuario. Indicadores de perderán su ambiente si necesitan desbordamiento y otros controles de administración para volver a ponerlos en la vista.  
  
#### <a name="gestures"></a>Gestos  
 Un aspecto clave de permitir que el usuario mantener el foco en el contenido principal es admitiendo los movimientos de la derecha para abrir y descartar el contenido de detalles adicionales.  
  
-   **Siempre** requiere que el usuario realizar algunas gesto explícito para abrir el contenido adicional. Gestos de abrir comunes son:  
  
    -   **Al mantener el mouse:** información sobre herramientas o contenido informativo no interactivo  
  
    -   **Comando explícito:** presentador en línea  
  
    -   **Haga doble clic en el indicador de ambiente:** ventana emergente de CodeLens  
  
-   **Siempre** descartar el contenido de detalle cada vez que el usuario presiona la tecla Esc.  
  
-   **Siempre** tenga en cuenta el contexto de la interfaz de usuario en el objeto. Para contenido moderadores que permiten la interacción dentro del contenedor, tenga en cuenta si se debe mostrar información adicional al mantener el mouse, que suele ser perjudiciales para el flujo de trabajo del usuario.  
  
-   **Nunca** mostrar contenido al mantener el mouse que parece ser editable o invita a la interacción del usuario. Este comportamiento puede frustrar a los usuarios si intentan mover el cursor sobre el contenido de detalle, como es el comportamiento estándar para una información sobre herramientas descartar inmediatamente cuando el cursor ya no está por encima del patrón contenido que lo generó.  
  
##  <a name="BKMK_SelectionModels"></a> Modelos de selección  
  
### <a name="overview"></a>Información general  
 Un modelo de selección es el mecanismo utilizado para indicar y confirmar las operaciones en uno o varios objetos de interés dentro de la interfaz de usuario. Este tema describen los patrones de interacción de selección en los editores de documento de Visual Studio: editores de texto, superficies de diseño y modelado de superficies.  
  
 Los usuarios deben tener una forma de indicar a Visual Studio qué están trabajando, y Visual Studio debe responder previsiblemente con comentarios a los usuarios sobre lo que se está ejecutando en. Puede dar lugar a una falta de comunicación entre el usuario y la interfaz de usuario o de diferencias en el usuario no teniendo en cuenta una acción, que puede tener consecuencias no deseadas. A menudo, el error inadvertido hasta que el usuario ve que falta algo o ha cambiado. Los modelos de selección son, por tanto, uno de los elementos más importantes de diseño de la interfaz de usuario. Aunque los modelos de selección en Visual Studio son coherentes con Windows, hay pequeñas variaciones.  
  
 En Visual Studio, como en Windows, los modelos de selección varían según el contexto en el que se produce la interacción. Las selecciones pueden producirse en cuatro tipos de objetos:  
  
-   Texto  
  
-   Objetos gráficos  
  
-   Listas y árboles  
  
-   Cuadrículas  
  
 Dentro de estos objetos, hay tres tipos de selecciones:  
  
-   Contiguos  
  
-   No contiguo  
  
-   Región  
  
#### <a name="scope"></a>Ámbito  
 El componente más importante de selección es asegurarse de que el usuario sabe en qué ventana trabajan (activación) y donde el foco está ubicada (selección). Visual Studio extiende la funcionalidad de administración de la ventana de Windows, pero el esquema de activación es el mismo: interactuar con una ventana trae el foco a la ventana. Visual Studio tiene dos indicadores para la activación: uno para las ventanas de documento y otro para las ventanas de herramientas.  
  
 Para las ventanas de documento, la ventana activa se indica mediante la pestaña de una ventana de documento que llegue a la parte delantera y cambiar su color de fondo:  
  
 ![Selección de pestaña activa en Visual Studio](../../extensibility/ux-guidelines/media/0713-01_activetab.png "01_ActiveTab 0713")  
  
 **Selección de pestaña activa**  
  
 Para las ventanas de herramientas, la ventana activa se indica mediante un cambio en el color del área de la barra de título de la ventana de herramientas:  
  
 ![Selección de ventana de herramientas activa en Visual Studio](../../extensibility/ux-guidelines/media/0713-02_activetoolwindow.png "02_ActiveToolWindow 0713")  
  
 **Mostrar selección primaria de un nodo de ventana de herramientas activa**  
  
 ![Selección de ventana de herramientas inactiva en Visual Studio](../../extensibility/ux-guidelines/media/0713-03_inactivetoolwindow.png "03_InactiveToolWindow 0713")  
  
 **Ventana de herramientas inactiva, mostrando latente selección del nodo**  
  
 Una vez que una ventana está activa, se indica su enfoque según los modelos de selección que se describen en esta sección de las instrucciones.  
  
#### <a name="context"></a>Contexto  
 Visual Studio fue diseñado para conservar un concepto seguro de contexto, realizar el seguimiento de donde el usuario está trabajando. Sólo una ventana está activa, si es una ventana de herramientas o de documento. Sin embargo, la ventana de documento de nivel superior siempre conserva una selección latente. Aunque es posible el foco en una ventana de herramientas, la ventana de documento que estaba activo por última vez muestra una selección, incluso en un estado inactivo. Esto sirve para conservar el contexto del usuario en el documento que estaban editando, mostrándoles que Visual Studio ha conservado su estado de forma que puede volver y cambiar sin problemas entre las ventanas de herramientas y ventanas de documento.  
  
### <a name="text-selection"></a>Selección de texto  
 Los editores de Visual Studio que sean estrictamente textuales, como el editor de texto integrado, usan el mismo modelo de selección de texto y apariencia se describe en la [mouse (ratón) y punteros](https://msdn.microsoft.com/en-us/library/dn742466.aspx) página de Windows User Experience Interaction Guidelines en MSDN. El foco de entrada en el editor de texto se indica mediante una barra vertical que llama el punto de inserción. El punto de inserción es un solo píxel grueso y color como el inverso de todo lo que aparece detrás de él. Parpadea según la frecuencia establecida el **velocidad de intermitencia del Cursor** en el **velocidad** pestaña de la **teclado** applet del Panel de Control.  
  
#### <a name="contiguous-and-disjoint-selection"></a>Selección de contigua y no contiguo  
 Solo es contiguo selección en el editor de texto. Texto selecciones no están permitidas, pero deben llevar a cabo en el Editor de objeto gráfico inconexos. Cuando el puntero del mouse está sobre un área de texto, el cursor cambia a un cursor en i. Un solo clic, coloca el punto de inserción en el editor de texto en la ubicación de haga clic en. Mantenga presionado el botón del mouse inicia un resalte de la selección y soltar el botón del mouse (ratón) finaliza el resalte de la selección.  
  
#### <a name="region-selection-box-selection"></a>Selección de región (selección de cuadro)  
 Visual Studio es compatible con selecciones de región en el editor de texto, y esto se denomina selección del cuadro. Selección del cuadro permite al usuario seleccionar un área de texto que no sigue la secuencia de texto normal. Al igual que con la selección de texto estándar, la selección debe ser contigua. Selección del cuadro se inicia manteniendo presionada la tecla Alt mientras arrastra el puntero con el mouse. También se puede iniciar la selección del cuadro manteniendo presionadas las teclas de desplazamiento y Alt mientras usa las teclas de dirección para indicar la región de selección. Selección del cuadro usa el resaltado de selección normal y muestra el cursor del punto de inserción parpadea al final del área de selección.  
  
 ![Regional &#40;cuadro&#41; selección en Visual Studio](../../extensibility/ux-guidelines/media/0713-04_boxselection.png "04_BoxSelection 0713")  
  
 **Selección de región (cuadro) en Visual Studio**  
  
#### <a name="text-selection-appearance"></a>Apariencia de la selección de texto  
 Se pueden personalizar los colores utilizados para la selección activa e inactiva en el editor. Para personalizar la apariencia visual del editor, un usuario puede ir a **Herramientas > opciones**y después haga clic en **entorno > fuentes y colores > Editor de texto**.  
  
### <a name="graphical-selection"></a>Selección de gráfico  
  
#### <a name="interaction"></a>Interacción  
 Selección de objetos gráficos puede ser compleja y depende de una serie de factores:  
  
-   **El modelo del editor selección primaria.** Los editores que contienen objetos gráficos también pueden utilizarse para editar texto o cuadrículas. Por ejemplo, el editor podría ser un editor de texto que también es compatible con la colocación de objetos gráficos, como el Diseñador XAML de Visual Studio. Compatibilidad con varios tipos de objeto puede afectar a cómo el usuario selecciona grupos formados por diferentes tipos de objetos.  
  
-   **Compatibilidad con los Estados de selección primaria y secundaria.** Un editor puede proporcionar selección primaria y secundaria Estados para que los objetos se pueden editar en al mismo tiempo, alineados entre sí, cambiar de tamaño juntos, y así sucesivamente.  
  
-   **Compatibilidad de edición en contexto.** Los editores también pueden permitir que el contenido de sus objetos gráficos que se pueda editar. Por ejemplo, una forma de rectángulo también podría contener texto interno que puede cambiarse por el usuario. Además, que el texto se podría centrado o justificado. Edición en contexto implica un nivel más detallado de la interacción del usuario y, por tanto, requiere un conjunto adecuado de indicaciones visuales para presentar la información de estado al usuario.  
  
#### <a name="mouse-interaction"></a>Interacción con el mouse  
  
|Entrada|Resultado|  
|-----------|------------|  
|Haga clic en un objeto no seleccionado|Selecciona el objeto y se muestra una línea discontinua y controladores de selección, si el objeto se puede cambiar el tamaño.|  
|Haga clic en un objeto seleccionado|Activa la edición en contexto si el objeto lo admite. Hacer clic fuera del objeto, desactiva el modo de edición en contexto.|  
|Haga doble clic en un objeto|Se abre el código detrás del objeto para su edición y podría insertar un controlador de eventos de forma predeterminada, si procede.|  
|Seleccione un objeto|Cambia el puntero hasta el cursor de movimiento. Puede cambiar la apariencia del objeto, como su luminosidad o color.|  
|Seleccione un controlador de selección|Cambia el puntero hasta el cursor de cambio de tamaño. Para los objetos que admiten la rotación, algunos controladores de selección pueden cambiar el puntero a un cursor Girar tal y como se sitúa el puntero diferente (por ejemplo, si se mueven más lejos) en relación con el controlador de selección.|  
|Arrastre|Incluso si el objeto no se ha seleccionado anteriormente, cambia el puntero hasta el cursor de movimiento y mueve el objeto.|  
|Editor de pierde el foco|Desactiva el modo de edición en contexto, aunque el objeto conserva el contenido y el aspecto que tenía durante su último estado de operación/selección.|  
|Selección de objetos|Indicado por un borde, línea de puntos u otro tratamiento visualmente distinto para resaltar el límite del objeto.|  
|Cambiar el tamaño de un objeto seleccionado|Indicado por controladores de selección.<br /><br /> Un objeto puede cambiar el tamaño tiene ocho controladores, que representa cada dirección en la que puede cambiarse. Si el objeto solo pueden cambiarse en determinadas direcciones, se pueden usar identificadores de menos. Cuando el usuario cambia el tamaño de un objeto hasta donde ocho controladores de no ser interactivas, pueden utilizarse cuatro identificadores. Tamaños de identificador deben asociarse a las métricas de borde y el borde de ventana con la **GetSystemMetrics** función de la API para el tamaño proporcionalmente a la resolución de pantalla.<br /><br /> ![Controladores de tamaño](../../extensibility/ux-guidelines/media/0713-05_resizehandles.png "05_ResizeHandles 0713")|  
|Girar un objeto seleccionado|![Controladores de giro](../../extensibility/ux-guidelines/media/0713-06_rotate.png "06_Rotate 0713")|  
  
#### <a name="keyboard-interaction"></a>Interacción con el teclado  
  
|Entrada|Resultado|  
|-----------|------------|  
|Tab|Mueve el indicador de foco entre el orden lógico de objetos en el editor. Puede tratarse de izquierda a derecha o de arriba a abajo según **TabIndex** (o equivalente) valor de propiedad, el orden de creación de objetos y el propósito general del editor. MAYÚS + Tabulador invierte la dirección de los indicadores de foco.|  
|Barra espaciadora|Activa el modo de panorámico mientras se mantiene la pulsación de tecla. Entrada de mouse adicional es necesario para aplicar una panorámica de la posición de la ventanilla.|  
|Ctrl+Barra espaciadora|Activa el modo de zoom mientras se mantiene la pulsación de tecla. Entrada de mouse adicional es necesario para aumentar y disminuir el factor de zoom.|  
|Ctrl + Alt + signo menos|Disminuye el factor de zoom en un nivel.|  
|Ctrl + Alt + signo más|Aumenta el factor de zoom en un nivel.|  
|MAYÚS o Ctrl|Agrega el objeto al grupo de selección. CTRL también permite quitar los objetos por separado desde el grupo de selección.|  
|Entrar|Realiza el comando predeterminado para el objeto (normalmente se abre o editar).|  
|F2|Activa la edición en contexto para el objeto.|  
|Teclas de dirección|Mueve los objetos seleccionados en la dirección de la tecla presionada, en incrementos pequeños (por ejemplo, 1 píxel a la vez)|  
|CTRL + teclas de dirección|Mueve los objetos seleccionados en la dirección de la tecla presionada, en incrementos mayores (por ejemplo, 10 píxeles a la vez)|  
|Mayús + flecha claves|Cambia el tamaño de los objetos seleccionados en la dirección correspondiente, en incrementos pequeños (por ejemplo, 1 píxel a la vez)|  
|Ctrl + Mayús + teclas de dirección|Cambia el tamaño de los objetos seleccionados en la dirección correspondiente, en incrementos mayores (por ejemplo, 10 píxeles a la vez)|  
  
 Cuando los usuarios modificar controles en su lugar, tendría sentido para los objetos que se va a cambiar de forma automática con proporcionados por el usuario. Por ejemplo, si el usuario edita un control de etiqueta, la etiqueta debe crecer para mostrar el texto que acaba de escribir el usuario. Si no es así, el usuario debe cambiar el tamaño del control manualmente después de editar el texto. Si el usuario tiene una gran cantidad de controles, se convierte en una tarea improductivo y básicas.  
  
#### <a name="graphical-containers"></a>Contenedores de gráficos  
 En algunos casos, editores gráficos proporcionan contenedores para otros objetos gráficos, como el control de Panel de Windows Forms o el diseño de cuadrícula en el Diseñador HTML. Si el editor proporciona contenedores para otros objetos gráficos, el siguiente modelo de selección debe utilizarse para el contenedor solo (objetos en el seguimiento de contenedor del modelo estándar como se ha descrito anteriormente):  
  
|Entrada|Resultado|  
|-----------|------------|  
|Hacer clic en el contenedor|Selecciona el objeto de contenedor sin directamente si se selecciona cualquiera de los objetos contenidos. El contenedor se puede mover o cambiar de tamaño con estándar mouse y teclado (tal y como se ha descrito anteriormente). Objetos contenidos se mueven en relación al contenedor, pero los objetos contenidos no se cambia el tamaño a menos que se seleccionan directamente.|  
|Mantenga el mouse sobre la región de límites del contenedor|El mouse se convierte en el cursor de movimiento, que indica que se puede mover el contenedor.|  
|Arrastre el control región de límites del contenedor|Cambia el mouse hasta el cursor de movimiento y mueve el contenedor (y los objetos contenidos en). El contenedor no se pueden mover sin primero se seleccionan con un solo clic.|  
|Hacer clic en un objeto dentro del contenedor|Anula el contenedor (si ha seleccionado) y selecciona sólo el objeto donde ha hecho clic.|  
|Mayús + clic o Ctrl + clic en un objeto independiente o un contenedor|Agrega el objeto donde ha hecho clic en un grupo de selección o selección existente. Si el objeto ha hecho clic ya es miembro del grupo de selección, se quita del grupo de selección.|  
  
 Los objetos contenidos deben respetar el modelo de selección básica como se describe en la sección anterior. De las pruebas de facilidad de uso del Diseñador de Windows Forms, espera que los usuarios un acceso ininterrumpido a los objetos contenidos sin intervención de los pasos (impuestas por el objeto de contención).  
  
#### <a name="disjoint-and-region-selections"></a>Discontinuas y las selecciones de región  
 Editores de objeto gráfico deben admitir selecciones discontinuas. Tenga en cuenta que este gráfico no muestra la apariencia de los controles para Visual Studio. Vea [apariencia de selección de objeto gráfico](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_GraphicalObjectSelectionAppearance) para obtener especificaciones detalladas visuales.  
  
 ![Discontinuas selectores de región y](../../extensibility/ux-guidelines/media/0713-07_disjointregionselectors.png "07_DisjointRegionSelectors 0713")  
  
 **Selección separado**  
  
 Editores gráficos también deben proporcionar las selecciones de la región con un indicador de selección de tipo de marquesina. Si el editor gráfico de es compatible con otros tipos de objeto (por ejemplo, texto), selecciones de región no sería posibles según las restricciones de esos otros tipos de objeto.  
  
 ![Selección de recuadro](../../extensibility/ux-guidelines/media/0713-08_marqueeselection.png "08_MarqueeSelection 0713")  
  
 **Selección de recuadro**  
  
#### <a name="primary-and-secondary-selections"></a>Selecciones principal y secundaria  
 Algunos editores de objeto gráfica permiten al usuario editar o alinear objetos en los grupos. En este caso, se necesita introducir el concepto de selecciones principal y secundaria. La selección primaria es el objeto al que todos los demás objetos responden para las operaciones de grupo. El objeto que el usuario seleccione primero se convierte en el control primario y selecciones posteriores se convierten en las selecciones secundarias. La selección primaria tiene un tratamiento distinto visual de las selecciones secundarias para indicar el objeto que es el principal:  
  
 ![Selección primaria y secundaria](../../extensibility/ux-guidelines/media/0713-09_primarysecondary.png "09_PrimarySecondary 0713")  
  
 **Selección primaria con dos selecciones secundarias**  
  
####  <a name="BKMK_GraphicalObjectSelectionAppearance"></a> Apariencia de la selección de objeto gráfico  
 Los controladores de selección son cuadrados dibujados en un patrón rectangular alrededor del cuadro de límite del objeto. La siguiente tabla muestra ejemplos de los diferentes Estados que puede tener un objeto gráfico en identificador, el tamaño y la apariencia de edición en contexto. El tamaño de los identificadores debe asociarse a borde de ventana y el uso de las métricas de borde la **GetSystemMetrics** API.  
  
|Estado|Apariencia|Detalles de Visual|  
|-----------|----------------|--------------------|  
|**Anular la selección**|Default|![Estado del botón predeterminado](../../extensibility/ux-guidelines/media/0713-10_defaultstate.png "10_DefaultState 0713")||  
|**Selección primaria**|Puede cambiar el tamaño|![Selección primaria con controladores de tamaño](../../extensibility/ux-guidelines/media/0713-11_primaryresize.png "11_PrimaryResize 0713")|![Selección primaria con controladores de tamaño &#40;ampliada&#41;](../../extensibility/ux-guidelines/media/0713-12_primaryresizezoom.png "12_PrimaryResizeZoom 0713")|  
|**Selección primaria**|No puede cambiar el tamaño|![Selección primaria sin controladores de tamaño](../../extensibility/ux-guidelines/media/0713-13_primarynoresize.png "13_PrimaryNoResize 0713")|![Selección primaria sin controladores de tamaño &#40;ampliada&#41;](../../extensibility/ux-guidelines/media/0713-14_primarynoresizezoom.png "14_PrimaryNoResizeZoom 0713")|  
|**Selección primaria**|Bloqueado|![Selección primaria bloqueada](../../extensibility/ux-guidelines/media/0713-15_primarylocked.png "15_PrimaryLocked 0713")|![Selección primaria bloqueada &#40;ampliada&#41;](../../extensibility/ux-guidelines/media/0713-16_primarylockedzoom.png "16_PrimaryLockedZoom 0713")|  
|**Selección secundaria**|Puede cambiar el tamaño|![Selección primaria con controladores de tamaño](../../extensibility/ux-guidelines/media/0713-17_secondaryresize.png "17_SecondaryResize 0713")|![Selección primaria con controladores de tamaño &#40;ampliada&#41;](../../extensibility/ux-guidelines/media/0713-18_secondaryresizezoom.png "18_SecondaryResizeZoom 0713")|  
|**Selección secundaria**|No puede cambiar el tamaño|![Selección secundaria sin controladores de tamaño](../../extensibility/ux-guidelines/media/0713-19_secondarynoresize.png "19_SecondaryNoResize 0713")|![Selección secundaria sin controladores de tamaño &#40;ampliada&#41;](../../extensibility/ux-guidelines/media/0713-20_secondarynoresizezoom.png "20_SecondaryNoResizeZoom 0713")|  
|**Selección secundaria**|Bloqueado|![Selección secundaria bloqueada](../../extensibility/ux-guidelines/media/0713-21_secondarylocked.png "21_SecondaryLocked 0713")|![Selección secundaria bloqueada &#40;ampliada&#41;](../../extensibility/ux-guidelines/media/0713-22_secondarylockedzoom.png "22_SecondaryLockedZoom 0713")|  
|**Interfaz de usuario activa**|Default|![Estado activo de interfaz de usuario](../../extensibility/ux-guidelines/media/0713-23_uiactive.png "23_UIActive 0713")|![Estado activo de interfaz de usuario &#40;ampliada&#41;](../../extensibility/ux-guidelines/media/0713-24_uiactivezoom.png "24_UIActiveZoom 0713")|  
  
### <a name="view-selection-models"></a>Modelos de selección de vista  
  
#### <a name="tree-view"></a>Vista de árbol  
 Se muestra la selección en una vista de árbol con un resaltado simple. Si el usuario hace clic en un nombre de nodo o un icono de nodo, el nodo deja de estar seleccionado. Los glifos triangulares a la izquierda del nodo expandir o contraer el control de árbol pero no afectan a la selección del usuario, con una excepción: al contraer un nodo primario cuando la selección está en un elemento secundario de ese nodo, la selección se mueve al elemento primario.  
  
 ![Vista de árbol típica de Visual Studio](../../extensibility/ux-guidelines/media/0713-25_treeview.png "25_TreeView 0713")  
  
 **Vista de árbol típica de Visual Studio**  
  
 Vistas de árbol pueden admitir selecciones contiguas y no contiguas, incluso a través de varios niveles del árbol. Contiguos o no contiguos se deben realizar varias selecciones en los nodos de árbol visible. Si un nodo está contraído, la selección no contiguo se pierde y el nodo que se contrajo Obtiene la selección. De esta manera, el usuario puede ver los nodos que se verán afectados por una operación. Cuando se contraen los nodos, se vuelve claro qué nodos podrían verse afectados.  
  
 Cuando se selecciona un nodo primario, debe aplicar la operación al elemento primario, aunque puede haber casos en relacione con una operación aplicar el elemento primario y todos sus elementos secundarios. En este caso, proporcionan la interfaz de usuario adicional durante la operación, como una casilla de verificación o el cuadro de diálogo de confirmación para que la opción "aplicar a todos los elementos secundarios" explícita para el usuario.  
  
##### <a name="renaming"></a>Cambiar nombre  
 Si los nodos del árbol admiten el cambio de nombre, cambiar el nombre debe realizarse en su lugar. La operación en el contexto debe ser el estándar en todos los controles de árbol en Visual Studio. Proporciona un comando de cambio de nombre que se activa inmediatamente el modo de edición en contexto, con la selección de texto que abarcan el nombre completo del nodo, listo para aceptar proporcionados por el usuario. Si el nodo representa un archivo, el nombre de archivo debe contener la extensión. El resaltado de selección debe incluir solo el cuerpo del nombre de archivo y no la extensión.  
  
|Entrada|Resultado|  
|-----------|------------|  
|Entrar (tecla)|Confirma la operación de cambio de nombre|  
|Tecla ESC|Cancela la operación de cambio de nombre|  
|Hacer clic fuera de la región de edición en contexto|Confirma la operación de cambio de nombre|  
|Deshacer|Proporcionar fácil deshacer para cancelar la operación de cambio de nombre|  
  
#### <a name="selection-within-lists-and-grid-controls"></a>Selección de listas y los controles de cuadrícula  
 El concepto clave en la selección de la lista es que está basado en la fila, lo que significa que cuando se realiza una selección toda la fila está seleccionada como una unidad. Por el contrario, cuadrículas pueden permitir que determinadas celdas seleccionarse sin afectar a cualquier otro aspecto de la fila. Cuadrículas también podrían contener una jerarquía de filas anidadas (como en un control TreeGrid) que permiten todos ramas de la jerarquía se selecciona y se anula la selección mediante la interacción con las filas primarias. Selección en las listas se indica con un color de resaltado simple en toda la fila de datos. Enfoque se indica con un borde con puntos de píxel alrededor de la fila editable actual o la celda (fila si todas las celdas son de solo lectura).  
  
> [!NOTE]
>  **Foco** y **selección** son conceptos diferentes. *Foco* es una indicación de qué interfaz de usuario tiene como destino el elemento para recibir entrada dirigido no explícitamente a otro objeto, mientras que *selección* se refiere al estado de inclusión de un objeto de un conjunto de objetos en los que posteriores pueden realizar operaciones.  
  
 Las selecciones en las listas pueden ser contiguas, separado, o la región. Cuando selecciones múltiples están permitidos, contiguo y siempre debe ser compatibles selección separado al soporte técnico para las selecciones de región (cuadro) son opcional. Selecciones de región se inician y arrastrándola en el espacio en blanco del cuerpo de la lista.  
  
|Object|Selección|  
|------------|---------------|  
|Lista|Contiguos|Siempre admiten (cuando se permiten selecciones múltiples).|  
|Lista|No contiguo|Siempre admiten (cuando se permiten selecciones múltiples).|  
|Lista|Región|Compatibilidad opcional con. Iniciar arrastrando el mouse en el espacio en blanco del cuerpo de la lista.|  
  
 Al hacer clic una vez en una lista, selecciona la fila en el que hizo clic. Si el usuario haga clic en una celda de la lista que admite la edición en contexto, la celda se activa también inmediatamente para su edición en contexto. En caso contrario, la fila completa inmediatamente queda seleccionada y muestra un resaltado.  
  
 Arrastrar en el cuerpo de la lista, realiza una de estas tres cosas:  
  
-   Inicia una selección de región, si lo admite la lista y la profundidad del mouse se encuentra en el espacio en blanco  
  
-   Inicia una operación de arrastrar y colocar si la fila o celda de la lista admite que se va a un origen de arrastre  
  
-   Selecciona la fila actual  
  
##### <a name="in-place-editing"></a>Edición en contexto  
 Cuando se permite la edición en contexto, hay dos modelos básicos: selector de control y la propiedad de edición simple. Con un control de edición simple, el contenido está resaltado y listo para entrada tan pronto como se activa la edición en contexto del usuario. Cuando se implementa un selector de propiedades, se muestra el botón que invoca el selector de propiedad una vez que se activará el modo de edición en contexto y la selección actual no está resaltada. El botón selector debe estar justificado a la derecha en la celda. Para obtener ejemplos de edición en contexto, vea la **ventana propiedades** y **lista de tareas** en Visual Studio.  
  
##### <a name="keyboard-support"></a>Compatibilidad con el teclado  
 Compatibilidad con el teclado para la selección en listas y cuadrículas sigue las convenciones estándar de Windows:  
  
-   Teclas de dirección desplazarse por la lista, seleccione cada celda de filas mientras se mueve el foco.  
  
-   Mayús + flecha realiza una selección contigua en la dirección de las teclas de dirección.  
  
-   Ctrl + flecha seguido de barra espaciadora alterna entre agregar y quitar elementos de la lista de la selección, crear una selección no contiguo.  
  
-   Para las cuadrículas que contienen las jerarquías anidadas, la tecla flecha derecha expande una fila primaria y la tecla flecha izquierda contrae uno.  
  
-   La tecla Tab mueve el foco entre las celdas de la fila actual si las celdas se pueden modificables.  
  
-   La tecla ENTRAR realiza el comando predeterminado en el elemento en la lista (a menudo **abiertos**).  
  
-   La tecla F2 activa la edición en contexto para la celda seleccionada actualmente.  
  
##  <a name="BKMK_PersistenceAndSavingSettings"></a> Persistencia y guardar la configuración  
  
### <a name="overview"></a>Información general  
 Aunque es suele ser responsable de su propio estado y persistencia de cada componente de software en Visual Studio, Visual Studio guarda la configuración en algunos casos, como con posiciones y tamaños de ventana. En la tabla siguiente es una combinación de opciones que se guardan automáticamente y que requieren un usuario explícito o programarse la acción que se realizará.  
  
|Object|Lo que se debe guardar|Cuándo se debe guardar|Dónde guardar|  
|------------|------------------|------------------|-------------------|  
|Objeto seleccionable (por ejemplo, una línea de código)|Un punto de interrupción en una línea de código<br /><br /> Un acceso directo de usuario asociado a la línea de código|Cuando se guarda el proyecto|El **opciones de usuario (.suo)** archivo para el proyecto|  
|Cuadro de diálogo|La ubicación del cuadro de diálogo, si se han movido<br /><br /> La vista que el usuario utilizó por última vez en el cuadro de diálogo|Cuando se cierra el cuadro de diálogo<br /><br /> Cuando finaliza la sesión de Visual Studio|En la memoria<br /><br /> Registro en **HKEY_Current_User**|  
|Ventana|El tamaño y la ubicación de la ventana|Cuando se cierra la ventana<br /><br /> Cuando se cambia el modo de Visual Studio<br /><br /> Cuando finaliza la sesión de Visual Studio|El **opciones de usuario (.suo)** archivo para el proyecto<br /><br /> Archivo de opciones personalizadas para la configuración de la ventana|  
|Documento|La selección actual en el documento<br /><br /> La vista del documento<br /><br /> El último varios lugares, el usuario ha visitado|Cuando se guarda el documento|El **opciones de usuario (.suo)** archivo para el proyecto|  
|Proyecto|Referencias a archivos<br /><br /> Referencias a los directorios en el disco<br /><br /> Referencias a otro software<br /><br /> Componentes<br /><br /> Información de estado sobre el propio proyecto|Cuando se guarda el proyecto|El archivo de proyecto|  
|Soluciones|Referencias a proyectos<br /><br /> Referencias a archivos|Cuando se guarda el proyecto o solución|El **solución (.sln)** archivo|  
|Configuración de **Herramientas > Opciones**|Personalizaciones del teclado<br /><br /> Personalizaciones de la barra de herramientas<br /><br /> Combinaciones de colores|Cuando el **Herramientas > opciones** cierra el cuadro de diálogo<br /><br /> Cuando finaliza la sesión de Visual Studio|Registro en **HKEY_Current_User**|  
  
 ¿Qué está haciendo el usuario y cuando está realizando, determina si una configuración se guarda en la memoria (durante la sesión), que se guardan en el disco (en las sesiones como una configuración del registro), como parte de la solución o proyecto propio archivo, como parte de la **solución Opciones (.suo)** de archivos o como una configuración personalizada de archivos que sólo ese componente de software conoce. La tabla anterior muestra varios eventos en el que se puede guardar configuración. Sin embargo, hay otras ocasiones en que puede guardar el estado:  
  
-   Cuando el usuario cambia la ubicación de un cuadro de diálogo o ventana  
  
-   Cuando el usuario transfiere el foco a otra ventana  
  
-   Cuando el usuario cambia de diseño en modo de depuración  
  
-   Cuando el usuario cierra su cuenta  
  
-   Cuando se pasa a hibernación o se apaga el equipo  
  
-   Cuando la unidad de disco duro equipo está a punto de ser volver a formatear y volver a configurar  
  
### <a name="window-configurations"></a>Configuraciones de ventanas  
 Una configuración de la ventana es la presentación básica del entorno de desarrollo: es un esquema que se compone de la lista de las ventanas de herramientas está presentes y la manera en que se organizan. Para windows administradas por el IDE (ventanas del IDE), información de diseño se conserva por usuario, lo que cuando un usuario ejecute el IDE, el diseño de ventana aparece el mismo que cuando duran salió de Visual Studio. El estado y la posición de las ventanas del IDE se guardan en un archivo de opciones personalizadas en formato XML. Ventanas de herramientas que se crean paquetes que se cargan en el IDE de conservan su información de estado en el registro y pueden o no ser por usuario.  
  
#### <a name="profile-specific-layouts"></a>Diseños específicos de perfil  
 Cada perfil incluye diseños de ventana de herramienta, organizados en una forma que resultará familiar a los roles de desarrollador determinado (esperar que los desarrolladores de Visual C++ ver el **el Explorador de soluciones** en el lado izquierdo del IDE, mientras que los desarrolladores de C# esperan que se muestre el  **El Explorador de soluciones** a la derecha). Diseños de ventana específica del perfil se cargan después de que el usuario elija un perfil en el inicio. Un autor del paquete debe determinar el diseño de ventana más adecuado para la experiencia de sus clientes, sabiendo que, a continuación, se conservarán los cambios que el usuario realice en la configuración de la ventana.  
  
##  <a name="BKMK_TouchInput"></a> Entrada táctil  
 Los usuarios utilizan cada vez más productos de desarrollo de Microsoft en dispositivos táctiles. Sin embargo, existen obstáculos que hacen que sea difícil utilizar herramientas de desarrollo en dispositivos táctiles. Los usuarios esperarán que nuestros productos para proporcionar una experiencia táctil confiable y precisa. El propósito de estas instrucciones es informar a ninguna decisión sobre qué funciones táctiles para incorporar y animar a una experiencia táctil coherente entre Visual Studio y productos relacionados.  
  
### <a name="levels-of-experience"></a>Niveles de experiencia  
 Los siguientes niveles de experiencia están diseñados para actuar como una guía para ayudar a los equipos a decidir qué funciones táctiles para ofrecer basan en su nivel deseado de interés de la inversión en contacto.  
  
-   El **experiencia básica** es para equipos que desean proporcionar touch capacidades, por lo que no hay ningún extremos no enviados a lo largo de su trabajo.  
  
-   El **optimizado experiencia** es para equipos que desee proporcionar más capacidades táctiles (por ejemplo, las que suelen estar disponibles en las aplicaciones de explorador de internet).  
  
-   El **elevados experiencia** es para equipos que desean agregar capacidades tales como gestos u otras capacidades opcionales que pueden hacer que su aplicación táctil primero descriptivo.  
  
||Experiencia básica|Experiencia optimizada|Experiencia con privilegios elevados|  
|-|----------------------|--------------------------|-------------------------|  
|Permite a los usuarios...|Corrija el código y solución/nivel de proyecto de lectura sin extremos no enviados|Realizar tareas de mantenimiento, refactorizaciones y navegación|Operar en una experiencia coherente, intuitiva y fluida con confianza|  
|Editor|Modo panorámico táctil y la selección<br /><br /> Barra de desplazamiento táctil para saltar y presione + arrastrar|Acercar alejar<br /><br /> Desplazamiento rápido<br /><br /> Selección<br /><br /> Fácil de usar del menú contextual||  
|Ventanas de herramientas superior|Aplicar una panorámica en lista<br /><br /> Selección de elementos<br /><br /> Barra de desplazamiento táctil para saltar y presione + arrastrar|Desplazamiento de elemento fácil y selección||  
|Ventana||Cambiar el tamaño de ventana<br /><br /> Acceso rápido||  
|Cuadro de documento||Facilitar el desplazamiento entre los archivos abiertos||  
|Gestos||Asegúrese de movimientos comunes pueden funcionar en el IDE|Acciones de gestos<br /><br /> Compatible con arrastrar y colocar y diseñadores|  
|Otras consideraciones|||Teclado en pantalla personalizado|  
  
#### <a name="gestures"></a>Gestos  
 Movimientos de proporcionan a los usuarios un acceso directo a los comandos que en caso contrario, podrían requerir una interacción más complicada. Consulte las instrucciones de Windows en [gestos táctiles para las aplicaciones de escritorio](http://msdn.microsoft.com/en-us/library/windows/desktop/dd940543\(v=vs.85\).aspx)y siga estas instrucciones para los gestos mayoría, incluidos los gestos simples como panorámica y zoom.