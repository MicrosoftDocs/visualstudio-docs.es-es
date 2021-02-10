---
title: Fuentes y colores, Entorno, Opciones (Cuadro de diálogo)
description: Obtenga información sobre cómo usar la página Fuentes y colores de la sección Entorno para establecer una combinación personalizada de colores y fuentes para varios elementos de la interfaz de usuario del IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.FontsAndColors
- VS.ToolsOptionsPages.Environment.Fonts_And_Colors
- VS.Environment.Fonts And Colors
helpviewer_keywords:
- colors, customizing IDE
- Query and View Designer, customizing
- fonts, editors
- menus, customizing
- Table Designer, customizing
- Database Designer, customizing environment
- default colors
- accessibility, options
- editors, customizing
- designers, customizing environment
- defaults, colors
- printers, customizing
ms.assetid: c767d302-51ed-47a8-a527-c07bce2aa485
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ccc2309cf3ccc51c82796816f635908b55b81901
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969755"
---
# <a name="fonts-and-colors-environment-options-dialog-box"></a>Fuentes y colores, Entorno, Opciones (Cuadro de diálogo)

La página **Fuentes y colores** del cuadro de diálogo **Opciones** le permite establecer una combinación de colores y una fuente personalizadas para varios elementos de la interfaz de usuario del entorno de desarrollo integrado (IDE). Para acceder a este cuadro de diálogo, haga clic en **Herramientas** > **Opciones** y seleccione **Entorno** > **Fuentes y colores**.

Los cambios de combinaciones de colores no surten efecto durante la sesión en la que se realizan. Puede evaluar los cambios de color abriendo otra instancia de Visual Studio y creando las condiciones en las que espera aplicar los cambios.

**Mostrar valores para**

Enumera todos los elementos de la interfaz de usuario para los que puede cambiar las combinaciones de fuentes y colores. Después de seleccionar un elemento de esta lista, puede personalizar la configuración de color para el elemento seleccionado en **Elementos para mostrar**.

- **Editor de texto**

     Los cambios realizados en la configuración de visualización de estilo, tamaño y color para el Editor de texto afectan a la apariencia del texto en el editor de texto predeterminado. Esta configuración no afectará a los documentos abiertos en un editor de texto fuera del IDE

- **Impresora**

     Los cambios realizados en la configuración de visualización de estilo, tamaño y color para la Impresora afectan a la apariencia del texto en documentos impresos.

    > [!NOTE]
    > Según sea necesario, puede seleccionar una fuente predeterminada para imprimir distinta a la que se usa para mostrar en el editor de texto. Esto puede ser útil cuando imprima código que contiene caracteres tanto de un solo byte como de doble byte.

- **Finalización de instrucciones**

     Cambia el estilo de fuente y el tamaño del texto que aparece en los elementos emergentes de finalización de instrucciones del editor.

- **Información sobre herramientas del editor**

     Cambia el estilo de fuente y el tamaño del texto que aparece en Información sobre herramientas que se muestra en el editor.

- **Fuente del entorno**

     Cambia el estilo y el tamaño de la fuente de todos los elementos de la interfaz de usuario del IDE que aún no tienen una opción independiente en **Mostrar valores para**.

     ::: moniker range="vs-2017"

     Por ejemplo, esta opción se aplica a la **Página de inicio** pero no afecta a la ventana de **salida**.

     ::: moniker-end

- **[Todas las ventanas de herramientas de texto]**

     Los cambios realizados en la configuración de visualización de estilo, tamaño y color para este elemento afectan a la apariencia del texto en ventanas de herramientas que tengan paneles de resultados en el IDE. Por ejemplo, la ventana de salida, la ventana de comandos, la ventana inmediata, etc.

    > [!NOTE]
    > Los cambios realizados en el texto de elementos **[Todas las ventanas de herramientas de texto]** no surten efecto durante la sesión en la que se realizan. Puede evaluar dichos cambios abriendo otra instancia de Visual Studio.

**Usar valores predeterminados**

Restablece los valores de fuente y color del elemento de lista seleccionado en **Mostrar valores para**. El botón **Uso** aparece cuando hay otras combinaciones de visualización disponibles para seleccionarlas. Por ejemplo, puede elegir entre dos combinaciones para la impresora.

**Fuente (los tipos en negrita indican fuentes con ancho fijo)**

