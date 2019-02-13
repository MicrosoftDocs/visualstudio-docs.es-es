---
title: Opciones, editor de texto, C/C++, formato
ms.date: 04/30/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.C%2fC%2b%2b.Formatting.General
dev_langs:
- CPP
helpviewer_keywords:
- Text Editor Options dialog box, formatting
- ClangFormat
ms.assetid: cb6f1cbb-5305-48da-a8e8-33fd70775d46
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: ae24e69ddceea88155d7185157a6ed25daab5430
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55922126"
---
# <a name="options-text-editor-cc-formatting"></a>Opciones, editor de texto, C/C++, formato

Utilice estas páginas de propiedades para cambiar el comportamiento predeterminado del editor de código cuando se programa en C o C++.

[Páginas de propiedades de formato de C++](media/cpp-formatting.png)

 Para tener acceso a esta página, en el cuadro de diálogo **Opciones**, en el panel izquierdo, expanda **Editor de texto**, expanda **C/C++** y, a continuación, haga clic en **Formato**.

> [!NOTE]
> Es posible que el equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="general-page"></a>Página general

Esta página tiene opciones para dar formato a las instrucciones y las bloquea a medida que las escribe.

**Visual Studio 2017 versión 15.7 y posteriores:** La página también tiene opciones para configurar la compatibilidad con [ClangFormat](https://clang.llvm.org/docs/ClangFormat.html) versión 5.0. ClangFormat es una utilidad que facilita aplicar estilo y dar formato al código según un conjunto de reglas que se pueden configurar en un archivo de formato .clang o de formato _clang.

### <a name="configuring-clangformat-options"></a>Configurar las opciones de ClangFormat

En Visual Studio 2017 versión 15.7 y versiones posteriores, la compatibilidad con ClangFormat está habilitada de forma predeterminada. Puede elegir cuál de estas convenciones de formato comunes quiere aplicar a todos los proyectos: LLVM, Google, Chromium, Mozilla o WebKit. También puede crear un archivo de formato .clang o _clang de definición de formato personalizado. Si este archivo está presente en una carpeta de proyecto, Visual Studio lo usará para dar formato a todos los archivos de código fuente en esa carpeta y en sus subcarpetas. 

De forma predeterminada, Visual Studio ejecuta clangformat.exe en segundo plano y aplica formato a medida que escribe. También puede especificar que solo se ejecute manualmente en los comandos de formato invocados manualmente **Dar formato al documento (Ctrl+K, Ctrl+D)** o **Dar formato a la selección (Ctrl+K, Ctrl+F)**.


## <a name="indentation-new-lines-spacing-wrapping-pages"></a>Páginas de sangría, nuevas líneas, ajuste del espaciado

Estas páginas permiten varias personalizaciones de formato pero se omiten si ClangFormat está habilitado.

## <a name="see-also"></a>Vea también

- [General, Entorno, Opciones (Cuadro de diálogo)](../../ide/reference/general-environment-options-dialog-box.md)
- [Usar IntelliSense](../../ide/using-intellisense.md)