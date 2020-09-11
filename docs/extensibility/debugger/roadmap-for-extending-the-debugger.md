---
title: Guía básica para extender el depurador | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9d97a7edd62540d12a0a60d15b3179ca0a623c26
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2020
ms.locfileid: "90011832"
---
# <a name="roadmap-for-extending-the-debugger"></a>Guía básica para extender el depurador
En esta documentación se proporciona información de referencia y guía para extender el [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] depurador con [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] .

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] la documentación de depuración incluye ejemplos, una referencia completa y varios escenarios representativos que muestran las formas típicas de personalizar el depurador.

 El compilador y su salida determinan lo que se necesita para configurar la depuración en el producto. Si el compilador:

- Tiene como destino el sistema operativo nativo de Windows y escribe un *. Archivo PDB* , puede depurar programas con el motor de depuración de código nativo (de), que está integrado en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . No es necesario implementar un evaluador DE expresiones o. El evaluador de expresiones se escribe para la sintaxis del lenguaje de programación de C++.

- Genera la salida del lenguaje intermedio DE Microsoft (MSIL), puede depurar programas con el motor DE depuración DE código administrado DE, que también está integrado en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Por lo tanto, solo necesita implementar un evaluador de expresiones. Se proporciona un evaluador de expresiones de ejemplo. Para obtener más información, vea los temas siguientes:

   [Evaluación de expresiones](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)

   [Evaluar expresiones](../../extensibility/debugger/evaluating-expressions.md)

   [Contexto de evaluación de expresiones](../../extensibility/debugger/expression-evaluation-context.md)

   [Evaluación de expresiones en modo de interrupción](../../extensibility/debugger/expression-evaluation-in-break-mode.md)

   [Escribir un evaluador de expresiones de Common Language Runtime](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)

- Tiene como destino un sistema operativo propietario o algún otro entorno en tiempo de ejecución, debe escribir su propio. Se proporciona un tutorial que crea un sencillo DE mediante ATL COM. Para obtener más información, vea los temas siguientes:

   [Crear un motor de depuración personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)

   [Tutorial: compilar un motor de depuración mediante ATL COM](/previous-versions/bb147024(v=vs.90))

   [Implementación de un proveedor de Puerto](../../extensibility/debugger/implementing-a-port-supplier.md)

   [Ejemplos](../../extensibility/debugger/visual-studio-debugging-samples.md)

## <a name="see-also"></a>Consulte también
- [Introducción](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)