---
title: Opciones, editor de texto, C#, IntelliSense | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Intellisense
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Intellisense
helpviewer_keywords:
- IntelliSense [J#], options
- underlines, wavy
- IntelliSense [C#], options
- IntelliSense [C#], wavy underlines
- wavy underlines
- Text Editor Options dialog box, IntelliSense
ms.assetid: 3466dedb-e5f4-424c-8dd8-e4941b2f4fc2
caps.latest.revision: 30
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1e3f4df9a7a885245e40f7e9fec1b0da207ada39
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662296"
---
# <a name="options-text-editor-c-intellisense"></a>Opciones, editor de texto, C#, IntelliSense
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Use la página de propiedades **IntelliSense** para modificar la configuración que afecta al comportamiento de IntelliSense para Visual C#. Puede tener acceso a la página de propiedades **IntelliSense** haciendo clic en **Opciones** en el menú **Herramientas**, después hacer clic en **C#** en la carpeta **Editor de texto** y, después, hacer clic en **IntelliSense.**

> [!NOTE]
> Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para obtener más información, consulte [Personalizar la configuración de desarrollo en Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

 La página de propiedades **IntelliSense** contiene las siguientes propiedades:

## <a name="completion-lists"></a>Listas de finalización
 **Mostrar lista de finalización después de escribir un carácter** Cuando se selecciona esta opción, IntelliSense muestra automáticamente la lista de finalización al empezar a escribir. Cuando esta opción no está seleccionada, la finalización de IntelliSense todavía está disponible desde el menú **IntelliSense** o presionando CTRL+BARRA ESPACIADORA.

 **Colocar palabras clave en las listas de finalización** Cuando se selecciona esta opción, IntelliSense agrega C# palabras clave, por ejemplo, [clase](https://msdn.microsoft.com/library/b95d8815-de18-4c3f-a8cc-a0a53bdf8690), a la lista de finalización.

 **Colocar fragmentos de código en listas de finalización** Cuando se selecciona esta opción, IntelliSense agrega alias para los C# fragmentos de código a la lista de finalización. En el caso en que el alias de fragmento de código sea el mismo que una palabra clave, por ejemplo, [class](https://msdn.microsoft.com/library/b95d8815-de18-4c3f-a8cc-a0a53bdf8690), la palabra clave se reemplaza mediante el acceso directo. Para obtener más información, vea [Fragmentos de código de Visual C#](../../ide/visual-csharp-code-snippets.md).

## <a name="selection-in-completion-lists"></a>Selección en las listas de finalización
 **Confirmado escribiendo los siguientes caracteres:** Especifica todos los caracteres que ejecutan la finalización automática de IntelliSense para el elemento seleccionado en la lista de finalización, una vez que se escriben.

 **Confirmado presionando la barra espaciadora** Especifica que se incluya la acción de presionar la barra espaciadora para ejecutar la finalización automática de IntelliSense para el elemento seleccionado en la lista de finalización.

 **Agregar nueva línea al final de la palabra completa** Especifica que si escribe todos los caracteres de una entrada en la lista de finalización y, a continuación, presiona entrar, se crea automáticamente una nueva línea y el cursor se mueve a la nueva línea.

 Por ejemplo, si escribe `else` y, después, presiona ENTRAR, aparece lo siguiente en el editor:

 `else`

 `|` (ubicación del cursor)

 En cambio, si escribe solo `el` y, después, presiona ENTRAR, aparece lo siguiente en el editor:

 `else|` (ubicación del cursor)

## <a name="intellisense-member-selection"></a>Selección de miembros de IntelliSense
 **Selecciona previamente el miembro usado más recientemente** Cuando se selecciona esta opción, IntelliSense preselecciona los miembros que ha seleccionado recientemente en el cuadro lista de miembros emergentes para la finalización automática de los nombres de objeto, durante la sesión actual en el entorno de desarrollo integrado (IDE). El historial de los miembros usados recientemente se borra entre cada sesión del IDE. Para obtener más información, vea [IntelliSense para los miembros usados más recientemente](../../misc/intellisense-for-most-recently-used-members.md).

## <a name="see-also"></a>Otras referencias
 [General, entorno, opciones (cuadro de diálogo)](../../ide/reference/general-environment-options-dialog-box.md) [comentarios de documentación XML](https://msdn.microsoft.com/library/803b7f7b-7428-4725-b5db-9a6cff273199) [mediante IntelliSense](../../ide/using-intellisense.md)
