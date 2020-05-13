---
title: Hoja de ruta para la ampliación del depurador Microsoft Docs
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
ms.openlocfilehash: e809eeb6a1a5d2c24368932713d69c7199b5af38
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713144"
---
# <a name="roadmap-for-extending-the-debugger"></a>Hoja de ruta para ampliar el depurador
Esta documentación proporciona información de [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] guía y [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]referencia para ampliar el depurador con el archivo .

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]la documentación de depuración incluye ejemplos, una referencia completa y varios escenarios representativos que muestran las formas típicas de personalizar el depurador.

 El compilador y su salida determinan lo que se necesita para configurar la depuración en el producto. Si el compilador:

- Tiene como destino el sistema operativo nativo de Windows y escribe un *archivo . PDB,* puede depurar programas con el motor de depuración [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]de código nativo (DE), que está integrado en . No es necesario implementar un evaluador de expresiones o DE. El evaluador de expresiones se escribe para la sintaxis del lenguaje de programación C++.

- Produce la salida del lenguaje intermedio de Microsoft (MSIL), puede depurar programas con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]el motor de depuración de código administrado DE, que también está integrado en . Por lo tanto, solo necesita implementar un evaluador de expresiones. Se proporciona un evaluador de expresiones de ejemplo. Para obtener más información, vea los temas siguientes:

   [Evaluación de expresiones](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)

   [Evaluación de expresiones](../../extensibility/debugger/evaluating-expressions.md)

   [Contexto de evaluación de expresiones](../../extensibility/debugger/expression-evaluation-context.md)

   [Evaluación de expresiones en modo de interrupción](../../extensibility/debugger/expression-evaluation-in-break-mode.md)

   [Escribir un evaluador de expresiones de Common Language Runtime](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)

- Se dirige a un sistema operativo propietario o a algún otro entorno en tiempo de ejecución, debe escribir su propio DE. Se proporciona un tutorial que crea un DE simple mediante ATL COM. Para obtener más información, vea los temas siguientes:

   [Crear un motor de depuración personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)

   [Tutorial: Cree un motor de depuración con ATL COM](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24)

   [Implementar un proveedor portuario](../../extensibility/debugger/implementing-a-port-supplier.md)

   [Muestras](../../extensibility/debugger/visual-studio-debugging-samples.md)

## <a name="see-also"></a>Vea también
- [Introducción](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
