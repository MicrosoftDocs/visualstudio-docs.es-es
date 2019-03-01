---
title: Buscar qué llamada con error al llamar a una función muchas veces | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.functions
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- conditional breakpoints
- errors [debugger], function calls
- breakpoints, troubleshooting
- errors [debugger], finding which function call failed
- failures
- location breakpoint call failures
- errors [Visual Studio], function calls
- hit counts
- function calls, failure
- functions [debugger]
- Skip Count
ms.assetid: 66cfac86-f5be-4d3a-9329-d44cd74bc586
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fa6fb9613df5f5bffb50c9a161eaa0a0254f26dd
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56696901"
---
# <a name="when-calling-a-function-hundreds-of-times-how-do-i-know-which-call-failed"></a>Determinar qué llamada genera el error cuando se llama a una función varias veces
## <a name="problem-description"></a>Descripción del problema
 El programa presenta un error en una llamada a una cierta función, `CnvtV`. El programa probablemente llama a esa función unas doscientas veces antes del error. Si se define un punto de interrupción en `CnvtV`, el programa se detiene en todas las llamadas a esa función, pero no es eso lo que se pretende. No se sabe qué condiciones hacen que la llamada produzca un error, de modo que no se puede establecer un punto de interrupción condicional. ¿Qué puedo hacer?

## <a name="solution"></a>Soluciones
 Puede establecer un punto de interrupción en la función con el campo **Número de llamadas** establecido en un valor tan alto que no se pueda alcanzar. En este caso, como la función `CnvtV` se invoca unas doscientas veces, asigne a **Número de llamadas** un valor de 1000 o superior. A continuación, ejecute el programa y espere a que se produzca el error de la llamada. Cuando lo haga, abra la ventana Puntos de interrupción y examine la lista de puntos de interrupción. El punto de interrupción definido sobre `CnvtV` aparece seguido del número de llamadas y el número de iteraciones restantes:

```cpp
CnvtV(int) (no condition) when hit count is equal to 1000 (currently 101)
```

 Ahora sabe que la función produjo un error en la llamada nº 101. Si restablece el punto de interrupción con un número de llamadas de 101 y ejecuta el programa otra vez, éste se detiene en la llamada a `CnvtV` que causó el error.

## <a name="see-also"></a>Vea también
- [Preguntas más frecuentes sobre la depuración de código nativo](../debugger/debugging-native-code-faqs.md)
- [Establecimiento de puntos de interrupción](https://msdn.microsoft.com/library/fe4eedc1-71aa-4928-962f-0912c334d583)
- [Depuración de código nativo](../debugger/debugging-native-code.md)
