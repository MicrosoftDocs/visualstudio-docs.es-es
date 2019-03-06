---
title: Depuración F# | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Debugging [F#]
- F#, debugging
ms.assetid: 20bcd51c-2d06-4281-9a1e-ef2b91d1a779
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 11a310884f9f63264157c96bafc15e8161c0239d
ms.sourcegitcommit: 11337745c1aaef450fd33e150664656d45fe5bc5
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57323846"
---
# <a name="debugging-f"></a>Depurar F\#
La depuración de F# es similar a la depuración de cualquier lenguaje administrado, con algunas excepciones:

-   La ventana **Automático** no muestra variables de F#.

-   El modo Editar y Continuar no se admite en F#. Es posible editar código de F# durante una sesión de depuración pero se debería evitar. Dado que los cambios de código no se aplican durante la sesión de depuración, si se realizan cambios en el código de F# durante la depuración, el código fuente no se corresponderá con el código objeto de la depuración.

-   El depurador no reconoce expresiones de F#. Para escribir una expresión en una ventana de depurador o un cuadro de diálogo durante la depuración de F#, se debe convertir la expresión en la sintaxis de C#. Al convertir una expresión de F# en C#, no olvide que C# usa == como operador de comparación de igualdad y que F# utiliza =.

## <a name="see-also"></a>Vea también
- [Depurar código administrado](../debugger/debugging-managed-code.md)
