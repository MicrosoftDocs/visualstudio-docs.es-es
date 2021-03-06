---
title: Compatibilidad del servicio de lenguaje para la depuración | Microsoft Docs
description: Obtenga información sobre las características del servicio de lenguaje de la interfaz IVsLanguageDebugInfo que proporcionan compatibilidad para la depuración en Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugger, language support
- language services, debugging support
ms.assetid: 7a44067f-a410-4a6a-84d2-bda5184140bc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2c00d0af21d5d165b7733267e0a97ae71ca6e573
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074579"
---
# <a name="language-service-support-for-debugging"></a>Compatibilidad del servicio de lenguaje con la depuración
Un servicio de lenguaje puede proporcionar características que admiten un depurador a través de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo> interfaz. Estas características incluyen la validación de puntos de interrupción y la especificación de una lista de expresiones en la ventana **automático** .

 Sin embargo, debe tener un evaluador de expresiones para depurar el lenguaje. El evaluador de expresiones es responsable de evaluar las expresiones para generar valores durante la depuración. Para obtener información sobre cómo implementar evaluadores de expresiones CLR, vea:

- [Evaluadores de expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)

- [Ejemplo de evaluador de expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

## <a name="compiler-output"></a>Salida del compilador
 El tipo de compilador determina lo que debe hacer para implementar la depuración para su lenguaje. Si el compilador tiene como destino el sistema operativo Windows y escribe un archivo. pdb, puede depurar programas con el motor de depuración de código nativo que está integrado en Visual Studio. Si el compilador genera lenguaje intermedio de Microsoft (MSIL), puede depurar programas con el motor de depuración de código administrado, que también está integrado en Visual Studio. Si el compilador tiene como destino un sistema operativo propietario o un entorno de tiempo de ejecución diferente, debe escribir su propio motor de depuración.

 Para obtener más información sobre cómo implementar la depuración para su lenguaje, vea [Introducción](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) en el SDK de depuración de Visual Studio.
