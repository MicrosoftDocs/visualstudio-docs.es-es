---
title: Enviar mensajes a la ventana de salida | Microsoft Docs
ms.date: 11/08/2018
ms.topic: conceptual
helpviewer_keywords:
- diagnostic messages [C#]
- System.Diagnostics.Debug class, Output window
- messages, diagnostic
- Debug.Print replacements
- diagnosis
- Output window, diagnostic messages
- System.Diagnostics.Trace class, Output window
- Trace class, diagnostic messages
- diagnostics
- debugger, Output window
- debugging [Visual Studio], diagnostic messages in Output window
- Debug class
ms.assetid: 386e9524-be17-4573-83fb-4f7c5cae0be0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 47b563f58d08a732ec224bb8bbf47ad807c4e81d
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/29/2019
ms.locfileid: "68605377"
---
# <a name="send-messages-to-the-output-window"></a>Enrutamiento de mensajes a la ventana Salida

Puede escribir mensajes en tiempo de ejecución en la ventana de **salida** mediante <xref:System.Diagnostics.Debug> la clase o <xref:System.Diagnostics.Trace> la clase, que forman parte de <xref:System.Diagnostics> la biblioteca de clases. Utilice la <xref:System.Diagnostics.Debug> clase si solo desea la salida en la  versión de depuración del programa. Utilice la <xref:System.Diagnostics.Trace> clase si desea generar la salida en las versiones de depuración y *lanzamiento* .

## <a name="output-methods"></a>Métodos de salida
 Las clases <xref:System.Diagnostics.Trace> y <xref:System.Diagnostics.Debug> proporcionan los siguientes métodos de salida:

- Diversos métodos `Write`, que envían información sin interrumpir la ejecución. Estos métodos reemplazan el método `Debug.Print` que se utilizaba en versiones anteriores de Visual Basic.

- <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>los <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> métodos y, que interrumpen la información de ejecución y salida si se produce un error en una condición especificada. De forma predeterminada, el método `Assert` muestra la información en un cuadro de diálogo. Para obtener más información, vea [Aserciones en el código administrado](../debugger/assertions-in-managed-code.md).

- Los <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=fullName> métodos <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=fullName> y, que siempre interrumpen la información de ejecución y salida. De forma predeterminada, el método `Fail` muestra la información en un cuadro de diálogo.

La ventana de **salida** también puede mostrar información acerca de:

- Módulos que el depurador ha cargado o ha descargado.

- Excepciones que se producen.

- Procesos que salen.

- Subprocesos que salen.

## <a name="see-also"></a>Vea también
- [Seguridad del depurador](../debugger/debugger-security.md)
- [Resultados (Ventana)](../ide/reference/output-window.md)
- [Seguimiento e instrumentación de aplicaciones](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)
- [Tipos de proyectos de C#, F# y Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Depurar código administrado](../debugger/debugging-managed-code.md)
