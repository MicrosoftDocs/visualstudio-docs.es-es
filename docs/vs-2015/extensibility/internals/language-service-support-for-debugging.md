---
title: Soporte técnico de servicio de lenguaje para la depuración | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugger, language support
- language services, debugging support
ms.assetid: 7a44067f-a410-4a6a-84d2-bda5184140bc
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a568ef30a26ad198d839ddcde257fec3036cf3c5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49173711"
---
# <a name="language-service-support-for-debugging"></a>Compatibilidad del servicio de lenguaje con la depuración
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un servicio de lenguaje puede proporcionar características que admiten un depurador a través de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo> interfaz. Estas características incluyen la validación de los puntos de interrupción y proporcionar una lista de expresiones para la **automático** ventana.  
  
 Sin embargo, deberá tener un evaluador de expresiones para depurar su idioma. El evaluador de expresiones es responsable de evaluar expresiones para generar valores durante la depuración. Para obtener información sobre la implementación de evaluadores de expresión de CLR, vea:  
  
-   [Evaluadores de expresión de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)  
  
-   [Ejemplo de evaluador de expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)  
  
## <a name="compiler-output"></a>Resultado de compilación  
 El tipo de compilador determina lo que necesita hacer para implementar la depuración para su idioma. Si el compilador tiene como destino el sistema operativo de Windows y escribe un archivo .pdb, puede depurar programas con el motor que está integrado en Visual Studio de depuración de código nativo. Si el compilador genera el lenguaje intermedio de Microsoft (MSIL), puede depurar programas con el motor, que también está integrada en Visual Studio de depuración de código administrado. Si el compilador tiene como destino un sistema operativo de propietario o un entorno de tiempo de ejecución diferente, deberá escribir su propio motor de depuración.  
  
 Para obtener más información sobre la implementación de depuración para su idioma, consulte [Introducción](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) en el SDK de depuración de Visual Studio.

