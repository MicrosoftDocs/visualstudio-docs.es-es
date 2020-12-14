---
title: Editar y continuar (Cuadro de diálogo de mensaje de error)| Microsoft Docs
description: Editar y continuar puede notificar que no está disponible para los cambios del código. En este artículo se proporcionan los posibles motivos.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 8ef34889b838e2f7eaa92420eec90db9def57e65
ms.sourcegitcommit: 47da50a74fcd3db66d97cb20accac983bc41912f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/08/2020
ms.locfileid: "96862852"
---
# <a name="edit-and-continue-error-message"></a>Editar y continuar (Mensaje de error)

El cuadro de diálogo **Editar y continuar** aparece cuando se depura en un lenguaje de código que admite Editar y continuar, pero Editar y continuar no está disponible para los cambios de código realizados. El mensaje de error proporciona una explicación más detallada. Para responder al cuadro de diálogo, seleccione **Aceptar** para cerrarlo y cancelar el intento de edición.

Las posibles razones de este mensaje de error incluyen:

- Intentar editar código de SQL Server.
- Intentar editar código optimizado. Es posible que deba cambiar de una compilación de versión a una de depuración.
- Intentar editar código mientras se está ejecutando, en lugar de mientras está en pausa en el depurador. Intentar [establecer un punto de interrupción](../debugger/using-breakpoints.md) y editar el código mientras está en pausa.
- Intentar editar código administrado cuando solo está habilitada la depuración no administrada. Editar y continuar no funciona con la [depuración en modo mixto](../debugger/how-to-debug-in-mixed-mode.md).
- Realizar un cambio de código que Editar y continuar no admite en el lenguaje de programación. Para obtener más información, vea los artículos sobre [cambios de código admitidos en C#](supported-code-changes-csharp.md), [cambios no admitidos en Editar y continuar de Visual Basic](supported-code-changes-csharp.md) y [cambios admitidos en el código de C++](supported-code-changes-cpp.md).
- Intentar editar el código en una aplicación a la que se ha asociado, en lugar de iniciar la depuración desde el menú **Depurar**.
- Intentar editar código mientras se depura un volcado de Dr. Watson.
- Intentar editar código después de una excepción no controlada y con la opción **Desenredar la pila de llamadas de las excepciones no controladas** sin seleccionar.
- Intentar editar código mientras se depura una aplicación insertada en tiempo de ejecución.
- Intentar editar código administrado con una versión de .NET Framework anterior a la 4.5.1 con un destino de aplicación de 64 bits. Para usar Editar y continuar para .NET Framework anterior a 4.5.1, establezca el destino en **x86** en la pestaña **\<ProjectName>**  > **Propiedades** > **Compilar**, **Configuración avanzada del compilador**.
- Intentar editar código en un ensamblado que se ha modificado durante la depuración y se ha vuelto a cargar.
- Intentar editar código en un ensamblado que no se ha cargado.
- Iniciar la depuración de una versión antigua de una aplicación, ya que la más reciente tiene errores de compilación.

Para obtener más información, consulte:
- [Entrada de blog sobre Editar y continuar de C++](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/)
- [Cambios admitidos en el código (C++)](../debugger/supported-code-changes-cpp.md)
- [Editar y continuar](../debugger/edit-and-continue.md)