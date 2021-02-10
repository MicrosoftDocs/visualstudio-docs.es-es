---
title: Empleo de ventanas del depurador mientras se depura una aplicación en primer plano | Microsoft Docs
Description: Si va a depurar un programa que debe permanecer en primer plano, use la depuración remota para evitar ponerlo en segundo plano.
ms.custom: SEO-VS-2020, seodec18
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 420a4073e4c00f66775bf55565c2ee8645d90f49
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99911375"
---
# <a name="how-can-i-use-debugger-windows-while-debugging-a-foreground-program"></a>Cómo utilizar ventanas del depurador mientras se depura un programa en primer plano
## <a name="problem-description"></a>Descripción del problema
 Estoy intentando depurar un problema de actualización de pantalla. Para observar este problema, debo mantener mi programa en primer plano, de modo que no tengo acceso a las ventanas de depuración. ¿Qué puedo hacer?

## <a name="solution"></a>Soluciones
 Si dispone de un segundo equipo, puede utilizar la función de depuración remota. Con un segundo equipo, puede observar la actualización de pantalla en el equipo remoto mientras ejecuta el depurador en el host. Para obtener más información sobre la depuración remota, vea [Depuración remota](../debugger/remote-debugging.md).

## <a name="see-also"></a>Vea también
- [Preguntas más frecuentes sobre la depuración de código nativo](../debugger/debugging-native-code-faqs.md)
- [Depuración de código nativo](../debugger/debugging-native-code.md)