---
title: Depuración de funciones de la API de Windows | Microsoft Docs
ms.custom: seodec18
ms.date: 06/03/2020
ms.topic: how-to
f1_keywords:
- vs.debug.api
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], Windows API functions
- NT symbols and debugging Windows API functions
- Windows API functions, debugging
- Windows API, debugging API functions
- APIs, debugging
ms.assetid: 7c126f57-62ab-4d94-9805-632d696ba1f0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6fab5627f3d467c0df289969e4fee010dd3ea78b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85350399"
---
# <a name="how-can-i-debug-windows-api-functions"></a>Cómo depurar funciones de la API de Windows
Si desea depurar una función de la API de Windows que tiene símbolos de NT cargados, deberá hacer lo siguiente.

### <a name="to-set-a-breakpoint-on-a-windows-api-function-with-nt-symbols-loaded"></a>Para establecer un punto de interrupción en una función API de Windows con símbolos de NT cargados

- En el [punto de interrupción de la función](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file), escriba el nombre de la función junto con el nombre del archivo DLL en el que se encuentra la función (consulte el [operador de contexto](../debugger/context-operator-cpp.md)). En el código de 32 bits, utilice el formato representativo del nombre de la función. Para establecer un punto de interrupción en **MessageBeep**, por ejemplo, debe escribir lo siguiente:

    ```cpp
    {,,USER32.DLL}_MessageBeep@4
    ```

     Para obtener el nombre representativo, vea [Ver nombres representativos](https://msdn.microsoft.com/library/f79e2717-a4db-4d12-a689-69830cce2be0).

     Puede probar el nombre representativo y verlo en el código del desensamblado. Mientras esté en pausa en la función en el depurador de Visual Studio, haga clic con el botón derecho en dicha función en el editor de código o en la ventana de la pila de llamadas y elija **Ir al desensamblado**.

- En el código de 64 bits, puede utilizar el nombre no representativo.

    ```cpp
    {,,USER32.DLL}MessageBeep
    ```

## <a name="see-also"></a>Vea también
- [Preguntas más frecuentes sobre la depuración de código nativo](../debugger/debugging-native-code-faqs.md)
- [Depuración de código nativo](../debugger/debugging-native-code.md)