Enumera todas las fuentes instaladas en el sistema. Cuando el menú desplegable aparece por primera vez, la fuente actual del elemento seleccionado en el campo **Mostrar valores para** está resaltada. Las fuentes fijas, que son más fáciles de alinear en el editor, aparecen en negrita.

**Size**

Enumera los tamaños de puntos disponibles para la fuente resaltada. Cambiar el tamaño de la fuente afecta a todos los **Elementos para mostrar** de la selección **Mostrar valores para**.

**Elementos para mostrar**

Enumera los elementos de los que puede modificar el color de primer plano y de fondo.

> [!NOTE]
> **Texto sin formato** es el elemento para mostrar predeterminado. Como tal, las propiedades asignadas a **Texto sin formato** serán reemplazadas por las propiedades asignadas a otros elementos para mostrar. Por ejemplo, si asigna el color azul al **Texto sin formato** y el color verde al **Identificador**, todos los identificadores aparecerán en verde. En este ejemplo, las propiedades del **Identificador** reemplazan las propiedades del **Texto sin formato**.

Entre los elementos para mostrar se incluyen:

|Elemento para mostrar|Description|
|------------------|-----------------|
|**Texto sin formato**|Texto del editor.|
|**Texto seleccionado**|Texto que se incluye en la selección actual cuando el editor tiene el foco.|
|**Texto seleccionado inactivo**|Texto que se incluye en la selección actual cuando el editor ha perdido el foco.|
|**Margen del indicador**|El margen situado a la izquierda del Editor de código donde se muestran los iconos de los puntos de interrupción y de marcador.|
|**Números de línea**|Números opcionales que aparecen junto a cada línea de código|
|**Espacio en blanco visible**|Espacios, tabulaciones e indicadores de ajuste automático de línea|
|**Marcador**|Líneas con marcadores. **Marcador** solo está visible si el margen del indicador está deshabilitado.|
|**Coincidencia de llaves (resaltar)**|Resaltado que suele ser el formato de negrita para la coincidencia de llaves.|
|**Coincidencia de llaves (rectángulo)**|Resaltado que suele ser un rectángulo gris en segundo plano.|
|**Punto de interrupción (deshabilitado)**|No usado.|
|**Punto de interrupción (habilitado)**|Especifica el color de resaltado para las instrucciones o líneas que contienen puntos de interrupción simples. Esta opción solo es aplicable si los puntos de interrupción de nivel de instrucción están activos o si está seleccionada la opción **Resaltar la línea de código fuente para los puntos de interrupción o la instrucción actual** en [General, Depuración, Opciones (Cuadro de diálogo)](../../debugger/general-debugging-options-dialog-box.md).|
|**Punto de interrupción (error)**|Especifica el color de resaltado para las instrucciones o líneas que contienen puntos de interrupción que están en un estado de error. Solo es aplicable si los puntos de interrupción de nivel de instrucción están activos o si está seleccionada la opción **Resaltar la línea de código fuente para los puntos de interrupción o la instrucción actual** en [General, Depuración, Opciones (Cuadro de diálogo)](../../debugger/general-debugging-options-dialog-box.md).|
|**Punto de interrupción (advertencia)**|Especifica el color de resaltado para las instrucciones o líneas que contienen puntos de interrupción simples que están en un estado de advertencia. Solo es aplicable si los puntos de interrupción de nivel de instrucción están activos o si está seleccionada la opción **Resaltar la línea de código fuente para los puntos de interrupción o la instrucción actual** en [General, Depuración, Opciones (Cuadro de diálogo)](../../debugger/general-debugging-options-dialog-box.md).|
|**Punto de interrupción: avanzado (deshabilitado)**|Especifica el color de resaltado para las instrucciones o líneas que contienen puntos de interrupción con número de llamadas o condicionales deshabilitados. Solo es aplicable si los puntos de interrupción de nivel de instrucción están activos o si está seleccionada la opción **Resaltar la línea de código fuente para los puntos de interrupción o la instrucción actual** en [General, Depuración, Opciones (Cuadro de diálogo)](../../debugger/general-debugging-options-dialog-box.md).|
|**Punto de interrupción: avanzado (habilitado)**|Especifica el color de resaltado para las instrucciones o líneas que contienen puntos de interrupción con número de llamadas o condicionales. Solo es aplicable si los puntos de interrupción de nivel de instrucción están activos o si está seleccionada la opción **Resaltar la línea de código fuente para los puntos de interrupción o la instrucción actual** en [General, Depuración, Opciones (Cuadro de diálogo)](../../debugger/general-debugging-options-dialog-box.md).|
|**Punto de interrupción: avanzado (error)**|Especifica el color de resaltado para las instrucciones o líneas que contienen puntos de interrupción con número de llamadas o condicionales que están en un estado de error. Solo es aplicable si los puntos de interrupción de nivel de instrucción están activos o si está seleccionada la opción **Resaltar la línea de código fuente para los puntos de interrupción o la instrucción actual** en [General, Depuración, Opciones (Cuadro de diálogo)](../../debugger/general-debugging-options-dialog-box.md).|
|**Punto de interrupción: avanzado (advertencia)**|Especifica el color de resaltado para las instrucciones o líneas que contienen puntos de interrupción con número de llamadas o condicionales que están en un estado de advertencia. Solo es aplicable si los puntos de interrupción de nivel de instrucción están activos o si está seleccionada la opción **Resaltar la línea de código fuente para los puntos de interrupción o la instrucción actual** en [General, Depuración, Opciones (Cuadro de diálogo)](../../debugger/general-debugging-options-dialog-box.md).|
|**Punto de interrupción: asignado (deshabilitado)**|Especifica el color de resaltado para las instrucciones o líneas que contienen puntos de interrupción asignados deshabilitados. Es aplicable para depuración ASP o ASP.NET si los puntos de interrupción de nivel de instrucción están activos o si está seleccionada la opción **Resaltar la línea de código fuente para los puntos de interrupción o la instrucción actual** en [General, Depuración, Opciones (Cuadro de diálogo)](../../debugger/general-debugging-options-dialog-box.md).|
|**Punto de interrupción: asignado (habilitado)**|Especifica el color de resaltado para las instrucciones o líneas que contienen puntos de interrupción asignados. Es aplicable para depuración ASP o ASP.NET si los puntos de interrupción de nivel de instrucción están activos o si está seleccionada la opción **Resaltar la línea de código fuente para los puntos de interrupción o la instrucción actual** en [General, Depuración, Opciones (Cuadro de diálogo)](../../debugger/general-debugging-options-dialog-box.md).|
|**Punto de interrupción: asignado (error)**|Especifica el color de resaltado para las instrucciones o líneas que contienen puntos de interrupción asignados que están en un estado de error. Es aplicable para depuración ASP o ASP.NET si los puntos de interrupción de nivel de instrucción están activos o si está seleccionada la opción **Resaltar la línea de código fuente para los puntos de interrupción o la instrucción actual** en [General, Depuración, Opciones (Cuadro de diálogo)](../../debugger/general-debugging-options-dialog-box.md).|
|**Punto de interrupción: asignado (advertencia)**|Especifica el color de resaltado para las instrucciones o líneas que contienen puntos de interrupción asignados que están en un estado de advertencia. Es aplicable para depuración ASP o ASP.NET si los puntos de interrupción de nivel de instrucción están activos o si está seleccionada la opción **Resaltar la línea de código fuente para los puntos de interrupción o la instrucción actual** en [General, Depuración, Opciones (Cuadro de diálogo)](../../debugger/general-debugging-options-dialog-box.md).|
|**Palabras clave de usuario de C/C++**|Una constante dentro de un archivo de código determinado definido por medio de la directiva `#define`.|
|**Devolución de llamada**|Especifica el color de resaltado para las instrucciones de origen o líneas que indican puntos de devolución de llamada cuando el contexto cambia a un marco de pila que no es de nivel superior durante la depuración.|
|**Campo dependiente de fragmento de código**|Un campo que se actualizará al modificarse el campo editable actual.|
|**Campo de fragmento de código**|Campo editable cuando está activo un fragmento de código.|
|**Zona contraíble**|Un bloque de texto o código que se puede mostrar u ocultar en el Editor de código.|
|**Comentario**|Comentarios en código.|
|**Error del compilador**|Garabatos azules que aparecen en el editor y que indican un error del compilador.|
|**Área de cobertura no modificada**|Un código que no ha sido cubierto por una prueba unitaria.|
|**Área de cobertura modificada parcialmente**|Un código que ha sido parcialmente cubierto por una prueba unitaria.|
|**Área de cobertura modificada**|Un código que ha sido completamente cubierto por una prueba unitaria.|
|**Comentario CSS**|Un comentario en Hojas de estilos en cascada (CSS, Cascading Style Sheets). Por ejemplo:<br /><br /> /* comment \*/|
|**Palabra clave CSS**|Palabras clave en Hojas de estilos en cascada (CSS, Cascading Style Sheets).|
|**Nombre de propiedad CSS**|El nombre de una propiedad, como Fondo.|
|**Valor de propiedad CSS**|El valor asignado a una propiedad, como azul.|
|**Selector de CSS**|Una cadena que identifica los elementos a los que se aplica la regla correspondiente. Un selector puede ser un selector simple, como 'H1' o un selector contextual, como 'H1 B', que consta de varios selectores simples.|
|**Valor de cadena CSS**|Una cadena en Hojas de estilos en cascada (CSS, Cascading Style Sheets).|
|**Ubicación actual de la lista**|La línea actual a la que se navegó en una ventana de herramientas de lista, como la ventana de salida o la ventana de resultados de búsqueda.|
|**Instrucción actual**|Especifica el color de resaltado para la instrucción de origen o la línea que indica la posición actual del paso al depurar.|
|**Los datos del depurador han cambiado**|El color de texto usado para mostrar los datos cambiados dentro de las ventanas **Registros** y **Memoria**.|
|**Fondo de ventana de definición**|El color de fondo de la ventana **Definición de código**.|
|**Coincidencia actual de la ventana de definición**|La definición actual de la ventana **definición de código**.|
|**Nombre de archivo del desensamblado**|El color de texto usado para mostrar los saltos de nombre de archivo dentro de la ventana **Desensamblado**.|
|**Origen del desensamblado**|El color de texto usado para mostrar las líneas de código fuente dentro de la ventana **Desensamblado**.|
|**Símbolo del desensamblado**|El color de texto usado para mostrar los nombres de símbolos dentro de la ventana **Desensamblado**.|
|**Texto del desensamblado**|El color de texto usado para mostrar el código de operador y los datos dentro de la ventana **Desensamblado**.|
|**Código excluido**|Código que no se pueden compilar, según una directiva de preprocesador condicional como `#if`.|
|**Identificador**|Identificadores en el código, como los nombres de clase, los nombres de métodos y los nombres de variable.|
|**Palabra clave**|Palabras clave para el idioma especificado que están reservadas. Por ejemplo: clase y espacio de nombres.|
|**Dirección de memoria**|El color de texto usado para mostrar la columna de direcciones dentro de la ventana **Memoria**.|
|**Memoria cambiada**|El color de texto usado para mostrar datos cambiados dentro de la ventana **Memoria**.|
|**Datos de memoria**|El color de texto usado para mostrar datos dentro de la ventana **Memoria**.|
|**No se puede leer la memoria**|El color de texto usado para mostrar áreas de memoria dentro de la ventana **Memoria**.|
|**Número**|Un número en el código que representa un valor numérico real.|
|**Operator**|Operadores, como +, -, y! =.|
|**Otro error**|Otros tipos de error no cubiertos por otros subrayados ondulados de errores. Actualmente, incluyen las ediciones superficiales en Editar y continuar.|
|**Palabra clave del preprocesador**|Palabras clave utilizadas por el preprocesador, como #include.|
|**Zona de solo lectura**|No se puede editar el código. Por ejemplo, el código mostrado en la ventana Vista de definición de código o el código que no se puede modificar durante Editar y continuar.|
|**Refactorizando fondo**|Color de fondo de cuadro de diálogo **Obtener vista previa de cambios**.|
|**Campo actual de refactorización**|Color de fondo del elemento actual que se va a refactorizar en el cuadro de diálogo **Obtener vista previa de cambios**.|
|**Campo dependiente de refacturación**|Color de las referencias del elemento que se va a refactorizar en el cuadro de diálogo **Obtener vista previa de cambios**.|
|**Registrar datos**|El color de texto usado para mostrar datos dentro de la ventana **Registros**.|
|**Registrar NAT**|El color de texto usado para mostrar objetos y datos no reconocidos dentro de la ventana **Registros**.|
|**Etiqueta inteligente**|Se utiliza para denotar el esquema cuando se invocan etiquetas inteligentes.|
|**Marcador DML SQL**|Se aplica al Editor de Transact-SQL. Las instrucciones DML de este editor se marcan con un cuadro de límite azul de manera predeterminada.|
|**Código obsoleto**|Código reemplazado que espera una actualización. En algunos casos, Editar y continuar no puede aplicar cambios de código inmediatamente, pero los aplicarán más adelante a medida que continúa con la depuración. Esto ocurre si edita una función que debe llamar a la función que se está ejecutando, o si agrega más de 64 bytes de nuevas variables a una función que está esperando en la pila de llamadas. Cuando esto ocurre, el depurador muestra el cuadro de diálogo "Advertencia de código obsoleto" y el código reemplazado continúa ejecutándose hasta que la función en cuestión finalice y se llame de nuevo. Editar y continuar aplica los cambios de código en ese momento.|
|**String**|Literales de cadena.|
|**Cadena (C# @ Verbatim)**|Literales de cadena en C# que se interpretan literalmente. Por ejemplo:<br /><br /> @"x"|
|**Error de sintaxis**|Errores de análisis.|
|**Acceso directo de la Lista de tareas**|Si se agrega a una línea un acceso directo de la **Lista de tareas** y el margen del indicador está deshabilitado, se resaltará la línea.|
|**Punto de seguimiento (deshabilitado)**|No usado.|
|**Punto de seguimiento (habilitado)**|Especifica el color de resaltado para las instrucciones o líneas que contienen puntos de seguimiento simples. Esta opción solo es aplicable si los puntos de seguimiento de nivel de instrucción están activos o si está seleccionada la opción **Resaltar la línea de código fuente para los puntos de interrupción o la instrucción actual** en [General, Depuración, Opciones (Cuadro de diálogo)](../../debugger/general-debugging-options-dialog-box.md).|
|**Punto de seguimiento (error)**|Especifica el color de resaltado para las instrucciones o líneas que contienen puntos de seguimiento que están en un estado de error. Esta opción solo es aplicable si los puntos de seguimiento de nivel de instrucción están activos o si está seleccionada la opción **Resaltar la línea de código fuente para los puntos de interrupción o la instrucción actual** en [General, Depuración, Opciones (Cuadro de diálogo)](../../debugger/general-debugging-options-dialog-box.md).|
|**Punto de seguimiento (advertencia)**|Especifica el color de resaltado para las instrucciones o líneas que contienen puntos de seguimiento que están en un estado de advertencia. Esta opción solo es aplicable si los puntos de seguimiento de nivel de instrucción están activos o si está seleccionada la opción **Resaltar la línea de código fuente para los puntos de interrupción o la instrucción actual** en [General, Depuración, Opciones (Cuadro de diálogo)](../../debugger/general-debugging-options-dialog-box.md).|
|**Punto de seguimiento: avanzado (deshabilitado)**|Especifica el color de resaltado para las instrucciones o líneas que contienen puntos de seguimiento con número de llamadas o condicionales deshabilitados. Esta opción solo es aplicable si los puntos de seguimiento de nivel de instrucción están activos o si está seleccionada la opción **Resaltar la línea de código fuente para los puntos de interrupción o la instrucción actual** en [General, Depuración, Opciones (Cuadro de diálogo)](../../debugger/general-debugging-options-dialog-box.md).|
|**Punto de seguimiento: avanzado (habilitado)**|Especifica el color de resaltado para las instrucciones o líneas que contienen puntos de seguimiento con número de llamadas o condicionales. Esta opción solo es aplicable si los puntos de seguimiento de nivel de instrucción están activos o si está seleccionada la opción **Resaltar la línea de código fuente para los puntos de interrupción o la instrucción actual** en [General, Depuración, Opciones (Cuadro de diálogo)](../../debugger/general-debugging-options-dialog-box.md).|
|**Punto de seguimiento: avanzado (error)**|Especifica el color de resaltado para las instrucciones o líneas que contienen puntos de seguimiento con número de llamadas o condicionales que están en un estado de error. Esta opción solo es aplicable si los puntos de seguimiento de nivel de instrucción están activos o si está seleccionada la opción **Resaltar la línea de código fuente para los puntos de interrupción o la instrucción actual** en [General, Depuración, Opciones (Cuadro de diálogo)](../../debugger/general-debugging-options-dialog-box.md).|
|**Punto de seguimiento: avanzado (advertencia)**|Especifica el color de resaltado para las instrucciones o líneas que contienen puntos de seguimiento con número de llamadas o condicionales que están en un estado de advertencia. Esta opción solo es aplicable si los puntos de seguimiento de nivel de instrucción están activos o si está seleccionada la opción **Resaltar la línea de código fuente para los puntos de interrupción o la instrucción actual** en [General, Depuración, Opciones (Cuadro de diálogo)](../../debugger/general-debugging-options-dialog-box.md).|
|**Punto de seguimiento: asignado (deshabilitado)**|Especifica el color de resaltado para las instrucciones o líneas que contienen puntos de seguimiento asignados deshabilitados. Es aplicable para depuración ASP o ASP.NET si los puntos de interrupción de nivel de instrucción están activos o si está seleccionada la opción **Resaltar la línea de código fuente para los puntos de interrupción o la instrucción actual** en [General, Depuración, Opciones (Cuadro de diálogo)](../../debugger/general-debugging-options-dialog-box.md).|
|**Punto de seguimiento: asignado (habilitado)**|Especifica el color de resaltado para las instrucciones o líneas que contienen puntos de seguimiento asignados. Es aplicable para depuración ASP o ASP.NET si los puntos de interrupción de nivel de instrucción están activos o si está seleccionada la opción **Resaltar la línea de código fuente para los puntos de interrupción o la instrucción actual** en [General, Depuración, Opciones (Cuadro de diálogo)](../../debugger/general-debugging-options-dialog-box.md).|
|**Punto de seguimiento: asignado (error)**|Especifica el color de resaltado para las instrucciones o líneas que contienen puntos de seguimiento asignados que están en un estado de error. Es aplicable para depuración ASP o ASP.NET si los puntos de interrupción de nivel de instrucción están activos o si está seleccionada la opción **Resaltar la línea de código fuente para los puntos de interrupción o la instrucción actual** en [General, Depuración, Opciones (Cuadro de diálogo)](../../debugger/general-debugging-options-dialog-box.md).|
|**Punto de seguimiento: asignado (advertencia)**|Especifica el color de resaltado para las instrucciones o líneas que contienen puntos de seguimiento asignados que están en un estado de advertencia. Es aplicable para depuración ASP o ASP.NET si los puntos de interrupción de nivel de instrucción están activos o si está seleccionada la opción **Resaltar la línea de código fuente para los puntos de interrupción o la instrucción actual** en [General, Depuración, Opciones (Cuadro de diálogo)](../../debugger/general-debugging-options-dialog-box.md).|
|**Control de cambios después de guardar**|Líneas de código que se han modificado desde que se abrió el archivo pero que se guardaron en el disco.|
|**Control de cambios antes de guardar**|Líneas de código que se han modificado desde que se abrió el archivo pero que no se guardaron en el disco.|
|**Tipos de usuario**|Tipos definidos por los usuarios.|
|**Tipos de usuario (delegados)**|Color del tipo de los delegados.|
|**Tipos de usuario (enumeraciones)**|Color del tipo utilizado para las enumeraciones.|
|**Tipos de usuario (interfaces)**|Color del tipo de las interfaces.|
|**Tipos de usuario (tipos de valor)**|Color del tipo de tipos de valor como estructuras en C#.|
|**Marcador de solo lectura de Visual Basic**|Un marcador específico de Visual Basic para designar EnC, como áreas de excepción, una definición de método y marcos de llamada no hoja.|
|**Advertencia**|Advertencias del compilador.|
|**Ruta de acceso de líneas de advertencia**|Se utiliza para las líneas de advertencia de Análisis estático.|
|**Atributo XML**|Nombres de atributo.|
|**Comillas de atributo XML**|Los caracteres de comillas para los atributos XML.|
|**Valor del atributo XML**|Contenido de atributos XML.|
|**Sección CData XML**|Contenido de \<![CDATA[...]]>.|
|**Comentario XML**|Contenido de \<!-- -->.|
|**Delimitador XML**|Delimitadores de sintaxis XML, incluidos <, <?, <!, \<!--, -->, ?\>, \<![, ]]> y [, ].|
|**Atributo de documento XML**|Valor de un atributo de documentación XML, como \<param name="I">, donde la "I" se colorea.|
|**Comentario de documento XML**|Los comentarios incluidos en los comentarios de documentación xml.|
|**Etiqueta de documento XML**|Las etiquetas en los comentarios de documentos XML, como<br /><br /> /// \<summary>.|
|**Palabra clave XML**|Palabras clave de DTD como CDATA, IDREF y NDATA.|
|**Nombre XML**|Los nombres de elementos y el nombre de destino de las instrucciones de procesamiento.|
|**Instrucción de procesamiento XML**|Contenido de las instrucciones de procesamiento, sin incluir el nombre de destino.|
|**Texto XML**|Contenido del elemento de texto sin formato.|
|**Palabra clave XSLT**|Nombres de elementos XSLT.|

