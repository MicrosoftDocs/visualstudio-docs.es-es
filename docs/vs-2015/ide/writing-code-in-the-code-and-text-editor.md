---
title: Escribir código en el editor de código y texto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
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
- code editor, navigate to
- code editor, comparing files
- code editor, zoom
- code editor
- code files
- go to line
- tabify
- zoom
- navigate to
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
caps.latest.revision: 46
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aa647d8a8d52588481d18347cb3400141978bd20
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548036"
---
# <a name="writing-code-in-the-code-and-text-editor"></a>Escribir código en el editor de código y texto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
El editor de Visual Studio proporciona muchas características que le facilitan la escritura y administración del código. Puede expandir y contraer diferentes bloques de código mediante el uso de la esquematización. Puede obtener más información sobre el código que utiliza mediante IntelliSense, el **Examinador de objetos**y la Jerarquía de llamadas. Puede navegar dentro de su código mediante características como **Navegar a**, **Ir a definición**y **Buscar todas las referencias**. Puede insertar bloques de código con fragmentos de código y generar código mediante funciones como **Generar a partir del uso**. Si no ha usado nunca el editor de Visual Studio 2015, vea [Editar código](https://www.visualstudio.com/features/ide-vs) , donde podrá ver una breve introducción.

 Puede ver el código de varias maneras. Para ver una vista de clases de la solución, puede abrir la ventana **Vista de clases** o expandir los nodos del **Explorador de soluciones** bajo los archivos de clase.

 Puede buscar y reemplazar texto en uno o varios archivos. Para obtener más información, vea [Buscar y reemplazar texto](../ide/finding-and-replacing-text.md). Si utiliza expresiones regulares, tenga en cuenta que ahora Buscar y reemplazar admite expresiones regulares de .NET. Para obtener más información, vea [Usar expresiones regulares en Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

 Los diferentes lenguajes de Visual Studio ofrecen distintos conjuntos de características y, en algunos casos, estas se comportan de forma diferente en función del lenguaje. Muchas de estas diferencias se especifican en las descripciones de las características, pero si quiere obtener más información, puede ver las secciones sobre lenguajes específicos de Visual Studio.

> [!IMPORTANT]
> La edición de Visual Studio y la configuración que use pueden afectar a las características en el IDE. Podrían ser diferentes de las descritas en este tema.

## <a name="editor-features"></a>Características del editor

|Característica|Descripción|
|-|-|
|Colores de la sintaxis|Algunos elementos de la sintaxis de los archivos de código y marcado están coloreados de forma distinta para distinguirlos. Por ejemplo, las palabras clave (como `using` en C# y `Imports` en Visual Basic) son de un color, pero los tipos (como `Console` y `Uri`) son de otro. También se colorean otros elementos de la sintaxis, como los comentarios y los literales de cadena. C++ utiliza el color para diferenciar entre tipos, enumeraciones y macros, entre otros tokens.<br /><br /> Puede ver el color predeterminado para cada tipo y puede cambiar el color de cualquier elemento específico de la sintaxis en [Fonts and Colors, Environment, Options Dialog Box](../ide/reference/fonts-and-colors-environment-options-dialog-box.md), que puede abrir desde el menú **Herramientas** .|
|Marcas de errores y advertencias|Al agregar código y compilar su solución, puede que vea (a) que aparecen subrayados ondulados de diferentes colores o (b) bombillas en el código. Los subrayados ondulados rojos indican errores de sintaxis, los subrayados ondulados azules indican errores del compilador, los subrayados ondulados verdes indican advertencias y los subrayados ondulados púrpura, otros tipos de errores. Las[bombillas](../ide/perform-quick-actions-with-light-bulbs.md) sugieren correcciones para problemas y facilitan la aplicación de la corrección.<br /><br /> Puede ver el color predeterminado de cada subrayado ondulado de error y advertencia en el cuadro de diálogo **herramientas/opciones/entorno/fuentes y colores** . Busque **Error de sintaxis**, **Error del compilador**, **Advertencia**y **Otro Error**.|
|Coincidencia de llaves|Cuando el punto de inserción se coloca en una llave de apertura en un archivo de código, tanto esta como la llave de cierre se resaltan. Esta característica le permite saber inmediatamente si faltan llaves o si estas están mal colocadas. Puede activar o desactivar la coincidencia de llaves con el valor **resaltado de delimitador automático** (**herramientas/opciones/editor de texto**). Puede cambiar el color de resaltado en la opción **fuentes y colores** (**herramientas/opciones/entorno**). Busque **Coincidencia de llaves (resaltar)** o **Coincidencia de llaves (rectángulo)**.|
|Números de línea|Se pueden mostrar números de línea en el margen izquierdo de la ventana de código. No se muestran de forma predeterminada. Puede activar esta opción en la configuración de **Editor de texto todos los lenguajes** (**herramientas/opciones/editor de texto/todos los lenguajes**). Puede mostrar los números de línea de los lenguajes de programación individuales cambiando la configuración de esos lenguajes (**herramientas/opciones \<language> /Editor de texto/**). Si desea que se impriman los números de línea, seleccione Incluir números de línea en el cuadro de diálogo **Imprimir** .|
|Seguimiento de cambios|El color del margen izquierdo le permite realizar un seguimiento de los cambios realizados en un archivo. Los cambios que se hayan realizado pero no se hayan guardado desde que se abrió el archivo se indican mediante una barra amarilla en el margen izquierdo (conocido como el margen de selección). Una vez que haya guardado los cambios (pero antes de cerrar el archivo), la barra se volverá verde. Si deshace un cambio después de haber guardado el archivo, la barra se volverá naranja. Para activar y desactivar esta característica, cambie la opción **seguimiento de cambios** en la configuración del **Editor de texto** (**herramientas/opciones/editor de texto**).|
|Selección de código y texto|Puede seleccionar texto en el modo de flujo continuo estándar o en el modo de cuadro, en el que selecciona una parte rectangular del texto en lugar de un conjunto de líneas. Para hacer una selección en el modo de cuadro, presione ALT mientras arrastra el mouse sobre la selección (o presione ALT + MAYÚS + \<arrow key> ). La selección incluye todos los caracteres dentro del rectángulo definido por el primer y el último carácter de la selección. Cualquier cosa escrita o pegada en el área seleccionada se inserta en el mismo punto en cada línea.|
|Zoom|Puede acercar o alejar la vista en cualquier ventana de código manteniendo presionada la tecla CTRL y moviendo la rueda del mouse (o CTRL + MAYÚS + . para acercarla y CTRL + MAYÚS - , para alejarla). También puede utilizar el cuadro Zoom en la esquina inferior izquierda de la ventana de código para establecer un porcentaje de zoom específico. La característica de zoom no funciona en ventanas de herramientas.|
|Espacio virtual|De forma predeterminada, las líneas en los editores de Visual Studio terminan después del último carácter, para que si se pulsa la tecla de flecha derecha cuando el cursor está al final de una línea, este se mueva hasta el principio de la siguiente línea. En algunos editores, las líneas no terminan después del último carácter y se puede colocar el cursor en cualquier parte de la línea. Puede habilitar el espacio virtual en el editor en la configuración **herramientas/opciones/editor de texto/todos los lenguajes** . Tenga en cuenta que puede habilitar bien **Espacio Virtual** o bien **Ajuste automático de línea**, pero no los dos.|
|Impresión|Puede utilizar las opciones del cuadro de diálogo **Imprimir** para que al imprimir un archivo, se incluyan los números de línea o las regiones contraídas y ocultas de código. En el cuadro de diálogo **Configurar página** también puede elegir imprimir la ruta de acceso completa y el nombre del archivo seleccionando **Encabezado de página**.<br /><br /> Puede establecer las opciones de impresión de color en el cuadro de diálogo **herramientas/opciones/entorno/fuentes y colores** . Elija **Impresora** en la lista **Mostrar valores para** para personalizar la impresión en color. Puede especificar distintos colores para imprimir un archivo y para editarlo.|
|Deshacer y Rehacer global|Los comandos **Deshacer la última acción global** y **Rehacer la última acción global** del menú **Editar** permiten deshacer o rehacer acciones globales que afectan a varios archivos. Entre las acciones globales se incluyen cambiar el nombre de una clase o espacio de nombres, realizar una operación de buscar y reemplazar en una solución, refactorizar una base de datos o cualquier otra acción que modifique varios archivos. Puede aplicar los comandos deshacer y rehacer global a acciones de la sesión actual de Visual Studio, incluso después de haber cerrado la solución en la que se aplicó una acción.|

## <a name="advanced-editing-features"></a>Características de edición avanzadas
 Puede encontrar un número de características avanzadas en el submenú **Editar/Avanzada** . No todas estas características están disponibles para todos los tipos de archivos de código.

|Característica|Descripción|
|-|-|
|Dar formato al documento|Establece la sangría adecuada de las líneas de código y mueve las llaves para separar las líneas del documento.|
|Dar formato a la selección|Establece la sangría adecuada de las líneas de código y mueve las llaves para separar las líneas de la selección.|
|Aplicar tabulación a las líneas seleccionadas|Cambia los espacios iniciales por tabulaciones en los casos que sea apropiado.|
|No aplicar tabulación a las líneas seleccionadas|Cambia las tabulaciones iniciales por espacios. Si desea convertir todos los espacios del archivo en tabulaciones (o todas las tabulaciones en espacios), puede utilizar los comandos `Edit.ConvertSpacesToTabs` y `Edit.ConvertTabsToSpaces` . Estos comandos no aparecen en los menús de Visual Studio, pero se pueden llamar desde la ventana Acceso rápido o la ventana Comandos.|
|Poner en mayúsculas|Cambia todos los caracteres de la selección a mayúsculas o, si no hay ninguna selección, cambia el carácter situado en el punto de inserción a mayúsculas.|
|Poner en minúsculas|Cambia todos los caracteres de la selección a minúsculas o, si no hay ninguna selección, cambia el carácter situado en el punto de inserción a minúsculas.|
|Validar documento|Valida los archivos de código JScript.|
|Eliminar espacio en blanco horizontal|Elimina las tabulaciones o los espacios al final de la línea actual.|
|Ver espacios en blanco|Muestra los espacios como puntos elevados y las tabulaciones como flechas. El final de un archivo se muestra como un glifo rectangular. Si está seleccionada la opción **herramientas/opciones/editor de texto/todos los lenguajes/ajuste de palabras/Mostrar glifos visibles para ajuste automático de** la pantalla, también se muestra ese glifo.|
|Ajuste automático de línea|Hace que todas las líneas de un documento se vean en la ventana de código. Puede activar o desactivar el ajuste automático de línea en la configuración Editor de texto/Todos los lenguajes (**Herramientas/Opciones/Editor de texto/Todos los lenguajes**).|
|Selección sin comentarios|Agrega los caracteres de comentarios a la selección o la línea actual.|
|Selección con comentarios|Quita los caracteres de comentarios de la selección o la línea actual.|
|Aumentar sangría de línea|Agrega una tabulación (o los espacios equivalentes) a las líneas seleccionadas o la línea actual.|
|Reducir sangría de línea|Quita una tabulación (o los espacios equivalentes) de las líneas seleccionadas o la línea actual.|
|Seleccionar etiqueta|En un documento que contenga etiquetas (por ejemplo, XML o HTML), selecciona la etiqueta.|
|Seleccionar contenido de la etiqueta|En un documento que contenga etiquetas (por ejemplo, XML o HTML), selecciona el contenido.|

## <a name="navigate-in-the-code-window"></a>Navegar por la ventana de código
 Puede moverse por un documento de varias maneras diferentes. Además de las operaciones estándar, puede utilizar los botones **Navegar hacia atrás** (o CTRL + signo menos) y **Navegar hacia delante** (CTRL + MAYÚS + signo menos) de la barra de herramientas para mover el punto de inserción o volver a ubicaciones más recientes en el documento activo. Estos botones retienen las últimas 20 ubicaciones del punto de inserción.

 ![Botones de navegación hacia adelante y atrás](../ide/media/vs2015-nav-buttons.png "VS2015_Nav_buttons")

 También puede utilizar la barra de desplazamiento mejorada en una ventana de código para obtener una visión global de su código. En el modo de asignación, puede obtener vistas previas del código al mover el cursor hacia arriba y hacia abajo por la barra de desplazamiento. Para obtener más información, vea [Cómo: Hacer un seguimiento del código personalizando la barra de desplazamiento](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md).

 Los siguientes comandos son métodos específicos para navegar por código :

|Comando|Descripción|
|-|-|
|Vete a\<line number>|(**Editar/Ir a** o CTRL + G): mover a un número de línea específico en el documento activo.|
|Navegar a|(**Editar/Navegar a** o CTRL +,): busca un símbolo o un archivo en la solución activa. Le ayuda a elegir un buen conjunto de resultados coincidentes de una consulta. Puede buscar palabras clave incluidas en un símbolo utilizando mayúsculas y minúsculas Camel y caracteres de subrayado para dividir dicho símbolo en palabras clave.|
|Buscar todas las referencias|(Menú contextual): busca todas las referencias al elemento seleccionado en la solución.|
|Ir a definición|(Menú contextual o F12): busca la definición del elemento seleccionado.|
|Ver la definición|(Menú contextual o Alt+F12): busca la definición del elemento seleccionado y lo muestra en una ventana emergente. Para obtener más información, vea [Cómo: ver y editar código mediante el uso de la definición de PEEK (Alt + F12)](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md).|
|Método siguiente, Método anterior|(**Editar/Método siguiente, Método anterior**) En los archivos de código de Visual Basic, utilice estos comandos para mover el punto de inserción hasta otros métodos.|
|Resaltado de referencia|Al hacer clic en un símbolo en el código fuente, se resaltan todas las instancias de ese símbolo en el documento. Los símbolos resaltados pueden incluir declaraciones y referencias, así como muchos otros símbolos que pueda devolver la función **Buscar todas las referencias** . Estos incluyen los nombres de clases, objetos, variables, métodos y propiedades. En el código de Visual Basic, también se resaltan las palabras clave de muchas estructuras de control. Para desplazarse al siguiente símbolo resaltado o al anterior, presione respectivamente CTRL + MAYÚS + flecha abajo o CTRL + MAYÚS + flecha arriba. Puede cambiar el color de resaltado en **herramientas/opciones/entorno/fuentes y colores/referencia resaltada.**|
|Buscar información relacionada con el código|Puede encontrar información relativa a determinado código, como los cambios realizados y quién los realizó, referencias, errores, elementos de trabajo, revisiones de código y estado de prueba unitaria cuando use CodeLens en el editor de código. CodeLens funciona como una pantalla de aviso cuando se utiliza Visual Studio Enterprise con Team Foundation Server. Vea [Buscar cambios en el código y otro historial](../ide/find-code-changes-and-other-history-with-codelens.md).|

 También puede utilizar la **barra de navegación**, es decir, los dos cuadros desplegables que aparecen en la parte superior de la ventana de código, para navegar por un archivo de código. Esta barra le permite ir directamente hasta un tipo determinado o hasta uno de los miembros dentro de un tipo. La barra de navegación aparece con los archivos de código de Visual Basic, C# y C++.

 Para ocultar la barra de navegación, cambie la opción **Barra de navegación** en la configuración de Editor de texto/Todos los lenguajes (**Herramientas/Opciones/Editor de texto/Todos los lenguajes**, o puede cambiar la configuración de lenguajes individuales). Puede navegar por los cuadros desplegables tal como se indica a continuación:

- Para cambiar el foco de la ventana de código a la barra de navegación, presione la combinación de teclas de método abreviado CTRL + F2.

- Para devolver el foco de la barra de navegación a la ventana de código, presione la tecla ESC.

- Para cambiar el foco de un elemento a otro en la barra de navegación, presione la tecla TAB.

- Para seleccionar el elemento de la Barra de navegación que tenga el foco y volver al IDE, presione la tecla ENTRAR.

- Para navegar hasta una clase o tipo, haga clic en su nombre en la lista desplegable izquierda.

- Para navegar directamente hasta un procedimiento en una clase, haga clic en un procedimiento en la lista desplegable derecha.

  En una clase parcial, los miembros definidos fuera del archivo de código actual pueden mostrarse en gris.

## <a name="find-code-using-navigate-to"></a>Buscar código con Navegar a
El comando "Navegar a" de Visual Studio realiza una búsqueda centrada en el código para ayudarle a encontrar rápidamente elementos específicos en archivos de código, rutas de archivo y símbolos de código. A diferencia de otras búsquedas de texto como Buscar o Buscar en archivos, Navegar a limita la búsqueda a áreas donde se encuentra el código real, como archivos, formularios y módulos de código. Por ejemplo, si busca una cadena en una aplicación web de ASP.NET con Buscar o Buscar en archivos en toda la solución, puede obtener varios resultados, incluidas instancias de la cadena en los comentarios de código. Sin embargo, al usar navegar a, es posible que solo obtenga una función única, omitiendo las instancias de la cadena en los comentarios de código.

### <a name="navigate-code-using-navigate-to"></a>Navegar por el código con Navegar a

1. Abra una solución o carpeta en Visual Studio.
1. En el menú principal, pulse **Editar**, **Navegar a** o presione **CTRL + ,**.

    Aparece un pequeño cuadro de texto en la esquina superior del editor de código.
1. En el cuadro de texto, escriba el nombre del elemento de código que quiere buscar.

    ![Ventana Navegar a](../ide/media/vside-navigatetowindow.png "Ventana Navegar a")

    A medida que escribe, los resultados aparecen en una lista desplegable debajo del cuadro de texto.
1. Para ir a un elemento, púlselo en la lista.

### <a name="filter-your-search"></a>Filtrar la búsqueda

Para limitar la búsqueda solo a los símbolos de código, anteponga a la consulta Navigate con un \@ carácter "". Por ejemplo, si busca `@application`, Navegar a muestra, por ejemplo, solo clases que tengan la palabra "aplicación" en ellas.

Si usa intercalación de mayúsculas y minúsculas en el código, puede buscar elementos de código más rápido al escribir solo las letras en mayúscula del nombre del elemento de código. Por ejemplo, si su código tiene un componente denominado `ViewSwitcher`, puede buscarlo escribiendo solo las letras mayúsculas del nombre (`"VS"`) en la ventana Navegar a.

![Ventana Navegar a: buscar con mayúsculas](../ide/media/vside-capitalsearch.png "Ventana Navegar a: buscar con mayúsculas")

Esta característica es especialmente útil si el código tiene nombres largos.

## <a name="customize-the-editor"></a>Personalizar el editor
 **Importar y exportar configuraciones**: puede compartir las configuraciones con otro desarrollador, hacer que sus configuraciones cumplan con un estándar o volver a la configuración predeterminada de Visual Studio usando el **Asistente para importar y exportar configuraciones** en el menú **Herramientas** . Puede cambiar la configuración general o la configuración específica del proyecto y el lenguaje.

 **Asignación de teclado**: puede definir nuevas teclas de acceso rápido o volver a definir las existentes en la configuración Herramientas/Opciones/Entorno/Teclado. Para obtener más información sobre las teclas de acceso rápido, vea [Métodos abreviados de teclado predeterminados](../ide/default-keyboard-shortcuts-in-visual-studio.md).

 Para obtener información acerca de las opciones del editor específicas de los lenguajes, consulte:

- [Configuración de Visual Basic](https://msdn.microsoft.com/library/2712b3b1-18f2-430c-ae91-28468bbf5f32)

- [Uso del entorno de desarrollo de Visual Studio para C#](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)

- [Options, Text Editor, JavaScript, Formatting](../ide/reference/options-text-editor-javascript-formatting.md)

## <a name="in-this-section"></a>En esta sección

- [Buscar y reemplazar texto](../ide/finding-and-replacing-text.md)

- [Codificaciones y saltos de línea](../ide/encodings-and-line-breaks.md)

- [esquematizar](../ide/outlining.md)

- [Refactorización](../ide/refactoring-in-visual-studio.md)

- [Sugerencias de productividad](../ide/productivity-tips-for-visual-studio.md)

- [Usar IntelliSense](../ide/using-intellisense.md)

- [Personalizar el editor](../ide/customizing-the-editor.md)

- [Cómo: Hacer un seguimiento del código personalizando la barra de desplazamiento](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md)

- [Cómo: ver y editar código mediante la definición de PEEK (Alt + F12)](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)

- [Realizar acciones rápidas con las bombillas](../ide/perform-quick-actions-with-light-bulbs.md)

- [Fragmentos de código](../ide/code-snippets.md)

- [Usar el cuadro de herramientas](../ide/using-the-toolbox.md)

- [Ver la estructura del código](../ide/viewing-the-structure-of-code.md)

- [Establecer marcadores en el código](../ide/setting-bookmarks-in-code.md)

- [Usar la Lista de tareas](../ide/using-the-task-list.md)

- [Buscar cambios en el código y otro historial](../ide/find-code-changes-and-other-history-with-codelens.md)

## <a name="see-also"></a>Consulte también
 [IDE de Visual Studio](../ide/visual-studio-ide.md)
