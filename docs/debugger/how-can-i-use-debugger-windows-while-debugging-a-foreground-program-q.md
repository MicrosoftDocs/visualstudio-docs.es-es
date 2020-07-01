---
title: Empleo de ventanas del depurador mientras se depura una aplicación en primer plano | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.background
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- foreground program debugging
- remote debugging, debugging foreground programs
- debugging [Visual Studio], while observing foreground programs
- focus, debugging while observing foreground programs
- debugging [Visual Studio], foreground programs
ms.assetid: 9e67a308-1c81-42ab-966b-7fc3c1d2bf7a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1c74ca2c01f55778930e2cab1ccf38011bba868d
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2020
ms.locfileid: "85350334"
---
# <a name="how-can-i-use-debugger-windows-while-debugging-a-foreground-program"></a>Cómo utilizar ventanas del depurador mientras se depura un programa en primer plano
## <a name="problem-description"></a>Descripción del problema
 Estoy intentando depurar un problema de actualización de pantalla. Para observar este problema, debo mantener mi programa en primer plano, de modo que no tengo acceso a las ventanas de depuración. ¿Qué puedo hacer?

## <a name="solution"></a>Soluciones
 Si dispone de un segundo equipo, puede utilizar la función de depuración remota. Con un segundo equipo, puede observar la actualización de pantalla en el equipo remoto mientras ejecuta el depurador en el host. Para obtener más información sobre la depuración remota, vea [Depuración remota](../debugger/remote-debugging.md).

## <a name="see-also"></a>Vea también
- [Preguntas más frecuentes sobre la depuración de código nativo](../debugger/debugging-native-code-faqs.md)
- [Depuración de código nativo](../debugger/debugging-native-code.md)