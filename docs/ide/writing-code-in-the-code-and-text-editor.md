---
title: Características del editor de código
ms.date: 02/23/2018
ms.topic: conceptual
helpviewer_keywords:
- code, editing [Visual Studio]
- code editor [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7dbb14a7ea6b3271c7608f3bbb49dd30aa605b66
ms.sourcegitcommit: e82baa50bf5a65858c410882c2e86a552c2c1921
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2019
ms.locfileid: "72380975"
---
# <a name="features-of-the-code-editor"></a>Características del editor de código

El editor de Visual Studio proporciona muchas características que le facilitan la escritura y la administración del código y del texto. Puede expandir y contraer diferentes bloques de código mediante el uso de la esquematización. Puede obtener más información sobre el código mediante IntelliSense, el **Examinador de objetos** y la jerarquía de llamadas. Puede encontrar código mediante características como **Ir a**, **Ir a definición** y **Buscar todas las referencias**. Puede insertar bloques de código con fragmentos de código y generar código mediante funciones como **Generar a partir del uso**. Si no ha usado nunca el editor de Visual Studio, vea [Aprender a usar el editor de código](../get-started/tutorial-editor.md).

> [!NOTE]
> Este tema se aplica a Visual Studio para Windows. En el caso de Visual Studio para Mac, vea [Editor de código fuente (Visual Studio para Mac)](/visualstudio/mac/source-editor).

Puede ver el código de varias maneras. De forma predeterminada, en el **Explorador de soluciones** se muestra el código organizado por archivos. Puede hacer clic en la pestaña **Vista de clases** en la parte inferior de la ventana para ver el código organizado por clases.

Puede buscar y reemplazar texto en uno o varios archivos. Para obtener más información, vea [Buscar y reemplazar texto](../ide/finding-and-replacing-text.md). Puede usar expresiones regulares para buscar y reemplazar texto. Para obtener más información, vea [Usar expresiones regulares en Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

Los diferentes lenguajes de Visual Studio ofrecen distintos conjuntos de características y, en algunos casos, estas se comportan de forma diferente en función del lenguaje. Muchas de estas diferencias se especifican en las descripciones de las características, pero si quiere obtener más información, puede ver las secciones sobre lenguajes específicos de Visual Studio.

## <a name="editor-features"></a>Características del editor

|||
|-|-|
|Colores de la sintaxis|Algunos elementos de la sintaxis de los archivos de código y marcado están coloreados de forma distinta para distinguirlos. Por ejemplo, las palabras clave (como `using` en C# y `Imports` en Visual Basic) son de un color, pero los tipos (como `Console` y `Uri`) son de otro. También se colorean otros elementos de la sintaxis, como los comentarios y los literales de cadena. C++ utiliza el color para diferenciar entre tipos, enumeraciones y macros, entre otros tokens.<br /><br /> Puede ver el color predeterminado para cada tipo y puede cambiar el color de cualquier elemento específico de la sintaxis en [Fonts and Colors, Environment, Options Dialog Box](../ide/reference/fonts-and-colors-environment-options-dialog-box.md), que puede abrir desde el menú **Herramientas**.|
|Marcas de errores y advertencias|Al agregar código y compilar su solución, puede que vea (a) que aparecen subrayados ondulados de diferentes colores o (b) bombillas en el código. Los subrayados ondulados rojos indican errores de sintaxis, los subrayados ondulados azules indican errores del compilador, los subrayados ondulados verdes indican advertencias y los subrayados ondulados púrpura, otros tipos de errores. Las [acciones rápidas](../ide/quick-actions.md) sugieren correcciones para problemas y facilitan la aplicación de la corrección.<br /><br /> Puede ver el color predeterminado de cada subrayado ondulado de error y advertencia en el cuadro de diálogo **Herramientas** > **Opciones** > **Entorno** > **Fuentes y colores**. Busque **Error de sintaxis**, **Error del compilador**, **Advertencia**y **Otro Error**.|
|Coincidencia de llaves|Cuando el punto de inserción se coloca en una llave de apertura en un archivo de código, tanto esta como la llave de cierre se resaltan. Esta característica le permite saber inmediatamente si faltan llaves o si estas están mal colocadas. Puede activar o desactivar la coincidencia de llaves mediante la configuración **Resaltar con el delimitador automático** (**Herramientas** > **Opciones** > **Editor de texto**). Puede cambiar el color de resaltado en la configuración **Fuentes y colores** (**Herramientas** > **Opciones** > **Entorno**). Busque **Coincidencia de llaves (resaltar)** o **Coincidencia de llaves (rectángulo)** .|
|Visualizador de estructura|Las líneas de puntos conectan las llaves que coinciden en los archivos de código, lo que hace que sea más fácil ver los pares de llaves de apertura y cierre. Esto puede ayudarle a encontrar código en el código base más rápidamente. Puede activar o desactivar estas líneas con **Mostrar líneas guía de estructura** en la sección **Mostrar** de la página **Herramientas** > **Opciones** > **Editor de texto** > **General**.|
|Números de línea|Se pueden mostrar números de línea en el margen izquierdo de la ventana de código. No se muestran de forma predeterminada. Puede activar esta opción en la configuración de **Editor de texto Todos los lenguajes** (**Herramientas** > **Opciones** > **Editor de texto** > **Todos los lenguajes**). Puede mostrar los números de línea de los lenguajes de programación individuales cambiando la configuración de esos lenguajes (**Herramientas** > **Opciones** > **Editor de texto** >  **\<lenguaje>** ). Si quiere que se impriman los números de línea, seleccione **Incluir números de línea** en el cuadro de diálogo **Imprimir**.|
|Seguimiento de cambios|El color del margen izquierdo le permite realizar un seguimiento de los cambios realizados en un archivo. Los cambios que se hayan realizado pero no se hayan guardado desde que se abrió el archivo se indican mediante una barra amarilla en el margen izquierdo (conocido como el margen de selección). Una vez que haya guardado los cambios (pero antes de cerrar el archivo), la barra se volverá verde. Si deshace un cambio después de haber guardado el archivo, la barra se volverá naranja. Para activar o desactivar esta característica, cambie la opción **Seguimiento de cambios** en la configuración del **Editor de texto** (**Herramientas** > **Opciones** > **Editor de texto**).|
|Selección de código y texto|Puede seleccionar texto en el modo de flujo continuo estándar o en el modo de cuadro, en el que selecciona una parte rectangular del texto en lugar de un conjunto de líneas. Para realizar una selección en el modo de cuadro, presione la tecla **ALT** mientras arrastra el mouse sobre la selección (o presione **ALT**+**MAYÚS**+ **\<tecla de flecha>** ). La selección incluye todos los caracteres dentro del rectángulo definido por el primer y el último carácter de la selección. Cualquier cosa escrita o pegada en el área seleccionada se inserta en el mismo punto en cada línea.|
|Zoom|Puede acercar o alejar la vista en cualquier ventana de código manteniendo presionada la tecla **CTRL** y moviendo la rueda del mouse (o **CTRL**+**MAYÚS**+ **.** para acercarla y **CTRL**+**MAYÚS**+ **,** para alejarla). También puede utilizar el cuadro **Zoom** en la esquina inferior izquierda de la ventana de código para establecer un porcentaje de zoom específico. La característica de zoom no funciona en ventanas de herramientas.|
|Espacio virtual|De forma predeterminada, las líneas en los editores de Visual Studio terminan después del último carácter, para que si se pulsa la tecla de **flecha derecha** cuando el cursor está al final de una línea, este se mueva hasta el principio de la siguiente línea. En algunos editores, las líneas no terminan después del último carácter y se puede colocar el cursor en cualquier parte de la línea. Puede habilitar el espacio virtual en el editor en la configuración **Herramientas** > **Opciones** > **Editor de texto** > **Todos los lenguajes**. Tenga en cuenta que puede habilitar bien **Espacio Virtual** o bien **Ajuste automático de línea**, pero no los dos.|
|Impresión|Puede utilizar las opciones del cuadro de diálogo **Imprimir** para que al imprimir un archivo, se incluyan los números de línea o las regiones contraídas y ocultas de código. En el cuadro de diálogo **Configurar página** también puede elegir imprimir la ruta de acceso completa y el nombre del archivo seleccionando **Encabezado de página**.<br /><br /> Puede establecer las opciones de impresión de color en el cuadro de diálogo **Herramientas** > **Opciones** > **Entorno** > **Fuentes y colores**. Elija **Impresora** en la lista **Mostrar valores para** para personalizar la impresión en color. Puede especificar distintos colores para imprimir un archivo y para editarlo.|
|Deshacer y Rehacer global|Los comandos **Deshacer la última acción global** y **Rehacer la última acción global** del menú **Editar** permiten deshacer o rehacer acciones globales que afectan a varios archivos. Entre las acciones globales se incluyen cambiar el nombre de una clase o espacio de nombres, realizar una operación de buscar y reemplazar en una solución, refactorizar una base de datos o cualquier otra acción que modifique varios archivos. Puede aplicar los comandos deshacer y rehacer global a acciones de la sesión actual de Visual Studio, incluso después de haber cerrado la solución en la que se aplicó una acción.|

## <a name="advanced-editing-features"></a>Características de edición avanzadas

Puede encontrar un número de características avanzadas en el menú **Editar** > **Avanzada** en la barra de herramientas. No todas estas características están disponibles para todos los tipos de archivos de código.

|||
|-|-|
|Dar formato al documento|Establece la sangría adecuada de las líneas de código y mueve las llaves para separar las líneas del documento.|
|Dar formato a la selección|Establece la sangría adecuada de las líneas de código y mueve las llaves para separar las líneas de la selección.|
|Aplicar tabulación a las líneas seleccionadas|Cambia los espacios iniciales por tabulaciones en los casos que sea apropiado.|
|No aplicar tabulación a las líneas seleccionadas|Cambia las tabulaciones iniciales por espacios. Si desea convertir todos los espacios del archivo en tabulaciones (o todas las tabulaciones en espacios), puede utilizar los comandos `Edit.ConvertSpacesToTabs` y `Edit.ConvertTabsToSpaces` . Estos comandos no aparecen en los menús de Visual Studio, pero se pueden llamar desde la ventana **Acceso rápido** o la ventana Comandos.|
|Poner en mayúsculas|Cambia todos los caracteres de la selección a mayúsculas o, si no hay ninguna selección, cambia el carácter situado en el punto de inserción a mayúsculas. Método abreviado: **Ctrl**+**Mayús**+**U**.|
|Poner en minúsculas|Cambia todos los caracteres de la selección a minúsculas o, si no hay ninguna selección, cambia el carácter situado en el punto de inserción a minúsculas. Método abreviado: **Ctrl**+**U**.|
|Subir líneas seleccionadas|Mueve la línea seleccionada una línea hacia arriba. Método abreviado: **Alt**+**Flecha arriba**.|
|Bajar líneas seleccionadas|Mueve la línea seleccionada una línea hacia abajo. Método abreviado: **Alt**+**Flecha abajo**.|
|Eliminar espacio en blanco horizontal|Elimina las tabulaciones o los espacios al final de la línea actual. Método abreviado: **Ctrl**+**K**, **Ctrl**+ **\\**|
|Ver espacios en blanco|Muestra los espacios como puntos elevados y las tabulaciones como flechas. El final de un archivo se muestra como un glifo rectangular. Si está seleccionada la opción **Herramientas** > **Opciones** > **Editor de texto** > **Todos los lenguajes** > **Ajuste automático de línea** > **Mostrar glifos visibles para ajuste automático de línea**, también se muestra ese glifo.|
|Ajuste automático de línea|Hace que todas las líneas de un documento se vean en la ventana de código. Puede activar o desactivar el ajuste automático de línea en la configuración **Editor de texto/Todos los lenguajes** (**Herramientas** > **Opciones** > **Editor de texto** > **Todos los lenguajes**).|
|Selección con comentarios|Agrega los caracteres de comentarios a la selección o la línea actual. Método abreviado: **Ctrl**+**K**, **Ctrl**+**C**|
|Selección sin comentarios|Quita los caracteres de comentarios de la selección o la línea actual. Método abreviado: **Ctrl**+**K**, **Ctrl**+**U**|
|Aumentar sangría de línea|Agrega una tabulación (o los espacios equivalentes) a las líneas seleccionadas o la línea actual.|
|Reducir sangría de línea|Quita una tabulación (o los espacios equivalentes) de las líneas seleccionadas o la línea actual.|
|Seleccionar etiqueta|En un documento que contenga etiquetas (por ejemplo, XML o HTML), selecciona la etiqueta.|
|Seleccionar contenido de la etiqueta|En un documento que contenga etiquetas (por ejemplo, XML o HTML), selecciona el contenido.|

## <a name="navigate-and-find-code"></a>Desplazarse y buscar código

Puede moverse por el editor de código de varias maneras. Por ejemplo, puede navegar hacia atrás y hacia delante a puntos de inserción anteriores, ver la definición de un tipo o miembro y saltar a un método específico mediante la barra de navegación. Para obtener más información, vea [navegar por el código](navigating-code.md).

## <a name="find-references-in-your-code-base"></a>Búsqueda de referencias en el código base

Para buscar dónde se hace referencia a elementos de código específicos en todo el código base, puede usar el comando **Buscar todas las referencias** o presionar **Mayús**+**F12**. Además, al hacer clic en un tipo o miembro, la característica de **resaltado de referencia** resalta automáticamente todas las referencias a ese tipo o miembro. Para obtener más información, vea [Búsqueda de referencias en el código](finding-references.md).

## <a name="customize-the-editor"></a>Personalización del editor

Puede compartir su configuración de Visual Studio con otro desarrollador, hacer que su configuración cumpla con un estándar o volver a la configuración predeterminada de Visual Studio mediante el comando **Asistente para importar y exportar configuraciones** en el menú **Herramientas**. En el **Asistente para importar y exportar configuraciones**, puede cambiar la configuración general o el lenguaje seleccionados y la configuración específica del proyecto.

Para definir teclas de acceso rápido nuevas o redefinir las existentes, vaya a **Herramientas** > **Opciones** > **Entorno** > **Teclado**. Para más información sobre las teclas de acceso rápido, consulte [Métodos abreviados de teclado predeterminados](../ide/default-keyboard-shortcuts-in-visual-studio.md).

Para las opciones del editor específicas de JavaScript, consulte las [opciones del editor de JavaScript](../ide/reference/options-text-editor-javascript-formatting.md).

## <a name="see-also"></a>Vea también

- [Editor de código fuente (Visual Studio para Mac)](/visualstudio/mac/source-editor)
- [IDE de Visual Studio](../get-started/visual-studio-ide.md)
- [Introducción a C++ en Visual Studio](/cpp/get-started/tutorial-console-cpp)
- [Introducción a C# y ASP.NET Core en Visual Studio](../get-started/csharp/tutorial-aspnet-core.md)
- [Introducción a Python en Visual Studio](../ide/quickstart-python.md)
