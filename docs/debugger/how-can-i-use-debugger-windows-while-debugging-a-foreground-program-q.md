---
title: Usar ventanas del depurador mientras se depura una aplicación de primer plano | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 11bd61cda8c92721fb42c640b0b5100b8054acdf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62894871"
---
# <a name="how-can-i-use-debugger-windows-while-debugging-a-foreground-program"></a>Cómo utilizar ventanas del depurador mientras se depura un programa en primer plano
## <a name="problem-description"></a>Descripción del problema
 Estoy intentando depurar un problema de actualización de pantalla. Para observar este problema, debo mantener mi programa en primer plano, de modo que no tengo acceso a las ventanas de depuración. ¿Qué puedo hacer?

## <a name="solution"></a>Soluciones
 Si dispone de un segundo equipo, puede utilizar la función de depuración remota. Con un segundo equipo, puede observar la actualización de pantalla en el equipo remoto mientras ejecuta el depurador en el host. Para obtener más información sobre la depuración remota, vea [depuración remota](../debugger/remote-debugging.md).

## <a name="see-also"></a>Vea también
- [Preguntas más frecuentes sobre la depuración de código nativo](../debugger/debugging-native-code-faqs.md)
- [Depuración de código nativo](../debugger/debugging-native-code.md)