**Primer plano del elemento**

Muestra los colores disponibles que puede seleccionar para el primer plano del elemento seleccionado en **Elementos para mostrar**. Puesto que algunos elementos están relacionados y, por tanto, deben mantener un esquema par mostrar coherente, si cambia el color de primer plano del texto también cambian los valores predeterminados para elementos como Error del compilador, Palabra clave u Operador.

**Automático**

Los elementos pueden heredar el color de primer plano de otros elementos para mostrar como **Texto sin formato**. Con esta opción, al cambiar el color de un elemento para mostrar heredado, el color de los elementos mostrados relacionados también cambia automáticamente. Por ejemplo, si ha seleccionado el valor **Automático** para el **Error del compilador** y después ha cambiado el color del **Texto sin formato** a rojo, el **Error del compilador** también heredaría automáticamente el color rojo.

**Predetermiado**

Color que aparece para el elemento la primera vez que se abre Visual Studio. Al hacer clic en el botón **Usar valores predeterminados** restablece este color.

**Custom**

Muestra el cuadro de diálogo Color para permitirle establecer un color personalizado para el elemento seleccionado en la lista Elementos para mostrar

> [!NOTE]
> Su capacidad para definir colores personalizados puede verse limitada por la configuración de color de la pantalla de su equipo. Por ejemplo, si su equipo está configurado para mostrar 256 colores y selecciona un color personalizado en el cuadro de diálogo **Color**, el IDE tiene como valor predeterminado el **Color básico** más similar disponible y muestra el color negro en el cuadro de vista previa **Color**.

