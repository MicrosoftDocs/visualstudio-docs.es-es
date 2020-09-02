---
title: Enrutamiento de mensajes a la ventana Salida | Microsoft Docs
ms.date: 11/08/2018
ms.topic: how-to
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
ms.openlocfilehash: 85d3c146775ac06b3118186738ee74932a4c452a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85350477"
---
# <a name="send-messages-to-the-output-window"></a>Enrutamiento de mensajes a la ventana Salida

Puede escribir mensajes en tiempo de ejecución en la ventana **Salida** mediante las clases <xref:System.Diagnostics.Debug> o <xref:System.Diagnostics.Trace>, que forman parte de la biblioteca de clases <xref:System.Diagnostics>. Utilice la clase <xref:System.Diagnostics.Debug> si solo quiere resultados en la versión de *depuración* del programa. Utilice la clase <xref:System.Diagnostics.Trace> si quiere generar resultados en las versiones de *depuración* y *lanzamiento*.

## <a name="output-methods"></a>Métodos de salida
 Las clases <xref:System.Diagnostics.Trace> y <xref:System.Diagnostics.Debug> proporcionan los siguientes métodos de salida:

- Diversos métodos `Write`, que envían información sin interrumpir la ejecución. Estos métodos reemplazan el método `Debug.Print` que se utilizaba en versiones anteriores de Visual Basic.

- Los métodos <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> y <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>, que interrumpen la ejecución y envían información si se produce un error en una condición especificada. De forma predeterminada, el método `Assert` muestra la información en un cuadro de diálogo. Para obtener más información, vea [Aserciones en el código administrado](../debugger/assertions-in-managed-code.md).

- Los métodos <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=fullName> y <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=fullName>, que interrumpen siempre la ejecución y envían información. De forma predeterminada, el método `Fail` muestra la información en un cuadro de diálogo.

La ventana **Salida** también puede mostrar información sobre lo siguiente:

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
