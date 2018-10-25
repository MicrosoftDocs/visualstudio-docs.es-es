---
title: 'Error: El proceso de destino se cerró con el código &#39;código&#39; al evaluar la función &#39;función&#39; | Microsoft Docs'
ms.custom: ''
ms.date: 4/06/2018
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.process_exit_during_func_eval
ms.technology: vs-ide-debug
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 98923757912d1f4619cc79c8f946aabaa531ac05
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49936269"
---
# <a name="error-the-target-process-exited-with-code-39code39-while-evaluating-the-function-39function39"></a>Error: El proceso de destino se cerró con el código &#39;código&#39; al evaluar la función &#39;(función)&#39;

Mensaje de texto completo: el proceso de destino se cerró con el código "code" al evaluar la función 'función'.

Para que sea más fácil de inspeccionar el estado de objetos. NET, el depurador forzará automáticamente el proceso depurado se ejecute código adicional (normalmente, los métodos de captador de propiedad y `ToString` funciones). En la mayoría de los escenarios, estas funciones se completan correctamente o producen excepciones que se pueden detectar el depurador. Sin embargo, hay algunas circunstancias en que las excepciones no se puede detectar porque cruzar los límites del kernel, requieren el suministro de mensajes de usuario o son irrecuperables. Como un resultado, un captador de propiedad o método ToString que ejecuta código que explícitamente se finaliza el proceso (por ejemplo, llamadas `ExitProcess()`) o se produce una excepción no controlada que no se puede detectar (por ejemplo, `StackOverflowException`) finalizará el proceso depurado y finalizar la sesión de depuración. Si aparece este mensaje de error, esto ha sucedido.
 
Un motivo habitual para este problema es que cuando el depurador se evalúa como una propiedad que se llama a sí mismo, esto puede producir una excepción de desbordamiento de pila. No se puede recuperar la excepción de desbordamiento de pila y se finalizará el proceso de destino.
 
## <a name="to-correct-this-error"></a>Para corregir este error
 
Hay dos soluciones posibles para este problema.
 
### <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>Solución de #1: Impedir que al depurador de la llamada a la propiedad de captador o ToString (método) 

El mensaje de error le indicará el nombre de la función que el depurador intentó llamar a. Con el nombre de la función, puede intentar volver a evaluar esa función desde el **inmediato** ventana para depurar la evaluación. Es posible depurar al evaluar desde el **inmediato** ventana porque, a diferencia de las evaluaciones implícitas desde el **automático/variables locales/inspección** windows, el depurador se interrumpe en excepciones no controladas.

Si se puede modificar esta función, puede impedir que el depurador de una llamada del captador de propiedad o `ToString` método. Pruebe una de las siguientes acciones:
 
* Cambiar el método a algún otro tipo de código además de un captador de propiedad o método ToString y el problema desaparecerán.
    O bien
* (Para `ToString`) definir una `DebuggerDisplay` atributo en el tipo y puede tener el depurador evaluar algo distinto `ToString`.
    O bien
* (Para un captador de propiedad) Coloque el `[System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)]` atributo en la propiedad. Esto puede ser útil si tiene un método que debe permanecer en una propiedad por motivos de compatibilidad de API, pero debe ser realmente un método.

Si no se puede modificar este método, puede interrumpir el proceso de destino en una instrucción alternativa e intente de nuevo la evaluación.
 
### <a name="solution-2-disable-all-implicit-evaluation"></a>Solución #2: Deshabilitar toda la evaluación implícita
 
Si las soluciones anteriores no solucionan el problema, vaya a **herramientas** > **opciones**y desactive la opción **depuración**  >   **General** > **Habilitar evaluación de propiedades y otras llamadas a función implícitas**. Esto deshabilitará la mayoría de las evaluaciones de función implícitas y debería resolver el problema.



  
