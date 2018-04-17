---
title: Compatibilidad de servicio de lenguaje para depurar | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugger, language support
- language services, debugging support
ms.assetid: 7a44067f-a410-4a6a-84d2-bda5184140bc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 59c044f6ffc3f2cdf0749f0192f4b8fa458b00cc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="language-service-support-for-debugging"></a>Soporte de servicio de lenguaje para la depuración
Un servicio de lenguaje puede incluir características que admiten un depurador a través de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo> interfaz. Estas características incluyen la validación de los puntos de interrupción y proporcionar una lista de expresiones para la **automático** ventana.  
  
 Sin embargo, debe tener un evaluador de expresiones para depurar su idioma. El evaluador de expresiones es responsable de evaluar expresiones para generar valores durante la depuración. Para obtener información acerca de cómo implementar los evaluadores de expresión de CLR, vea:  
  
-   [Evaluadores de expresión de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)  
  
-   [Ejemplo de evaluador de expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)  
  
## <a name="compiler-output"></a>Resultado de compilación  
 El tipo de compilador determina lo que necesita hacer para implementar la depuración en su idioma. Si el compilador tiene como destino el sistema operativo Windows y escribe un archivo .pdb, puede depurar programas con el motor que está integrado en Visual Studio de depuración de código nativo. Si el compilador genera el lenguaje intermedio de Microsoft (MSIL), puede depurar programas con el motor, que también está integrada en Visual Studio de depuración de código administrado. Si el compilador tiene como destino un sistema operativo patentado o un entorno de tiempo de ejecución diferente, tiene que escribir su propio motor de depuración.  
  
 Para obtener más información sobre cómo implementar la depuración en su idioma, consulte [Introducción](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) en el SDK de depuración de Visual Studio.