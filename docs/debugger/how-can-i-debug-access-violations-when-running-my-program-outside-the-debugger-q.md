---
title: Depurar las infracciones de acceso cuando se ejecuta la aplicación fuera del depurador
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.access
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 780a298a-132e-4245-8370-8c82ca27c6c1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d42dd206117885a23a6c1c15c712be4dc4cd8fe2
ms.sourcegitcommit: 13ab9a5ab039b070b9cd9251d0b83dd216477203
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/23/2019
ms.locfileid: "66177663"
---
# <a name="how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger"></a>Cómo depurar las infracciones de acceso cuando se ejecuta un programa fuera del depurador

## <a name="problem-description"></a>Descripción del problema
 El programa funciona bien en el entorno de Visual Studio, pero cuando se ejecuta de forma independiente en el sistema operativo Windows, produce una infracción de acceso. ¿Cómo se puede depurar este problema?

## <a name="solution"></a>Soluciones
 Establezca la opción [Depuración Just-In-Time](../debugger/just-in-time-debugging-in-visual-studio.md) y ejecute el programa de forma independiente hasta que se produzca la infracción de acceso. A continuación, en el cuadro de diálogo **Infracción de acceso**, se puede hacer clic en **Cancelar** para iniciar el depurador.

## <a name="see-also"></a>Vea también
- [Preguntas más frecuentes sobre la depuración de código nativo](../debugger/debugging-native-code-faqs.md)
- [Depuración de código nativo](../debugger/debugging-native-code.md)