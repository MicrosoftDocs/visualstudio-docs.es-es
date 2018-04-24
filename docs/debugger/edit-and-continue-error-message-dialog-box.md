---
title: Editar y continuar en el cuadro de diálogo de mensaje de Error | Documentos de Microsoft
ms.custom: ''
ms.date: 06/22/2017
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.ENC.SupportedButNotAvaiable
- vs.debug.ENC.CannotEditWhileException
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue Error Message dialog box
ms.assetid: f98c91c0-447a-4533-85b6-87170a0dc4c3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5b521eafcc62a49f2dd2a4c327158070bdbe62ce
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
---
# <a name="edit-and-continue-error-message-dialog-box"></a>Editar y continuar (Cuadro de diálogo de mensaje de error)
Este cuadro de diálogo aparece cuando se depura en un lenguaje que admite Editar y continuar, pero **editar y continuar** no está disponible para el tipo de cambios de código realizados. El mensaje de error incluido en el cuadro proporciona una explicación más detallada. Entre las posibles razones para que aparezca este cuadro de diálogo se incluyen:  

-   Se intentó editar código de SQL Server.

-   Se intentó editar código optimizado. (Puede que tenga cambiar de una versión de lanzamiento a una versión de depuración).

-   Se intentó editar código mientras se estaba ejecutando (en lugar de mientras está en pausa en el depurador). Intente [establecer un punto de interrupción](../debugger/using-breakpoints.md) y editar código mientras está en pausa.

-   Se intentó editar código administrado cuando estaba habilitada la depuración no administrada. Editar y continuar no funciona con [depuración en modo mixto](../debugger/how-to-debug-in-mixed-mode.md).

-   Realizó un código de cambio que no es compatible con Editar y continuar en el lenguaje de programación. Para obtener más información, vea temas para cambios de códigos no admitida en [C#](../debugger/supported-code-changes-csharp.md), [Visual Basic](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md), y [C++](../debugger/supported-code-changes-cpp.md).
  
-   Se intentó editar código en un programa que se asoció, en lugar de a partir de la **depurar** menú.  
  
-   Se intentó editar código mientras se depuraba un volcado de memoria de Dr. Volcado de memoria de Watson.  
  
-   Se intentó editar código después de que se produjo una excepción no controlada y la opción "**desenredar la pila de llamadas de las excepciones no controladas**" no se seleccionó.  
  
-   Se intentó editar código mientras se depuraba una aplicación incrustada en tiempo de ejecución.
  
-   Se intentó editar código administrado mediante la versión de .NET Framework anterior a 4.5.1 y el destino es una aplicación de 64 bits. Si desea utilizar la opción Editar y continuar, deberá establecer el destino en x86. (*projectname* **propiedades**, **compilar** ficha, **compilador avanzada** configuración.).  
  
-   Se intentó editar código en un ensamblado que se modificó durante la depuración y se ha vuelto ha cargar.  
  
-   Se intentó editar código en un ensamblado que no se ha cargado.  
  
-   Se inició la depuración de una versión anterior de la aplicación (ya que la nueva versión tenía errores de compilación).
  
## <a name="uielement-list"></a>Lista de UIElement  
 **VALE**  
 Sale del cuadro de diálogo y cancela el intento de edición inmediatamente anterior.  
  
## <a name="see-also"></a>Vea también  
 [C++ editar y continuar blog post](https://blogs.msdn.microsoft.com/vcblog/2016/07/01/c-edit-and-continue-in-visual-studio-2015-update-3/)  
 [Cambios admitidos en el código (C++)](../debugger/supported-code-changes-cpp.md)