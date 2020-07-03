---
title: 'Error: El proceso de destino ha terminado con el código &#39;code&#39; al evaluar la función &#39;function&#39; | Microsoft Docs'
ms.date: 4/06/2018
ms.topic: error-reference
f1_keywords:
- vs.debug.error.process_exit_during_func_eval
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d1721196becf1f746d81fa7e3d4ff5f0371e3f57
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2020
ms.locfileid: "85460783"
---
# <a name="error-the-target-process-exited-with-code-39code39-while-evaluating-the-function-39function39"></a>Error: El proceso de destino terminó con el código &#39;code&#39; al evaluar la función &#39;function&#39;

Texto completo del mensaje: El proceso de destino terminó con el código "code" al evaluar la función "function".

Para que sea más fácil inspeccionar el estado de los objetos .NET, el depurador forzará automáticamente el proceso depurado para que ejecute código adicional (normalmente métodos captador de propiedad y funciones `ToString`). En la mayoría de los escenarios, estas funciones se completan correctamente o inician excepciones que el depurador puede detectar. Sin embargo, hay algunas circunstancias en las que no se pueden detectar excepciones porque cruzan los límites del kernel, requieren bombeo de mensajes de usuario o son irrecuperables. Como resultado, un captador de propiedad o método ToString que ejecuta código que finaliza explícitamente el proceso (por ejemplo, llama a `ExitProcess()`) o produce una excepción no controlada que no se puede detectar (por ejemplo, `StackOverflowException`) finalizará el proceso depurado y dará fin a la sesión de depuración. Si aparece este mensaje de error, esta ha sido la causa.

Un motivo común de este problema es que cuando el depurador evalúa una propiedad que se llama a sí misma, puede producirse una excepción de desbordamiento de pila. Dicha excepción no se puede recuperar y el proceso de destino finalizará.

## <a name="to-correct-this-error"></a>Para corregir este error

Estas son dos soluciones posibles a este problema.

### <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>Solución 1: Impedir que el depurador llame a la propiedad de captador o al método ToString 

El mensaje de error le indicará el nombre de la función a la que el depurador intentó llamar. Con el nombre de la función, puede intentar volver a evaluar esa función desde la ventana **Inmediato** para depurar la evaluación. La depuración es posible cuando la evaluación se realiza desde la ventana **Inmediato** porque, a diferencia de las evaluaciones implícitas de las ventanas **Automático/Variables locales/Inspección**, el depurador se interrumpe en las excepciones no controladas.

Si puede modificar esta función, puede impedir que el depurador llame a los métodos captador de propiedad o `ToString`. Pruebe una de las siguientes opciones:

* Cambie el método por otro tipo de código que no sea un método de captador de propiedad o ToString y el problema desaparece.
    o bien
* (Para `ToString`) Defina un atributo `DebuggerDisplay` en el tipo y puede hacer que el depurador evalúe algo que no sea `ToString`.
    o bien
* (Para un captador de propiedad) Coloque el atributo `[System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)]` en la propiedad. Esta opción puede ser útil si tiene un método que debe permanecer como propiedad por motivos de compatibilidad con la API, pero realmente debe ser un método.

Si no puede modificar este método, es posible que pueda interrumpir el proceso de destino en una instrucción alternativa y volver a intentar la evaluación.

### <a name="solution-2-disable-all-implicit-evaluation"></a>Solución 2: Deshabilitar todas las evaluaciones implícitas

Si las soluciones anteriores no resuelven el problema, vaya a **Herramientas** > **Opciones** y desactive el valor **Depuración** > **General** > **Habilitar la evaluación de propiedades y otras llamadas a función implícitas**. El resultado es que se deshabilitarán la mayoría de las evaluaciones de función implícitas y el problema se resolverá.
