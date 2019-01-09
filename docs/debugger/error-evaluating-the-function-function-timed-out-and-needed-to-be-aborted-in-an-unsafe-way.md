---
title: 'Error: Evaluación de la función &#39;función&#39; agotó y tuvo que anularse de forma insegura | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.unsafe_func_eval_abort
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a72bd821d7ecd32e82b2ad3b02debe03ff511531
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53883316"
---
# <a name="error-evaluating-the-function-39function39-timed-out-and-needed-to-be-aborted-in-an-unsafe-way"></a>Error: Evaluación de la función &#39;función&#39; agotó y tuvo que anularse de forma no segura

Texto completo del mensaje: El tiempo de espera de evaluación de la función 'función' se agotó y tuvo que anularse de forma no segura Esto puede haber dañado el proceso de destino. 

Para que sea más fácil de inspeccionar el estado de objetos. NET, el depurador forzará automáticamente el proceso depurado se ejecute código adicional (normalmente métodos captadores de propiedades y funciones de ToString). En la mayoría de todos los escenarios, estas funciones completar rápidamente y facilitar la depuración mucho. Sin embargo, el depurador no ejecuta la aplicación en un espacio aislado. Como resultado, un captador de propiedad o método ToString que llama a una función nativa que se bloquea puede provocar tiempos de espera largo que quizás no pueda recuperarse. Si aparece este mensaje de error, esto ha sucedido.
 
Un motivo habitual para este problema es que cuando el depurador se evalúa como una propiedad, solo permite el subproceso que se va a inspeccionar para ejecutar. Por lo que si la propiedad está esperando a otros subprocesos se ejecuten dentro de la aplicación depurada y está esperando de forma que el tiempo de ejecución .NET no se puede interrumpir, se realizará este problema.
 
## <a name="to-correct-this-error"></a>Para corregir este error
 
Existen varias soluciones posibles para este problema.
 
### <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>Solución 1 Evitar que al depurador de la llamada a la propiedad de captador o ToString (método)
 
El mensaje de error le indicará el nombre de la función que el depurador intentó llamar a. Si se puede modificar esta función, puede impedir que el depurador llamar al captador de propiedad o método ToString. Pruebe una de las siguientes acciones:
 
* Cambiar el método a algún otro tipo de código además de un captador de propiedad o método ToString y el problema desaparecerán.
    o bien
* (Para ToString) Definir un atributo DebuggerDisplay en el tipo y puede tener el depurador evaluar un valor distinto de ToString.
    o bien
* (Para un captador de propiedad) Coloque el `[System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)]` atributo en la propiedad. Esto puede ser útil si tiene un método que debe mantenerse en una propiedad por motivos de compatibilidad de API, pero debe ser realmente un método.
 
### <a name="solution-2-have-the-target-code-ask-the-debugger-to-abort-the-evaluation"></a>Solución 2 Que el código de destino le pregunte el depurador para anular la evaluación
 
El mensaje de error le indicará el nombre de la función que el depurador intentó llamar a. Si el captador de propiedad o método ToString a veces no se puede ejecutar correctamente, especialmente en situaciones donde el problema es que el código necesita otro subproceso para ejecutar el código, entonces puede llamar la función de la implementación `System.Diagnostics.Debugger.NotifyOfCrossThreadDependency` para pedir el depurador para anular la función evaluación. Con esta solución, es posible evaluar explícitamente estas funciones, pero el comportamiento predeterminado es que la ejecución se detiene cuando se produce la llamada NotifyOfCrossThreadDependency.
 
### <a name="solution-3-disable-all-implicit-evaluation"></a>Solución 3 Deshabilitar toda la evaluación implícita
 
Si las soluciones anteriores no solucionan el problema, vaya a **herramientas** > **opciones**y desactive la opción **depuración**  >   **General** > **Habilitar evaluación de propiedades y otras llamadas a función implícitas**. Esto deshabilitará la mayoría de las evaluaciones de función implícitas y debería resolver el problema.

### <a name="solution-4-enable-managed-compatibility-mode"></a>&Solución Habilitar el modo de compatibilidad administrado

Si cambia al motor de depuración heredado, puede eliminar este error. Vaya a **herramientas** > **opciones**y seleccione la opción **depuración** > **General**  >  **Usar el modo de compatibilidad administrado**. Para obtener más información, consulte [General de las opciones de depuración](../debugger/general-debugging-options-dialog-box.md).
