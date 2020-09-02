---
title: Guía básica para extender el depurador | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 89a07bc5a5c4c8b7a6054b53610325c654355bc8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695960"
---
# <a name="roadmap-for-extending-the-debugger"></a>Guía básica para ampliar el depurador
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En esta documentación se proporciona información de referencia y guía para extender el [!INCLUDE[vs_current_short](../../includes/vs-current-short-md.md)] depurador con [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] .  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] la documentación de depuración incluye ejemplos, una referencia completa y varios escenarios representativos que muestran las formas típicas de personalizar el depurador.  
  
 El compilador y su salida determinan lo que debe hacer para implementar la depuración en el producto. Si el compilador:  
  
- Tiene como destino el sistema operativo nativo de Windows y escribe un. Archivo PDB, puede depurar programas con el motor DE depuración DE código nativo (DE), que está integrado en [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . No es necesario implementar un evaluador DE expresiones o. El evaluador de expresiones se escribe para la sintaxis del lenguaje de programación de C++.  
  
- Genera la salida del lenguaje intermedio DE Microsoft (MSIL), puede depurar programas con el motor DE depuración DE código administrado DE, que también está integrado en [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Por lo tanto, solo necesita implementar un evaluador de expresiones. Se proporciona un evaluador de expresiones de ejemplo. Para obtener más información, vea los temas siguientes:  
  
     [Evaluación de expresiones](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
  
     [Evaluar expresiones](../../extensibility/debugger/evaluating-expressions.md)  
  
     [Contexto de evaluación de expresiones](../../extensibility/debugger/expression-evaluation-context.md)  
  
     [Evaluación de expresiones en el modo de interrupción](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
     [Escritura de un evaluador de expresiones de Common Language Runtime](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
  
- Tiene como destino un sistema operativo propietario o algún otro entorno en tiempo de ejecución, debe escribir su propio. Se proporciona un tutorial que crea un sencillo DE mediante ATL COM. Para obtener más información, vea los temas siguientes:  
  
     [Creación de un motor de depuración personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
  
     [Tutorial: crear un motor de depuración mediante ATL COM](https://msdn.microsoft.com/9097b71e-1fe7-48f7-bc00-009e25940c24)  
  
     [Implementación de un proveedor de puerto](../../extensibility/debugger/implementing-a-port-supplier.md)  
  
     [Muestras](../../extensibility/debugger/visual-studio-debugging-samples.md)  
  
## <a name="see-also"></a>Consulte también  
 [Introducción](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
