---
title: Opciones, editor de texto, C/C++ y visualización
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.View
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.View
- VS.ToolsOptionsPages.Text_Editor.C\C++.View
author: mikeblome
ms.author: mblome
manager: wpickett
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.workload:
- cplusplus
ms.openlocfilehash: c4ffef0b1b76f453048ff20e3cbada0b8a591c65
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388837"
---
# <a name="options-text-editor-cc-view"></a>Opciones, editor de texto, C/C++ y visualización

Utilice estas páginas de propiedades para cambiar el comportamiento predeterminado del editor de código cuando se programa en C o C++.

Para acceder a esta página de propiedades, elija **Herramientas** > **Opciones** y expanda **Editor de texto**. Luego, seleccione **C/C++** y elija **Vista**.

## <a name="code-squiggles"></a>Subrayados ondulados de código

Puede habilitar o deshabilitar las siguientes opciones para administrar la manera en que el editor de texto controla los subrayados ondulados de código de C y C++:

- **Macros en regiones donde se omite la exploración**: define cómo resaltar las macros que están dentro de regiones omitidas por la base de datos de exploración, como las macros cuyas definiciones incluyen llaves.

- **Macros convertibles en constexpr**: define cómo resaltar las definiciones de macro que se pueden convertir en definiciones `constexpr`.

## <a name="inactive-code"></a>Código inactivo

- **Mostrar bloques inactivos**: los bloques inactivos del preprocesador se colorean de forma diferente.

- **Deshabilitar opacidad de código inactivo**: se usa un color sólido en lugar de opacidad para los bloques de código inactivos.

- **Porcentaje de opacidad del código inactivo**: porcentaje de opacidad de los bloques de código inactivos.

## <a name="miscellaneous"></a>Varios

- **Enumerar tareas de comentario**: examina los archivos de código fuente abiertos en busca de tokens de VS y los muestra en la ventana Lista de tareas.

- **Resaltar tokens de emparejamiento**: resalta la sintaxis o las llaves delimitadoras que coinciden con la posición del cursor.

## <a name="outlining"></a>esquematizar

- **Habilitar esquematización**: entra en el modo de esquematización cuando se abre un archivo.

- **Esquematizar regiones pragma**: esquematiza automáticamente bloques de región `#pragma`.

- **Esquematizar bloques de instrucciones**: esquematiza automáticamente bloques de instrucciones.

## <a name="see-also"></a>Vea también

- [Opciones del editor específicas del lenguaje](../../ide/reference/setting-language-specific-editor-options.md)
- [Refactorización en C++ (Blog de VC)](http://blogs.msdn.com/b/vcblog/archive/2014/11/14/all-about-c-refactoring-in-visual-studio-2015-preview.aspx)
