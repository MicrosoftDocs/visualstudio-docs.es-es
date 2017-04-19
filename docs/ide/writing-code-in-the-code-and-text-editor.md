---
title: "Escribir código en el editor de código | Microsoft Docs"
ms.custom: 
ms.date: 03/28/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.texteditor
dev_langs:
- JScript
- VB
- CSharp
helpviewer_keywords:
- code editor, word wrap
- outlining
- code, editing
- squiggles
- code editor, outlining
- code editor, error and warning markers
- word wrap
- code editor, syntax coloring
- code editor, go to definition
- diff
- code editor [Visual Studio]
- code editor, diff
- error and warning markers
- code editor, navigation bar
- code editor, customizing
- comment selection
- code editor, tabify
- brace matching
- code editor, line numbers
- printing
- code editor, brace matching
- code editor, squiggles
- code editor, features
- line numbers
- go to definition
- syntax coloring
- code editor, go to
- code editor, comparing files
- code editor, zoom
- code editor
- code files
- go to line
- tabify
- zoom
- go to
- line break characters
- code editor, virtual space
- code editor, change tracking
- code editor, comment selection
- code editor, printing
- virtual space
- code editor, line break characters
- code editor, go to line
- code
ms.assetid: cb53ab9a-5b76-4759-b9e8-7bf32298ecbe
caps.latest.revision: 44
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 06cdfb076120ffd7459a16b56c659bb86942cd7f
ms.openlocfilehash: c5e8972cf5efb5596f7649df2c622e802803319f
ms.lasthandoff: 03/31/2017

