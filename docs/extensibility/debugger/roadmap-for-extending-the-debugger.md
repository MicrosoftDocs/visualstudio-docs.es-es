---
title: Guía básica para ampliar el depurador | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 637452fe5b36860cd23385f4a041872ea9dfeb0f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55013475"
---
# <a name="roadmap-for-extending-the-debugger"></a>Guía básica para ampliar el depurador
Esta documentación proporciona información de referencia y la guía para extender la [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] del depurador con el [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] documentación sobre depuración incluye varios escenarios representativos que muestran formas habituales para personalizar al depurador, una referencia completa y ejemplos.  
  
 El compilador y su salida determinan requisitos necesarios para configurar la depuración en el producto. Si el compilador:  
  
- Tiene como destino el sistema operativo de Windows nativo y escribe un *. PDB* archivo, puede depurar programas con el motor de depuración de código nativo (DE), que está integrado en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. No es necesario implementar un evaluador DE o una expresión. El evaluador de expresiones se escribe para conocer la sintaxis del lenguaje de programación C++.  
  
- Genera el lenguaje intermedio (MSIL) de salida, puede depurar programas con el motor de depuración de código administrado DE, que también está integrado en el Microsoft [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Por lo tanto, sólo debe implementar un evaluador de expresiones. Un evaluador de expresiones de ejemplo se proporciona para usted. Para obtener más información, vea los temas siguientes:  
  
   [Evaluación de expresiones](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
  
   [Evaluación de expresiones](../../extensibility/debugger/evaluating-expressions.md)  
  
   [Contexto de evaluación de expresión](../../extensibility/debugger/expression-evaluation-context.md)  
  
   [Evaluación de expresiones en modo de interrupción](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
   [Escribir un evaluador de expresiones de common language runtime](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
  
- Destinos de una propiedad de sistema operativo o algún otro entorno de tiempo de ejecución, deberá escribir su propio DE. Se proporciona un tutorial que crea un sencillo DE usar COM de ATL. Para obtener más información, vea los temas siguientes:  
  
   [Crear un motor de depuración personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
  
   [Tutorial: Crear un motor de depuración mediante ATL COM](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24)  
  
   [Implementar un proveedor de puerto](../../extensibility/debugger/implementing-a-port-supplier.md)  
  
   [Muestras](../../extensibility/debugger/visual-studio-debugging-samples.md)  
  
## <a name="see-also"></a>Vea también  
 [Introducción](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)