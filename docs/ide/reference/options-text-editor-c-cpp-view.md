---
title: Opciones, editor de texto, C/C++ y visualización
description: Obtenga información sobre cómo usar la página Vista de la sección C/C++ para cambiar el comportamiento predeterminado de las propiedades Subrayados ondulados de código, Código inactivo, Esquematización, etc., en Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.View
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.View
- VS.ToolsOptionsPages.Text_Editor.C\C++.View
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 68d08953ca3c493f3b3e42dd4ddd84bc19bdfd6e
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/25/2020
ms.locfileid: "96041079"
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

## <a name="see-also"></a>Consulte también

- [Opciones del editor específicas del lenguaje](../../ide/reference/setting-language-specific-editor-options.md)
- [Refactorización en C++ (Blog de VC)](https://devblogs.microsoft.com/cppblog/all-about-c-refactoring-in-visual-studio-2015-preview/)
