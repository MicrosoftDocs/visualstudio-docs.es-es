---
title: Cuadro de diálogo Editar y continuar mensaje de error | Microsoft Docs
ms.date: 10/15/2018
ms.topic: reference
f1_keywords:
- vs.debug.ENC.SupportedButNotAvailable
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7df95eae689f7c3abbb0d75a7557ce749bdceee5
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2019
ms.locfileid: "73188225"
---
# <a name="edit-and-continue-error-message"></a>Mensaje de error de editar y continuar

El cuadro de mensaje de error **Editar y continuar** aparece al depurar en un lenguaje de código que admite editar y continuar, pero editar y continuar no está disponible para los cambios de código realizados. El mensaje de error proporciona una explicación más detallada. Para responder al cuadro de diálogo, seleccione **Aceptar** para cerrar el cuadro de diálogo y cancelar el intento de edición.

Las posibles razones de este mensaje de error son:

- Intentando editar el código de SQL Server.
- Intentando editar el código optimizado. Es posible que deba cambiar de una versión de lanzamiento a una compilación de depuración.
- Se está intentando editar el código mientras se está ejecutando, en lugar de en pausa en el depurador. Pruebe [a establecer un punto de interrupción](../debugger/using-breakpoints.md)y a editar el código mientras está en pausa.
- Se está intentando editar el código administrado cuando solo está habilitada la depuración no administrada. Editar y continuar no funciona con [la depuración en modo mixto](../debugger/how-to-debug-in-mixed-mode.md).
- Realización de un cambio de código que no es compatible con editar y continuar en el lenguaje de programación. Para obtener más información, consulte los artículos sobre [los cambios C#de código admitidos en ](supported-code-changes-csharp.md), [ediciones no compatibles en Visual Basic editar y continuar](supported-code-changes-csharp.md)y [los cambios de código admitidos C++ ](supported-code-changes-cpp.md).
- Se está intentando editar el código en una aplicación a la que se ha adjuntado, en lugar de iniciar la depuración desde el menú **depurar** .
- Se está intentando editar código durante la depuración de un volcado de Dr. Watson.
- Al intentar editar el código después de que se produzca una excepción no controlada, no se selecciona la opción **desenredar la pila de llamadas de las excepciones no controladas** .
- Se está intentando editar código mientras se depura una aplicación en tiempo de ejecución incrustada.
- Se está intentando editar el código administrado con una versión de .NET Framework anterior a la 4.5.1 con un destino de aplicación de 64 bits. Para usar editar y continuar para .NET Framework anterior a 4.5.1, establezca el destino en **x86** en la **\<nombreDeProyecto >**  > **propiedades** > pestaña **compilar** , configuración **avanzada del compilador** .
- Se está intentando editar el código de un ensamblado que se modificó durante la depuración y se ha recargado.
- Intentando editar el código de un ensamblado que no se ha cargado.
- Iniciar la depuración de una versión anterior de una aplicación, ya que la última versión tiene errores de compilación.

Para obtener más información, consulte:
- [C++Publicación de blog editar y continuar](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/)
- [Cambios admitidos en el código (C++)](../debugger/supported-code-changes-cpp.md)
- [Editar y continuar](../debugger/edit-and-continue.md)