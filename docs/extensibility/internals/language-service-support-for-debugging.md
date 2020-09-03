---
title: Compatibilidad del servicio de lenguaje para la depuración | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugger, language support
- language services, debugging support
ms.assetid: 7a44067f-a410-4a6a-84d2-bda5184140bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8c80e8e1f584b1728f342cb596b689f6a22c9297
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80707430"
---
# <a name="language-service-support-for-debugging"></a>Compatibilidad del servicio de lenguaje con la depuración
Un servicio de lenguaje puede proporcionar características que admiten un depurador a través de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo> interfaz. Estas características incluyen la validación de puntos de interrupción y la especificación de una lista de expresiones en la ventana **automático** .

 Sin embargo, debe tener un evaluador de expresiones para depurar el lenguaje. El evaluador de expresiones es responsable de evaluar las expresiones para generar valores durante la depuración. Para obtener información sobre cómo implementar evaluadores de expresiones CLR, vea:

- [Evaluadores de expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)

- [Ejemplo de evaluador de expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

## <a name="compiler-output"></a>Salida del compilador
 El tipo de compilador determina lo que debe hacer para implementar la depuración para su lenguaje. Si el compilador tiene como destino el sistema operativo Windows y escribe un archivo. pdb, puede depurar programas con el motor de depuración de código nativo que está integrado en Visual Studio. Si el compilador genera lenguaje intermedio de Microsoft (MSIL), puede depurar programas con el motor de depuración de código administrado, que también está integrado en Visual Studio. Si el compilador tiene como destino un sistema operativo propietario o un entorno de tiempo de ejecución diferente, debe escribir su propio motor de depuración.

 Para obtener más información sobre cómo implementar la depuración para su lenguaje, vea [Introducción](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) en el SDK de depuración de Visual Studio.