**Segundo plano del elemento**

Proporciona una paleta de colores de la que puede seleccionar un color de fondo para el elemento seleccionado en **Elementos para mostrar**. Puesto que algunos elementos están relacionados y, por tanto, deben mantener un esquema par mostrar coherente, si cambia el color de fondo del texto también cambian los valores predeterminados para elementos como Error del compilador, Palabra clave u Operador.

**Automático**

Los elementos pueden heredar el color de fondo de otros elementos para mostrar como **Texto sin formato**. Con esta opción, al cambiar el color de un elemento para mostrar heredado, el color de los elementos mostrados relacionados también cambia automáticamente. Por ejemplo, si ha seleccionado el valor **Automático** para el **Error del compilador** y después ha cambiado el color del **Texto sin formato** a rojo, el **Error del compilador** también heredaría automáticamente el color rojo.

**Predetermiado**

Color que aparece para el elemento la primera vez que se abre Visual Studio. Al hacer clic en el botón **Usar valores predeterminados** restablece este color.

**Custom**

Muestra el cuadro de diálogo Color para permitirle establecer un color personalizado para el elemento seleccionado en la lista Elementos para mostrar

**Negrita**

Seleccione esta opción para mostrar el texto de los **Elementos para mostrar** seleccionados en negrita. El texto en negrita es más fácil de identificar en el editor.

**Ejemplo**

Muestra un ejemplo de la combinación de colores, del tamaño y del estilo de la fuente para **Mostrar valores para** y para **Elementos para mostrar** seleccionados. Puede utilizar este cuadro para obtener una vista previa de los resultados mientras experimenta con diferentes opciones de formato.

## <a name="see-also"></a>Vea también

- [Opciones (cuadro de diálogo)](../../ide/reference/options-dialog-box-visual-studio.md)
- [Cómo: Cambiar fuentes y colores](../../ide/how-to-change-fonts-and-colors-in-visual-studio.md)
