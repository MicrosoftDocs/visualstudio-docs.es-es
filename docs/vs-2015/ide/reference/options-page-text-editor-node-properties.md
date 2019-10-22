---
title: Página de opciones, Propiedades de nodo Editor de texto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Tools Options settings, Text Editor node properties
- automation [Visual Studio], controlling Tools Options
ms.assetid: 19438302-0677-4f4d-9720-5667e6a22ab2
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 62dddacaea1846c8e5d5da404ad7a16fde90f209
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662412"
---
# <a name="options-page-text-editor-node-properties"></a>Página de opciones, Propiedades de nodo Editor de texto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En este documento, se describen algunas páginas (o colecciones de propiedades) asociadas a la categoría **Editor de texto**, `DTE.Properties("TextEditor", <Property Page>)`, del cuadro de diálogo **Opciones**. El título de cada subsección es la llamada que se usa para obtener acceso a la colección `Properties` y, en la tabla de cada subsección, se muestran las propiedades que se encuentran en la colección.

 Las macros de Visual Basic de [Controlar la configuración de opciones](https://msdn.microsoft.com/library/a09ed242-7494-4cde-bbd1-7a8ec617965d) ilustran cómo se muestran las opciones actuales y los valores de cada página del cuadro de diálogo **Opciones**.

## <a name="general"></a>General
 `DTE.Properties("TextEditor", "General")`

|Nombre de elemento de propiedad|Valor|DESCRIPCIÓN|
|------------------------|-----------|-----------------|
|GoToAnchorAfterEscape|Get/Set (Boolean)|Si es `True`, al presionar escape cuando hay elementos seleccionados, el punto de inserción se desplaza al lugar donde se inició la acción que creó la selección. `False` desplaza el punto de inserción al otro extremo de la selección.|
|DragNDropTextEditing|Get/Set (Boolean)|Determina si se puede arrastrar una porción de texto seleccionado desde una ubicación a otra en el documento para operaciones de copiar, cortar y pegar.|
|HorizontalScrollBar|Get/Set (Boolean)|Determina si las ventanas del editor contienen una barra de desplazamiento horizontal.|
|VerticalScrollBar|Get/Set (Boolean)|Determina si las ventanas del editor contienen una barra de desplazamiento vertical.|
|SelectionMargin|Get/Set (Boolean)|Determina si se deja espacio a la izquierda del panel de texto para operaciones de selección especiales, para iconos de punto de interrupción, etc.|
|MarginIndicatorBar|Get/Set (Boolean)|Determina si una línea vertical separa el margen izquierdo del panel de texto del cuerpo principal del mismo.|
|UndoCaretActions|Get/Set (Boolean)|Si `True`. las operaciones de la fase de reversión incluyen el movimiento del punto de inserción, los comandos de selección, etc., además de las acciones de edición que modifican el búfer.|
|AutoDelimiterHighlighting|Get/Set (Boolean)|Determina si, al escribir un delimitador de cierre, el editor resalta el delimitador de apertura. Independientemente del valor de esta propiedad, el editor destaca en negrita el delimitador de apertura.|
|EditorEmulation|Get/Set (Enum)||
|DetectUTF8WithoutSignature|Get/Set (Boolean)|Detecta si un archivo usa la codificación UTF-8 cuando no tiene una firma de codificación.|
|TrackChanges|Get/Set (Boolean)||

## <a name="plain-text"></a>Texto sin formato
 `DTE.Properties("TextEditor", "PlainText")`

 Las opciones del editor `PlainText` afectan a la configuración del editor cuando se editan archivos de texto. Cada lenguaje de programación y paquete de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] tienen su propia configuración específica del **Editor de texto**. Por ejemplo, para ver o cambiar la configuración del editor de [!INCLUDE[csprcs](../../includes/csprcs-md.md)], utilice `DTE.Properties("TextEditor", "CSharp") or DTE.Properties("TextEditor", "CSharp-Specific")`. Para la configuración del editor de **Script SQL**, use `DTE.Properties("TextEditor", "SQL ")`.

|Nombre de elemento de propiedad|Valor|DESCRIPCIÓN|
|------------------------|-----------|-----------------|
|AutoListMembers|Get/Set (Boolean)|Determina si una lista de miembros disponible aparece de forma automática cuando un usuario escribe un punto a continuación de una referencia a una variable.|
|AutoListParams|Get/Set (Boolean)|Determina si se muestra automáticamente una descripción de una lista de argumentos cuando el usuario escribe "(" después de un nombre de función.|
|HideAdvancedMembers|Get/Set (Boolean)|Determina si la finalización de instrucciones incluye todos los miembros o sólo los más comunes.|
|VirtualSpace|Get/Set (Boolean)|Determina si los caracteres de espacio en blanco se muestran en forma de gráficos. Si se establece como `true`, el elemento de propiedades `WordWrap` (de esta lista) se establecerá en `false`.|
|WordWrap|Get/Set (Boolean)|Determina si se ajustan las líneas largas en los límites de las palabras. Si se establece como `true`, el elemento de propiedades `VirtualSpace` (de esta lista) se establecerá en `false`.|
|WordWrapGlyphs|Get/Set (Boolean)|Muestra un glifo al final de una línea; esto indica que la línea se ajusta a la línea siguiente.|
|EnableLeftClickForURLs|Get/Set (Boolean)|Determina si el editor subraya las URL y permite efectuar un solo clic con el botón primario del mouse para saltar a la URL del explorador web registrado en el sistema.|
|IndentStyle|Get/Set (<xref:EnvDTE.vsIndentStyle>)|Determina el estilo de sangría: Default, Smart o None.|
|TabSize|Get/Set (Long)|Representa el número de espacios a los que equivale un tabulador. Si se selecciona un entero fuera del intervalo de 1 a 60 (incluidos), se producirá un error.|
|InsertTabs|Get/Set (Boolean)|Si es `True`, se utilizan caracteres de tabulación al aplicar sangría.|
|IndentSize|Get/Set (Long)|Representa el número de espacios a los que equivale un nivel de sangría. Si se selecciona un valor entero fuera del intervalo de 1 a 60 (incluidos), se producirá un error.|
|ShowLineNumbers|Get/Set (Boolean)|Determina si en la vista de un documento en el editor principal muestra los números de línea en el margen izquierdo.|
|ShowNavigationBar|Get/Set (Boolean)|Determina si aparecen listas desplegables y botones en la parte superior de las ventanas del editor.|
|CutCopyBlankLines|Get/Set (Boolean)|Corta o copia las líneas en blanco cuando están seleccionadas.|

## <a name="see-also"></a>Otras referencias
 [Controlar la configuración de opciones](https://msdn.microsoft.com/library/a09ed242-7494-4cde-bbd1-7a8ec617965d) [determinar los nombres de elementos de propiedades en las páginas de opciones](https://msdn.microsoft.com/library/d450422d-47c7-4eeb-9f9f-3286264bc5aa) [Página opciones, página Opciones propiedades de nodo de entorno](../../ide/reference/options-page-environment-node-properties.md) [, propiedades de nodo fuentes y colores](../../ide/reference/options-page-fonts-and-colors-node-properties.md)
