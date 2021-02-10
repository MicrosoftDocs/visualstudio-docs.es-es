---
title: Depuración de infracciones de acceso al ejecutar una aplicación fuera de Visual Studio
titleSuffix: ''
description: Use el depurador Just-in-Time para depurar una infracción de acceso producida fuera del entorno de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: dd4709807b176806d8a7ca56de4adda8cdfe13ec
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99904329"
---
# <a name="how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger"></a>Cómo depurar las infracciones de acceso cuando se ejecuta un programa fuera del depurador

## <a name="problem-description"></a>Descripción del problema
 El programa funciona bien en el entorno de Visual Studio, pero cuando se ejecuta de forma independiente en el sistema operativo Windows, produce una infracción de acceso. ¿Cómo se puede depurar este problema?

## <a name="solution"></a>Soluciones
 Establezca la opción [Depuración Just-In-Time](../debugger/just-in-time-debugging-in-visual-studio.md) y ejecute el programa de forma independiente hasta que se produzca la infracción de acceso. A continuación, en el cuadro de diálogo **Infracción de acceso**, se puede hacer clic en **Cancelar** para iniciar el depurador.

## <a name="see-also"></a>Vea también
- [Preguntas más frecuentes sobre la depuración de código nativo](../debugger/debugging-native-code-faqs.md)
- [Depuración de código nativo](../debugger/debugging-native-code.md)