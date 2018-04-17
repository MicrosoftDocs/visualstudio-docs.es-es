---
title: Guía básica para ampliar el depurador | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 46c5a8a995644d6876457836674152eb3b3ccad7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="roadmap-for-extending-the-debugger"></a>Guía básica para ampliar el depurador
Esta documentación proporciona información de referencia y la guía para extender la [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] del depurador con la [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] documentación sobre depuración incluye ejemplos, una referencia completa y varios escenarios representativos que muestran cómo personalizar al depurador de las maneras más comunes.  
  
 El compilador y su salida determinan lo que necesita hacer para implementar la depuración en su producto. Si el compilador:  
  
-   Tiene como destino el sistema operativo de Windows nativo y escribe un. Archivos PDB, puede depurar programas con el motor de depuración de código nativo (Alemania), que está integrado en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. No es necesario implementar un evaluador Alemania o una expresión. El evaluador de expresiones que se escribe para la sintaxis del lenguaje de programación C++.  
  
-   Genera Microsoft al lenguaje intermedio (MSIL) de salida, puede depurar programas con el motor de depuración de código administrado DE, que también se integra en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Por lo tanto, solo necesita implementar un evaluador de expresiones. Un evaluador de expresiones de ejemplo se proporciona automáticamente. Para obtener más información, vea los temas siguientes:  
  
     [Evaluación de expresiones](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
  
     [Evaluación de expresiones](../../extensibility/debugger/evaluating-expressions.md)  
  
     [Contexto de evaluación de expresiones](../../extensibility/debugger/expression-evaluation-context.md)  
  
     [Evaluación de expresiones en el modo de interrupción](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
     [Escritura de un evaluador de expresiones de Common Language Runtime](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
  
-   Destinos de un sistema operativo o algún otro entorno de tiempo de ejecución de propietario, tiene que escribir su propio Alemania. Se proporciona un tutorial que crea un sencillo DE usar COM de ATL. Para obtener más información, vea los temas siguientes:  
  
     [Creación de un motor de depuración personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
  
     [Tutorial: Creación de un motor de depuración mediante COM de ATL](http://msdn.microsoft.com/en-us/9097b71e-1fe7-48f7-bc00-009e25940c24)  
  
     [Implementación de un proveedor de puerto](../../extensibility/debugger/implementing-a-port-supplier.md)  
  
     [Ejemplos](../../extensibility/debugger/visual-studio-debugging-samples.md)  
  
## <a name="see-also"></a>Vea también  
 [Introducción](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)