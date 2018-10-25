---
title: Editar y continuar en el cuadro de diálogo de mensaje de error | Microsoft Docs
ms.custom: ''
ms.date: 06/22/2018
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
ms.openlocfilehash: 5fd4fe31996a75c4b743f3dac12e7b945c912506
ms.sourcegitcommit: c5e72875206b8c5737c29d5b1ec7b86eec747303
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/17/2018
ms.locfileid: "49382797"
---
# <a name="edit-and-continue-error-message"></a>Editar y continuar el mensaje de error 

El **editar y continuar** aparece el cuadro de mensaje de error cuando se depura en un lenguaje de código que admite Editar y continuar, pero Editar y continuar no está disponible para los cambios de código realizados. El mensaje de error proporciona una explicación más detallada. Para responder al cuadro de diálogo, seleccione **Aceptar** para cerrar el cuadro de diálogo y cancelar el intento de edición.  

Las posibles razones para este mensaje de error incluyen:  

-   Se está intentando editar código de SQL Server.
-   Se está intentando editar código optimizado. Es posible que deba cambiar de una versión de lanzamiento a una compilación de depuración.
-   Si intenta modificar el código mientras se está ejecutando, en lugar de mientras está en pausa en el depurador. Pruebe [establecer un punto de interrupción](../debugger/using-breakpoints.md)y editar el código mientras está en pausa.
-   Se está intentando editar código administrado cuando está habilitada la depuración solo no administrado. Editar y continuar no funciona con [depuración en modo mixto](../debugger/how-to-debug-in-mixed-mode.md).
-   Por lo que un código de cambio que no es compatible con Editar y continuar en el lenguaje de programación. Para obtener más información, consulte los artículos [admite cambios de código en C# ](supported-code-changes-csharp.md), [no admite la edición de Visual Basic editar y continuar](unsupported-edits-in-visual-basic-edit-and-continue.md), y [admite cambios en el código C++](supported-code-changes-cpp.md).
-   Si intenta modificar el código en una aplicación que está conectado, en lugar de iniciar la depuración desde el **depurar** menú.  
-   Se está intentando editar código mientras se depuraba una recuperación ante desastres. Volcado de memoria de Watson.  
-   Si intenta modificar el código después de que se produce una excepción no controlada y la opción **desenredar la pila de llamadas en las excepciones no controladas** no está seleccionada.  
-   Se está intentando editar código mientras se depura una aplicación incrustada en tiempo de ejecución.
-   Se está intentando editar código administrado mediante una versión de .NET Framework anteriores a 4.5.1 con un objetivo de la aplicación de 64 bits. Para utilizar editar y continuar para .NET Framework anteriores a 4.5.1, establezca el destino en **x86** en el  **\<NombreDelProyecto >** > **propiedades**  >  **Compilar** ficha, **compilador avanzada** configuración.  
-   Se está intentando editar código en un ensamblado que se modificó durante la depuración y se volvió a cargar.  
-   Se está intentando editar código en un ensamblado que no se ha cargado.  
-   Comenzar a depurar una versión anterior de una aplicación, porque la versión más reciente tiene errores de compilación.
  
Para obtener más información, consulte:
- [C++ editar y continuar blog post](https://blogs.msdn.microsoft.com/vcblog/2016/07/01/c-edit-and-continue-in-visual-studio-2015-update-3/)  
- [Admite los cambios de código (C++)](../debugger/supported-code-changes-cpp.md)
- [Editar y continuar](../debugger/edit-and-continue.md)