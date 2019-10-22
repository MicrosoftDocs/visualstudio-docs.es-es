---
title: Opciones, editor de texto, todos los lenguajes, pestañas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.ResJSON.Tabs
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Tabs
- VS.ToolsOptionsPages.Text_Editor.All_Languages.Tabs
helpviewer_keywords:
- indents, Code Editor
- Code Editor, default behavior
- tabs, setting in Code Editor
- All Languages Text Editor Options dialog box
- editors, Code Editor
- Code Editor, indenting
- Code Editor, tabs
ms.assetid: 7e208e1d-5e3a-4bf7-a27b-4417e3e049c7
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4cb670ab52e321f15c5b009c66ca40623409f10a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662384"
---
# <a name="options-text-editor-all-languages-tabs"></a>Opciones, editor de texto, todos los lenguajes, pestañas
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Este cuadro de diálogo le permite cambiar el comportamiento predeterminado del Editor de código. Estas opciones también se aplican a otros editores basados en el Editor de código, como la vista de origen del diseñador HTML. Para mostrar estas opciones, seleccione **Opciones** desde el menú **Herramientas**. En la carpeta **Editor de texto**, expanda la subcarpeta **Todos los lenguajes** y, después, pulse **Pestañas**.

> [!CAUTION]
> Esta página establece las opciones predeterminadas de todos los lenguajes de desarrollo. Recuerde que restablecer una opción en este cuadro de diálogo restablecerá las opciones de pestañas de todos los lenguajes para cualquier elección seleccionada aquí. Para cambiar las opciones del Editor de texto solo de un lenguaje, expanda la subcarpeta de ese lenguaje y seleccione sus páginas de opciones.

 Si están seleccionadas diferentes opciones en las páginas de opciones de pestañas para lenguajes de programación determinados, entonces el mensaje "Los valores de la sangría para formatos de texto individuales están en conflicto entre sí" se muestra para las distintas opciones de **sangría**; y se muestra el mensaje "Los valores del tabulador para formatos de texto individuales están en conflicto entre sí" para las distintas opciones del **tabulador**. Por ejemplo, este recordatorio se muestra si la opción **Sangría inteligente** está seleccionada para Visual Basic, pero **Sangría de bloques** está seleccionada para Visual C++.

> [!NOTE]
> Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para obtener más información, consulte [Personalizar la configuración de desarrollo en Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="indenting"></a>Aplicar sangría
 Ninguno cuando se selecciona, no se aplica sangría a las líneas nuevas. El punto de inserción se coloca en la primera columna de una nueva línea.

 Bloquear cuando se selecciona, se aplica sangría automáticamente a las nuevas líneas. El punto de inserción se coloca en el mismo punto inicial que la línea anterior.

 Inteligente Cuando está seleccionada, se colocan nuevas líneas para ajustarse al contexto de código, por otras opciones de formato de código y convenciones de IntelliSense para el lenguaje de desarrollo. Esta opción no está disponible para todos los lenguajes de desarrollo.

 Por ejemplo, a las líneas que aparecen entre una llave inicial ( { ) y una llave de cierre ( } ) se les puede aplicar automáticamente una sangría equivalente a una posición de tabulación adicional con respecto a la posición de las llaves alineadas.

## <a name="tabs"></a>Tabulaciones
 Tamaño de tabulación establece la distancia en espacios entre las tabulaciones. El valor predeterminado es de cuatro espacios.

 Tamaño de sangría establece el tamaño en espacios de una sangría automática. El valor predeterminado es de cuatro espacios. Se insertan caracteres de tabulación, caracteres de espacio o ambos, para llenar el tamaño especificado.

 Insertar espacios cuando se selecciona, las operaciones de sangría insertan solo caracteres de espacio, no caracteres de TABULAción. Si el **Tamaño de sangría** se establece en 5, por ejemplo, se insertarán cinco caracteres de espacio cada vez que se presione la tecla TAB o el botón **Aumentar sangría** en la barra de herramientas **Formato**.

 Mantener tabulaciones cuando se selecciona, las operaciones de sangría insertan tantos caracteres de TABULAción como sea posible. Cada carácter de tabulación rellena el número de espacios especificado en **Tamaño de tabulación**. Si el **Tamaño de sangría** no es un múltiplo par del **Tamaño de tabulación**, se agregan caracteres de espacio en blanco para igualar la diferencia.

## <a name="see-also"></a>Otras referencias
 [Opciones, editor de texto, todos los lenguajes](../../ide/reference/options-text-editor-all-languages.md) [General, entorno, opciones (cuadro de diálogo)](../../ide/reference/general-environment-options-dialog-box.md)