---
# <a name="write-code-in-the-code-editor"></a>Escribir código en el editor de código
El editor de Visual Studio proporciona muchas características que le facilitan la escritura y la administración del código y del texto. Puede expandir y contraer diferentes bloques de código mediante el uso de la esquematización. Puede obtener más información sobre el código que utiliza mediante IntelliSense, el **Examinador de objetos**y la Jerarquía de llamadas. Puede encontrar código mediante características como **Ir a**, **Ir a definición** y **Buscar todas las referencias**. Puede insertar bloques de código con fragmentos de código y generar código mediante funciones como **Generar a partir del uso**. Si no ha usado nunca el editor de Visual Studio, vea una breve introducción en [Edición del código](https://www.visualstudio.com/features/ide-vs).  

 Puede ver el código de varias maneras. Para ver una vista de clases de la solución, abra la ventana **Vista de clases** o expanda los nodos del **Explorador de soluciones** bajo los archivos de clase.

 Puede buscar y reemplazar texto en uno o varios archivos. Para obtener más información, vea [Buscar y reemplazar texto](../ide/finding-and-replacing-text.md). Puede usar expresiones regulares para buscar y reemplazar texto. Para obtener más información, vea [Usar expresiones regulares en Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  

 Los diferentes lenguajes de Visual Studio ofrecen distintos conjuntos de características y, en algunos casos, estas se comportan de forma diferente en función del lenguaje. Muchas de estas diferencias se especifican en las descripciones de las características, pero si quiere obtener más información, puede ver las secciones sobre lenguajes específicos de Visual Studio.  

> [!IMPORTANT]
>  La edición de Visual Studio y la configuración que use pueden afectar a las características en el IDE. Podrían ser diferentes de las descritas en este tema.  

## <a name="editor-features"></a>Características del editor  

|||  
|-|-|  
|Colores de la sintaxis|Algunos elementos de la sintaxis de los archivos de código y marcado están coloreados de forma distinta para distinguirlos. Por ejemplo, las palabras clave (como `using` en C# y `Imports` en Visual Basic) son de un color, pero los tipos (como `Console` y `Uri`) son de otro. También se colorean otros elementos de la sintaxis, como los comentarios y los literales de cadena. C++ utiliza el color para diferenciar entre tipos, enumeraciones y macros, entre otros tokens.<br /><br /> Puede ver el color predeterminado para cada tipo y puede cambiar el color de cualquier elemento específico de la sintaxis en [Fuentes y colores, Entorno, Opciones (Cuadro de diálogo)](../ide/reference/fonts-and-colors-environment-options-dialog-box.md), que puede abrir desde el menú **Herramientas**.|  
|Marcas de errores y advertencias|Al agregar código y compilar su solución, puede que vea (a) que aparecen subrayados ondulados de diferentes colores o (b) bombillas en el código. Los subrayados ondulados rojos indican errores de sintaxis, los subrayados ondulados azules indican errores del compilador, los subrayados ondulados verdes indican advertencias y los subrayados ondulados púrpura, otros tipos de errores. Las [bombillas](../ide/perform-quick-actions-with-light-bulbs.md) sugieren correcciones para problemas y facilitan la aplicación de la corrección.<br /><br /> Puede ver el color predeterminado de cada subrayado ondulado de error y advertencia en el cuadro de diálogo **Herramientas/Opciones/Entorno/Fuentes y colores** . Busque **Error de sintaxis**, **Error del compilador**, **Advertencia**y **Otro Error**.|  
|Coincidencia de llaves|Cuando el punto de inserción se coloca en una llave de apertura en un archivo de código, tanto esta como la llave de cierre se resaltan. Esta característica le permite saber inmediatamente si faltan llaves o si estas están mal colocadas. Puede activar o desactivar la coincidencia de llaves mediante el ajuste **Resaltar con el delimitador automático** (**Herramientas/Opciones/Editor de texto**). Puede cambiar el color de resaltado en el ajuste **Fuentes y colores** (**Herramientas/Opciones/Entorno**). Busque **Coincidencia de llaves (resaltar)** o **Coincidencia de llaves (rectángulo)**.|  
|Visualizador de estructura|Las líneas de puntos conectan las llaves que coinciden en los archivos de código, lo que hace que sea más fácil ver los pares de llaves de apertura y cierre. Esto puede ayudarle a encontrar código en el código base más rápidamente. Puede activar o desactivar estas líneas con **Mostrar líneas guía de estructura** en la sección **Mostrar** de la página **Herramientas/Opciones/Editor de texto/General**.|
|Números de línea|Se pueden mostrar números de línea en el margen izquierdo de la ventana de código. No se muestran de forma predeterminada. Puede activar esta opción en la configuración de **Editor de texto Todos los lenguajes** (**Herramientas/Opciones/Editor de texto/Todos los lenguajes**). Puede mostrar los números de línea de los lenguajes de programación individuales cambiando la configuración de esos lenguajes (**Herramientas/Opciones/Editor de texto/\<lenguaje>**). Si desea que se impriman los números de línea, seleccione Incluir números de línea en el cuadro de diálogo **Imprimir** .|  
|Seguimiento de cambios|El color del margen izquierdo le permite realizar un seguimiento de los cambios realizados en un archivo. Los cambios que se hayan realizado pero no se hayan guardado desde que se abrió el archivo se indican mediante una barra amarilla en el margen izquierdo (conocido como el margen de selección). Una vez que haya guardado los cambios (pero antes de cerrar el archivo), la barra se volverá verde. Si deshace un cambio después de haber guardado el archivo, la barra se volverá naranja. Para activar o desactivar esta característica, cambie la opción **Seguimiento de cambios** en la configuración del **Editor de texto** (**Herramientas/Opciones/Editor de texto**).|  
|Selección de código y texto|Puede seleccionar texto en el modo de flujo continuo estándar o en el modo de cuadro, en el que selecciona una parte rectangular del texto en lugar de un conjunto de líneas. Para realizar una selección en el modo de cuadro, presione la tecla ALT mientras arrastra el mouse sobre la selección (o presione ALT + MAYÚS + \<tecla de flecha>). La selección incluye todos los caracteres dentro del rectángulo definido por el primer y el último carácter de la selección. Cualquier cosa escrita o pegada en el área seleccionada se inserta en el mismo punto en cada línea.|  
|Zoom|Puede acercar o alejar la vista en cualquier ventana de código manteniendo presionada la tecla CTRL y moviendo la rueda del mouse (o CTRL + MAYÚS + . para acercarla y CTRL + MAYÚS - , para alejarla). También puede utilizar el cuadro Zoom en la esquina inferior izquierda de la ventana de código para establecer un porcentaje de zoom específico. La característica de zoom no funciona en ventanas de herramientas.|  
|Espacio virtual|De forma predeterminada, las líneas en los editores de Visual Studio terminan después del último carácter, para que si se pulsa la tecla de flecha derecha cuando el cursor está al final de una línea, este se mueva hasta el principio de la siguiente línea. En algunos editores, las líneas no terminan después del último carácter y se puede colocar el cursor en cualquier parte de la línea. Puede habilitar el espacio virtual en el editor en la configuración **Herramientas/Opciones/Editor de texto/Todos los lenguajes** . Tenga en cuenta que puede habilitar bien **Espacio Virtual** o bien **Ajuste automático de línea**, pero no los dos.|  
|Impresión|Puede utilizar las opciones del cuadro de diálogo **Imprimir** para que al imprimir un archivo, se incluyan los números de línea o las regiones contraídas y ocultas de código. En el cuadro de diálogo **Configurar página** también puede elegir imprimir la ruta de acceso completa y el nombre del archivo seleccionando **Encabezado de página**.<br /><br /> Puede establecer las opciones de impresión de color en el cuadro de diálogo **Herramientas/Opciones/Entorno/Fuentes y colores** . Elija **Impresora** en la lista **Mostrar valores para** para personalizar la impresión en color. Puede especificar distintos colores para imprimir un archivo y para editarlo.|  
|Deshacer y Rehacer global|Los comandos **Deshacer la última acción global** y **Rehacer la última acción global** del menú **Editar** permiten deshacer o rehacer acciones globales que afectan a varios archivos. Entre las acciones globales se incluyen cambiar el nombre de una clase o espacio de nombres, realizar una operación de buscar y reemplazar en una solución, refactorizar una base de datos o cualquier otra acción que modifique varios archivos. Puede aplicar los comandos deshacer y rehacer global a acciones de la sesión actual de Visual Studio, incluso después de haber cerrado la solución en la que se aplicó una acción.|  

## <a name="advanced-editing-features"></a>Características de edición avanzadas  
 Puede encontrar un número de características avanzadas en el submenú **Editar/Avanzada** . No todas estas características están disponibles para todos los tipos de archivos de código.  

|||  
|-|-|  
|Dar formato al documento|Establece la sangría adecuada de las líneas de código y mueve las llaves para separar las líneas del documento.|  
|Dar formato a la selección|Establece la sangría adecuada de las líneas de código y mueve las llaves para separar las líneas de la selección.|  
|Aplicar tabulación a las líneas seleccionadas|Cambia los espacios iniciales por tabulaciones en los casos que sea apropiado.|  
|No aplicar tabulación a las líneas seleccionadas|Cambia las tabulaciones iniciales por espacios. Si desea convertir todos los espacios del archivo en tabulaciones (o todas las tabulaciones en espacios), puede utilizar los comyos `Edit.ConvertSpacesToTabs` y `Edit.ConvertTabsToSpaces` commys. Estos comandos no aparecen en los menús de Visual Studio, pero se pueden llamar desde la ventana Acceso rápido o la ventana Comandos.|  
|Poner en mayúsculas|Cambia todos los caracteres de la selección a mayúsculas o, si no hay ninguna selección, cambia el carácter situado en el punto de inserción a mayúsculas.|  
|Poner en minúsculas|Cambia todos los caracteres de la selección a minúsculas o, si no hay ninguna selección, cambia el carácter situado en el punto de inserción a minúsculas.|  
|Subir líneas seleccionadas|Mueve la línea seleccionada una línea hacia arriba. Método abreviado: Alt + flecha arriba.|
|Bajar líneas seleccionadas|Mueve la línea seleccionada una línea hacia abajo. Método abreviado: Alt + flecha abajo.|
|Validar documento|Valida los archivos de código JScript.|  
|Eliminar espacio en blanco horizontal|Elimina las tabulaciones o los espacios al final de la línea actual.|  
|Ver espacios en blanco|Muestra los espacios como puntos elevados y las tabulaciones como flechas. El final de un archivo se muestra como un glifo rectangular. Si está seleccionada la opción **Herramientas/Opciones/Editor de texto/Todos los lenguajes/Ajuste automático de línea/Mostrar glifos visibles para ajuste automático de línea** , también se muestra ese glifo.|  
|Ajuste automático de línea|Hace que todas las líneas de un documento se vean en la ventana de código. Puede activar o desactivar el ajuste automático de línea en la configuración Editor de texto/Todos los lenguajes (**Herramientas/Opciones/Editor de texto/Todos los lenguajes**).|  
|Selección sin comentarios|Agrega los caracteres de comentarios a la selección o la línea actual.|  
|Selección con comentarios|Quita los caracteres de comentarios de la selección o la línea actual.|  
|Aumentar sangría de línea|Agrega una tabulación (o los espacios equivalentes) a las líneas seleccionadas o la línea actual.|  
|Reducir sangría de línea|Quita una tabulación (o los espacios equivalentes) de las líneas seleccionadas o la línea actual.|  
|Seleccionar etiqueta|En un documento que contenga etiquetas (por ejemplo, XML o HTML), selecciona la etiqueta.|  
|Seleccionar contenido de la etiqueta|En un documento que contenga etiquetas (por ejemplo, XML o HTML), selecciona el contenido.|  

## <a name="navigate-and-find-code"></a>Desplazarse y buscar código  
Puede moverse por un documento de varias maneras diferentes. Además de las operaciones estándar, puede usar los botones **Navegar hacia atrás** (Ctrl + signo menos) y **Navegar hacia delante** (Ctrl + Mayús + signo menos) de la barra de herramientas para mover el punto de inserción a ubicaciones anteriores o para volver a ubicaciones más recientes en el documento activo. Estos botones retienen las últimas 20 ubicaciones del punto de inserción.

![Botones de navegación hacia adelante y atrás](../ide/media/vs2017_nav_buttons.png)

La característica de visualizador de estructura en el editor de código muestra *líneas guía de estructura*, es decir, líneas discontinuas verticales que indican las llaves coincidentes en el código base. Esto hace que sea más fácil ver dónde empiezan y acaban los bloques lógicos.

![Visualizador de estructura](../ide/media/vside_structure_visualizer.png)

Para deshabilitar las líneas guía de estructura, vaya a **Herramientas**, **Opciones**, **Editor de texto**, **General** y desactive el cuadro **Mostrar líneas guía de estructura**.

También puede utilizar la barra de desplazamiento mejorada en una ventana de código para obtener una visión global de su código. En el modo de asignación, puede obtener vistas previas del código al mover el cursor hacia arriba y hacia abajo por la barra de desplazamiento. Para obtener más información, vea [Cómo: Hacer un seguimiento del código personalizando la barra de desplazamiento](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md).  

Los siguientes comandos son métodos específicos para navegar por código :  

|||  
|-|-|  
|Buscar todas las referencias|(Menú contextual o Mayús + F12): busca todas las referencias al elemento seleccionado en la solución.|  
|Ir a|Tiene los comandos siguientes: **Ir a la línea** (Ctrl + G): moverse al número de línea especificado en el documento activo. **Ir a todo** (Ctrl + T): moverse a la línea, tipo, archivo, miembro o símbolo especificados. **Ir al archivo** (Ctrl + 1, Ctrl + F): moverse al archivo especificado en la solución. **Ir al tipo** (Ctrl + 1, Ctrl + T): moverse al tipo especificado en la solución. **Ir al miembro** (Ctrl + 1, Ctrl + M): moverse al miembro especificado en la solución. **Ir al símbolo** (Ctrl + 1, Ctrl + S): moverse al símbolo especificado en la solución. Obtenga más información sobre estos comandos en la sección "Buscar código mediante comandos Ir a" más adelante en este tema.|  
|Ir a definición|(Menú contextual o F12): busca la definición del elemento seleccionado.|  
|Ir a implementación|(Menú contextual o Ctrl + F12): busca el lugar en el código donde se implementa el elemento seleccionado.|
|Ver la definición|(Menú contextual o Alt + F12): busca la definición del elemento seleccionado y lo muestra en una ventana en el editor de código. Para obtener más información, vea [Cómo: Ver y editar código mediante Definición de Peek (Alt+F12)](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md).|  
|Método siguiente, Método anterior|(**Editar/Método siguiente, Método anterior**) En los archivos de código de Visual Basic, utilice estos comandos para mover el punto de inserción hasta otros métodos.|  
|Resaltado de referencia|Al hacer clic en un símbolo en el código fuente, se resaltan todas las instancias de ese símbolo en el documento. Los símbolos resaltados pueden incluir declaraciones y referencias, así como muchos otros símbolos que pueda devolver la función **Buscar todas las referencias** . Estos incluyen los nombres de clases, objetos, variables, métodos y propiedades. En el código de Visual Basic, también se resaltan las palabras clave de muchas estructuras de control. Para desplazarse al siguiente símbolo resaltado o al anterior, presione respectivamente CTRL + MAYÚS + flecha abajo o CTRL + MAYÚS + flecha arriba. Puede cambiar el color de resaltado en **Herramientas/Opciones/Entorno/Fuentes y colores/Referencia resaltada**.|  
|Buscar información relacionada con el código|Puede encontrar información relativa a determinado código, como los cambios realizados y quién los realizó, referencias, errores, elementos de trabajo, revisiones de código y estado de prueba unitaria cuando use CodeLens en el editor de código. CodeLens funciona como una pantalla de aviso cuando se utiliza Visual Studio Enterprise con Team Foundation Server. Vea [Buscar cambios en el código y otro historial](../ide/find-code-changes-and-other-history-with-codelens.md).|
|Ver jerarquía de llamadas|(Menú contextual o Ctrl + K, Ctrl + T).|  

 También puede usar la **barra de navegación** (los cuadros desplegables situados en la parte superior de la ventana de código) para buscar código en un código base. Puede elegir un tipo o un miembro para ir directamente a él. La barra de navegación aparece cuando se edita código en un código base de Visual Basic, C# o C++.

 ![Barra de navegación por el código](../ide/media/vside_navigation_bar.png)

 Para ocultar la barra de navegación, cambie la opción **Barra de navegación** en la configuración Todos los lenguajes del editor de texto (**Herramientas**, **Opciones**, **Editor de texto**, **Todos los lenguajes**, o bien puede cambiar la configuración de lenguajes individuales). Puede navegar por los cuadros desplegables tal como se indica a continuación:  

-   Para cambiar el foco de la ventana de código a la barra de navegación, presione la combinación de teclas de método abreviado CTRL + F2.  

-   Para devolver el foco de la barra de navegación a la ventana de código, presione la tecla ESC.  

-   Para cambiar el foco de un elemento a otro en la barra de navegación, presione la tecla TAB.  

-   Para seleccionar el elemento de la Barra de navegación que tenga el foco y volver al IDE, presione la tecla ENTRAR.  

-   Para navegar hasta una clase o tipo, seleccione su nombre en la lista desplegable izquierda.  

-   Para navegar directamente hasta un procedimiento en una clase, seleccione un procedimiento en la lista desplegable derecha.  

 En una clase parcial, los miembros definidos fuera del archivo de código actual pueden estar deshabilitados (se muestran en gris).  

## <a name="find-code-using-go-to-commands"></a>Buscar código mediante comandos Ir a
Los comandos **Ir a** de Visual Studio realiza una búsqueda centrada en su código para ayudarle a encontrar rápidamente elementos específicos en archivos de código, rutas de archivo y símbolos de código. A diferencia de otras búsquedas de texto como Buscar o Buscar en archivos, Ir a limita la búsqueda a áreas donde se encuentra el código real, como archivos, formularios y módulos de código. Por ejemplo, si busca una cadena en una aplicación web de ASP.NET con Buscar o Buscar en archivos en toda la solución, puede obtener resultados que incluyan instancias de la cadena en los comentarios de código. Pero si usa un comando Ir a, la búsqueda puede identificar la función que busca y omitir las instancias de la cadena en los comentarios de código.

### <a name="find-code-using-go-to"></a>Buscar código mediante Ir a

1. Abra una solución o carpeta en Visual Studio.
1. En el menú principal, seleccione **Editar**, **Ir a**. Aparece un pequeño cuadro de texto en la esquina superior del editor de código.
1. En el cuadro de texto, escriba el nombre del elemento de código que quiere buscar.

    ![Ventana Navegar a](../ide/media/vside_navigatetowindow.png "Ventana Navegar a")

    A medida que escribe, los resultados aparecen en una lista desplegable debajo del cuadro de texto.
1. Para ir a un elemento, púlselo en la lista.


### <a name="filter-your-search"></a>Filtrar la búsqueda

De forma predeterminada, el elemento especificado se busca en todos los elementos de la solución, pero puede limitar la búsqueda de código a tipos de elemento específicos si coloca determinados caracteres delante de los términos de búsqueda. La manera más fácil de abrir el cuadro de diálogo Ir a consiste en presionar Ctrl + T y cambiar el carácter inicial por uno de la lista siguiente. (Como alternativa, puede presionar las siguientes teclas de método abreviado para agregar automáticamente el carácter).

|Símbolo|Descripción|  
|-|-|
|Ninguna|Ningún carácter inicial. Busca el término especificado en todas las líneas, archivos, tipos, miembros y símbolos. Método abreviado: Ctrl + T|
|:|Ir al número de línea especificado. Método abreviado: Ctrl + G|
|f|Ir al nombre de archivo especificado. Método abreviado: Ctrl + 1, Ctrl + F|
|m|Ir al tipo especificado. Método abreviado: Ctrl + 1, Ctrl + T|
|m|Ir al miembro especificado. Método abreviado: Ctrl + 1, Ctrl + M|
|#|Ir al símbolo especificado. Método abreviado: Ctrl + 1, Ctrl + S|

Por ejemplo, para limitar la búsqueda a solo símbolos de código, abra el cuadro de diálogo Ir a mediante Ctrl + T (o Ctrl + ,) y, después, coloque el carácter "#" delante la consulta de Ir a. También puede seleccionar **Editar**, **Ir a**, **Ir al símbolo** en el menú. Por ejemplo, si busca `# application`, solo se muestran los símbolos de código que contienen la palabra "application".

Además, puede cambiar rápidamente el filtro de búsqueda si selecciona los botones de la barra de herramientas del cuadro de diálogo Ir a. Los botones que cambian los filtros se encuentran a la izquierda y los botones que cambian el ámbito de la búsqueda se encuentran a la derecha.

![](../ide/media/vside_navigation_toolbar.png)

Si usa la [grafía Camel](https://en.wikipedia.org/wiki/Camel_case) en el código, puede buscar elementos de código más rápido al escribir solo las letras en mayúscula del nombre del elemento de código. Por ejemplo, si el código tiene un tipo denominado `CredentialViewModel`, puede limitar la búsqueda si selecciona el filtro de tipo ("t") y escribe solo las letras mayúsculas del nombre (`CVM`) en el cuadro de diálogo Ir a.

![Ventana Navegar a: buscar con mayúsculas](../ide/media/vside_capitalsearch.png)

Esta característica es útil si el código tiene nombres largos.

## <a name="finding-references-in-your-codebase"></a>Buscar referencias en el código base
Para buscar dónde se hace referencia a elementos de código específicos en todo el código base, puede usar el comando **Buscar todas las referencias**. Para usar **Buscar todas las referencias**, seleccione el comando en el menú contextual (clic con el botón derecho) del elemento del que quiere buscar las referencias, o bien presione las teclas Mayús + F12.

Los resultados aparecen en una ventana de herramientas denominada **'*{element}*' references**, donde *{element}* es el nombre del elemento que está buscando. Una barra de herramientas de esta ventana de referencias le permite hacer lo siguiente:
- Cambiar el ámbito de la búsqueda en una lista desplegable. Puede buscar solo en los documentos modificados o en toda la solución.
- Copiar el elemento seleccionado al que se hace referencia mediante el botón **Copiar**.
- Seleccionar botones para ir a la ubicación siguiente o anterior en la lista, o presionar las teclas F8 y Mayús + F8 para hacerlo.
- Quitar los filtros en los resultados devueltos mediante el botón **Borrar todos los filtros**.
- Cambiar la forma en que se agrupan los elementos devueltos mediante una opción de la lista desplegable **Agrupar por:**.
- Conservar la ventana de los resultados de la búsqueda actual mediante el botón **Mantener resultados**.
- Buscar cadenas en los resultados de la búsqueda mediante la entrada de texto en el cuadro de texto **Búsqueda en Buscar todas las referencias**.

También puede mantener el puntero sobre cualquier resultado de la búsqueda para obtener una vista previa del elemento devuelto.

![Ventana de herramientas Buscar todas las referencias](../ide/media/vside_findallreferences.png)

Para conservar los resultados de la búsqueda, haga clic en el botón **Mantener resultados**. Al hacer clic en este botón, los resultados de la búsqueda actual permanecen en esta ventana y los resultados de la búsqueda nueva aparecen en una ventana de herramientas nueva.

### <a name="navigate-to-references"></a>Navegar a referencias
En el cuadro de diálogo Buscar todas las referencias, puede usar los métodos siguientes para navegar a referencias.

- Presione F8 para ir a la referencia siguiente, o Mayús + F8 para ir a la referencia anterior.
- Presione la tecla ENTRAR en una referencia, o haga doble clic en ella para ir a ella en el código.
- En el menú contextual de una referencia, seleccione los comandos **Ir a ubicación anterior** / **Ir a ubicación siguiente**.
- Presione las teclas de flecha arriba y abajo (si están habilitadas en el cuadro de diálogo Opciones). Para habilitar esta funcionalidad, en el menú, seleccione **Herramientas**, **Opciones**, **Entorno**, **Pestañas y ventanas**, **Pestaña de vista previa** y, después, active las casillas **Permitir que se abran nuevos archivos en la pestaña de vista previa** y **Vista previa de archivos seleccionados en Resultados de búsqueda**.

### <a name="change-reference-groupings"></a>Cambiar las agrupaciones de referencia
De forma predeterminada, las referencias se agrupan por proyecto y, luego, por definición. Aun así, puede cambiar este orden de agrupación si cambia el valor de configuración de la lista desplegable **Agrupar por:** en la barra de herramientas. Por ejemplo, puede cambiarlo del valor predeterminado **Definición y luego Proyecto** a **Proyecto y luego Definición** o a otros valores.

**Definición** y **Proyecto** son las dos agrupaciones predeterminadas que se usan, pero puede agregar otras mediante el comando **Agrupación** en el menú contextual del elemento seleccionado. Puede ser útil agregar más agrupaciones si su solución tiene una gran cantidad de archivos y rutas de acceso.

## <a name="customize-the-editor"></a>Personalizar el editor  
Puede compartir su configuración de Visual Studio con otro desarrollador, hacer que su configuración cumpla con un estándar o volver a la configuración predeterminada de Visual Studio mediante el comando **Asistente para importar y exportar configuraciones** en el menú **Herramientas**. En el **Asistente para importar y exportar configuraciones**, puede cambiar la configuración general o el lenguaje seleccionados y la configuración específica del proyecto.

Para definir teclas de acceso rápido nuevas o redefinir las existentes, vaya a **Herramientas**, **Opciones**, **Entorno**, **Teclado**. Para obtener más información sobre las teclas de acceso rápido, vea [Métodos abreviados de teclado predeterminados](../ide/default-keyboard-shortcuts-in-visual-studio.md).  

Para más información sobre cómo personalizar el editor, vea [Personalizar el editor](../ide/customizing-the-editor.md). Para obtener información sobre las opciones del editor específicas del lenguaje, vea [Usar el entorno de desarrollo de Visual C#](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md) y [Opciones, editor de texto, JavaScript, formato](../ide/reference/options-text-editor-javascript-formatting.md).

## <a name="see-also"></a>Vea también  
 [IDE de Visual Studio](../ide/visual-studio-ide.md)

