---
title: Soporte técnico de servicio de lenguaje para la depuración | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugger, language support
- language services, debugging support
ms.assetid: 7a44067f-a410-4a6a-84d2-bda5184140bc
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c61f7fa7e698e2c01cadb1dbb36a321c6e656e35
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60089190"
---
# <a name="language-service-support-for-debugging"></a>Compatibilidad del servicio de lenguaje con la depuración
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un servicio de lenguaje puede proporcionar características que admiten un depurador a través de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo> interfaz. Estas características incluyen la validación de los puntos de interrupción y proporcionar una lista de expresiones para la **automático** ventana.  
  
 Sin embargo, deberá tener un evaluador de expresiones para depurar su idioma. El evaluador de expresiones es responsable de evaluar expresiones para generar valores durante la depuración. Para obtener información sobre la implementación de evaluadores de expresión de CLR, vea:  
  
- [Evaluadores de expresión de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)  
  
- [Ejemplo de evaluador de expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)  
  
## <a name="compiler-output"></a>Resultado de compilación  
 El tipo de compilador determina lo que necesita hacer para implementar la depuración para su idioma. Si el compilador tiene como destino el sistema operativo de Windows y escribe un archivo .pdb, puede depurar programas con el motor que está integrado en Visual Studio de depuración de código nativo. Si el compilador genera el lenguaje intermedio de Microsoft (MSIL), puede depurar programas con el motor, que también está integrada en Visual Studio de depuración de código administrado. Si el compilador tiene como destino un sistema operativo de propietario o un entorno de tiempo de ejecución diferente, deberá escribir su propio motor de depuración.  
  
 Para obtener más información sobre la implementación de depuración para su idioma, consulte [Introducción](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) en el SDK de depuración de Visual Studio.
