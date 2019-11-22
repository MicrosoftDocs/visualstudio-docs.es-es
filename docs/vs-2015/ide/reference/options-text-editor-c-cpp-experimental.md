---
title: Opciones, editor de texto, C/C++, experimental | Microsoft Docs
ms.date: 11/15/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Experimental
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Experimental
- VS.ToolsOptionsPages.Text_Editor.C\C++.Experimental
ms.assetid: b9e9dda2-350c-460d-b368-37d6c5342eee
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5979363f16f2e9d78a2f50ffbb6511d03146caaa
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297853"
---
# <a name="options-text-editor-cc-experimental"></a>Opciones, editor de texto, C/C++, experimental
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Al cambiar estas opciones, puede modificar el comportamiento relacionado con IntelliSense y la base de datos de exploración cuando programa en C o C++.

 Para tener acceso a esta página, en el cuadro de diálogo **Opciones** , en el panel izquierdo, expanda **Editor de texto**, expanda **C/C++** y luego haga clic en **Experimental**.

 Estas características están disponibles en una instalación de Visual Studio 2015 Update 1 RC.

> [!NOTE]
> Es posible que tu equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Vea [Personalizar la configuración de desarrollo en Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="browsingnavigation"></a>Exploración o navegación
 **Enable New Database Engine** This should automatically speed up database population and make all database operations faster (with no loss in accuracy) for operations such as **Go To Definition** and **Find All References**. (Para aplicar los cambios, solo cierre y vuelva a abrir la solución; no es necesario reiniciar Visual Studio).

## <a name="intellisense"></a>IntelliSense
 **Member List Dot-To-Arrow** Replaces '.' with '->' when applicable for Member List.

## <a name="refactoring"></a>Refactoring
 **Enable Extract Function** Extract selected code to its own function and replace code with a call to the new function. Para obtener acceso a esta característica, haga clic con el botón derecho en el código seleccionado y seleccione **Acciones rápidas**o simplemente presione el método abreviado de teclado predeterminado Ctrl+punto [Ctrl+.].

 **Enable Change Signature** Add, reorder, and delete parameters of a function and propagate the changes to all call sites. Para obtener acceso a esta característica, haga clic con el botón derecho en cualquier uso de la función y seleccione **Acciones rápidas**o simplemente presione el método abreviado predeterminado Ctrl+punto [Ctrl+.].

## <a name="text-editor"></a>Editor de texto
 **Enable Expand Scopes** If enabled, you can surround selected text with curly braces by typing '{' into the text editor.

 **Enable Expand Precedence** If enabled, you can surround selected text with parentheses by typing '(' into the text editor.

 Para conocer las características adicionales del editor de texto de la Galería de Visual Studio, consulte la lista [aquí](https://go.microsoft.com/fwlink/?LinkId=692016). Un ejemplo es [C++ Quick Fixes](https://visualstudiogallery.msdn.microsoft.com/be91feef-8dc3-4f7a-ac9f-f34e7ca5918f), que admite lo siguiente:

- **Agregar #include faltante** : sugiere las directivas #include pertinentes para símbolos desconocidos en el código

- **Agregar mediante espacio de nombres o símbolo completo** : similar al elemento anterior, pero para espacios de nombres

- **Agregar punto y coma faltante**

- **Ayuda de MSDN** : buscar en MSDN los mensajes de error

  Puede mantener el puntero sobre una línea ondulada para obtener una bombilla, o bien use el método abreviado de teclado predeterminado CTRL+punto (Ctrl+.). Tenga en cuenta que en el caso del método abreviado de teclado, no es necesario situar el símbolo de intercalación en el error o token específico. Simplemente puede estar en la misma línea que el error para invocar sugerencias para cualquier elemento incluido en esa línea.

## <a name="see-also"></a>Vea también
 [Setting Language-Specific Editor Options](../../ide/reference/setting-language-specific-editor-options.md) [Refactoring in C++ (VC Blog)](https://devblogs.microsoft.com/cppblog/all-about-c-refactoring-in-visual-studio-2015-preview/)
