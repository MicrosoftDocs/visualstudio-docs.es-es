---
title: Cuadro de diálogo Valores predeterminados de Visual Basic, Proyectos, Opciones | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.VBDefaults
helpviewer_keywords:
- Option Explicit statement, setting in the IDE
- Option Compare statement, setting in the IDE
- Option Strict statement, setting in the IDE
ms.assetid: 2465cd9d-18b6-4c4a-b1ea-86dbab23fc79
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f08cc817fab6e81ae1160462c9b6d1221ca41160
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657874"
---
# <a name="visual-basic-defaults-projects-options-dialog-box"></a>Valores predeterminados de Visual Basic, Proyectos, Opciones (Cuadro de diálogo)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Especifica la configuración predeterminada de las opciones de proyecto de Visual Basic. Cuando se crea un proyecto, se agregarán las instrucciones de la opción especificada al encabezado del proyecto en el Editor de código. Las opciones se aplican a todos los proyectos de Visual Basic.

 Para obtener acceso a este cuadro de diálogo, en el menú **Herramientas**, haga clic en **Opciones**, expanda la carpeta **Proyectos y soluciones** y después haga clic en **Valores predeterminados de VB**.

 **Option Explicit** Establece el valor predeterminado del compilador para que se requieran declaraciones explícitas de variables. De forma predeterminada, **Option Explicit** está establecido en **On**. Para más información, vea [/optionexplicit](https://msdn.microsoft.com/library/5d296ab3-bafe-4c4d-9887-78f162ed86c7).

 **Option Strict** Establece el valor predeterminado del compilador para que se requieran las conversiones de restricción explícitas y no se permite el enlace en tiempo de ejecución. De forma predeterminada, **Option Strict** está establecido en **Off**. Para más información, vea [/optionstrict](https://msdn.microsoft.com/library/c7b10086-0fa4-49db-b3c8-4ae0db5957da).

 **Option Compare** Establece el valor predeterminado del compilador para las comparaciones de cadenas: binario (distingue mayúsculas de minúsculas) o texto (no distingue mayúsculas de minúsculas). De forma predeterminada, Option Compare está establecido en **Binary**. Para más información, vea [/optioncompare](https://msdn.microsoft.com/library/7237b766-b44d-4cc5-9a3c-885348a7d9e4).

 **Option Infer** Establece el valor predeterminado del compilador para la inferencia de tipo local. De forma predeterminada, **Option Infer** está establecido en **On** para los proyectos recién creados y en **Off** para los proyectos migrados creados en versiones anteriores de Visual Basic. Para más información, vea [/optioninfer](https://msdn.microsoft.com/library/f6c09db1-0553-464a-abe3-d4510c61d6ed).

## <a name="see-also"></a>Otras referencias
 [Soluciones y proyectos](../../ide/solutions-and-projects-in-visual-studio.md)
