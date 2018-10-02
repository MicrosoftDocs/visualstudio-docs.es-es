---
title: Mensajes de diagnóstico en la ventana de salida | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.output
dev_langs:
- FSharp
- VB
- CSharp
- C++
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
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0a9e0bb4fa34133937e39b310cb05360e66a443
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47581293"
---
# <a name="diagnostic-messages-in-the-output-window"></a>Mensajes de diagnóstico en la ventana de resultados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [mensajes de diagnóstico en la ventana de salida](https://docs.microsoft.com/visualstudio/debugger/diagnostic-messages-in-the-output-window).  
  
Puede escribir mensajes en tiempo de ejecución en la Ventana de salida mediante la clase Debug o la clase Trace, que forman parte de la biblioteca de clases <xref:System.Diagnostics>. Utilice la clase Debug si sólo genera resultados en la versión de depuración del programa. Utilice la clase Trace si desea generar resultados en las versiones de depuración y de lanzamiento.  
  
## <a name="output-methods"></a>Métodos de salida  
 Las clases <xref:System.Diagnostics.Trace> y <xref:System.Diagnostics.Debug> proporcionan los siguientes métodos de salida:  
  
-   Diversos métodos `Write`, que envían información sin interrumpir la ejecución. Estos métodos reemplazan el método `Debug.Print` que se utilizaba en versiones anteriores de Visual Basic.  
  
-   Los métodos <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> y <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>, que interrumpen la ejecución y envían información si se produce un error en una condición especificada. De forma predeterminada, el método `Assert` muestra la información en un cuadro de diálogo. Para obtener más información, consulte [aserciones en el código administrado](../debugger/assertions-in-managed-code.md).  
  
-   Los métodos <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=fullName> y <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=fullName>, que interrumpen siempre la ejecución y envían información. De forma predeterminada, el método `Fail` muestra la información en un cuadro de diálogo.  
  
 Además del programa fuera de la aplicación, el **salida** ventana puede mostrar información acerca de:  
  
-   Módulos que el depurador ha cargado o ha descargado.  
  
-   Excepciones que se producen.  
  
-   Procesos que salen.  
  
-   Subprocesos que salen.  
  
## <a name="see-also"></a>Vea también  
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Ventana de salida](../ide/reference/output-window.md)   
 [Seguimiento e instrumentación de aplicaciones](http://msdn.microsoft.com/library/773b6fc4-9013-4322-b728-5dec7a72e743)   
 [Introducción a la instrumentación y el seguimiento](http://msdn.microsoft.com/en-us/e924e57c-33cf-4b0e-9e7f-a45d13e38f2c)   
 [Tipos de proyectos de C#, F# y Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Depurar código administrado](../debugger/debugging-managed-code.md)



