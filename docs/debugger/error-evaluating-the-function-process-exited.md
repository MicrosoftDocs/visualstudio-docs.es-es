---
title: 'Error: Se cerró el proceso de destino al evaluar la función &#39;función&#39; | Documentos de Microsoft'
ms.custom: ''
ms.date: 4/06/2018
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.process_exit_func_eval_abort
ms.technology: vs-ide-debug
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 620ff03ef364c21e20151547effe8bfbf5935fe7
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
---
# <a name="error-the-target-process-exited-while-evaluating-the-function-39function39"></a>Error: Se cerró el proceso de destino al evaluar la función &#39;(función)&#39;

Mensaje de texto completo: terminó el proceso de destino al evaluar la función 'function'. Consulte la ventana de salida para el código de salida del proceso de destino.

Para facilitar la inspeccionar el estado de objetos. NET, el depurador automáticamente forzará el proceso depurado para ejecutar código adicional (normalmente los métodos de captador de propiedad y `ToString` funciones). En la mayoría de los casos, estas funciones completan correctamente o producen excepciones que se pueden detectar el depurador. Sin embargo, hay algunas circunstancias en las que no se puede detectar excepciones porque cruzar los límites del kernel, requieren la distribución de mensajes de usuario o son irrecuperables. Como consecuencia, un captador de propiedad o método ToString que ejecuta código que termina explícitamente el proceso (por ejemplo, llama a `ExitProcess()`) o se produce una excepción no controlada que no se puede detectar (por ejemplo, `StackOverflowException`) se cerrará el proceso depurado y finalizar la sesión de depuración. Si aparece este mensaje de error, esto se ha producido.
 
Una causa habitual de este problema es que cuando el depurador se evalúa como una propiedad que se llama a sí mismo, esto puede producir una excepción de desbordamiento de pila. No se puede recuperar la excepción de desbordamiento de pila y se terminará el proceso de destino.
 
## <a name="to-correct-this-error"></a>Para corregir este error
 
Hay dos posibles soluciones para este problema.
 
### <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>Solución #1: Evitar que al depurador de la llamada a la propiedad de captador o ToString (método) 

El mensaje de error indicará el nombre de la función que el depurador intentó llamar a. Con el nombre de la función, puede intentar volver a evaluar esa función de la **inmediato** ventana para depurar la evaluación. Depuración es posible al evaluar desde la **inmediato** ventana porque, a diferencia de las evaluaciones implícita desde el **automático/variables locales/inspección** windows, el depurador se interrumpe en excepciones no controladas.

Si se puede modificar esta función, puede impedir que el depurador llamar al captador de propiedades o `ToString` método. Pruebe una de las siguientes acciones:
 
* Cambiar el método a algún otro tipo de código además de un captador de propiedad o método ToString y el problema desaparecerán.
    -o bien-
* (Para `ToString`) definir una `DebuggerDisplay` atributo en el tipo y puede que el depurador evalúa algo distinto de `ToString`.
    -o bien-
* (Para un captador de propiedad) Coloque el `[System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)]` atributo en la propiedad. Esto puede resultar útil si tiene un método que debe permanecer en una propiedad por motivos de compatibilidad de API, pero realmente debería ser un método.

Si no se puede modificar este método, es posible que pueda interrumpir el proceso de destino en una instrucción alternativa y vuelva a intentar la evaluación.
 
### <a name="solution-2-disable-all-implicit-evaluation"></a>Solución #2: Deshabilitar toda la evaluación implícita
 
Si las soluciones anteriores no soluciona el problema, vaya a **herramientas** > **opciones**y desactive la opción **depuración**  >   **General** > **Habilitar evaluación de propiedades y otras llamadas a función implícitas**. Esto deshabilitará la mayoría de las evaluaciones de función implícitas y debería resolver el problema.



  
