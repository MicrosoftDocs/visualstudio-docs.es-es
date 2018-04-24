---
title: 'Error: Evaluar la función &#39;función&#39; agotó el tiempo y sea necesario se anulará de forma insegura | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.unsafe_func_eval_abort
ms.technology: vs-ide-debug
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9843dd870521312f45353c894908130fba0074c7
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
---
# <a name="error-evaluating-the-function-39function39-timed-out-and-needed-to-be-aborted-in-an-unsafe-way"></a>Error: Evaluar la función &#39;función&#39; agotó el tiempo y sea necesario se anulará de forma no segura

Mensaje de texto completo: evaluar la función 'function' agotó el tiempo y sea necesario se anulará de forma insegura. Esto puede haber dañado el proceso de destino. 

Para facilitar la inspeccionar el estado de objetos. NET, el depurador forzará automáticamente el proceso depurado para ejecutar código adicional (normalmente métodos captadores de propiedades y funciones de ToString). En la mayoría de todos los casos, estas funciones completar rápidamente y facilitar la depuración mucho. Sin embargo, el depurador no ejecuta la aplicación en un espacio aislado. Como resultado, un captador de propiedad o método ToString que llama a una función nativa que se bloquea puede provocar tiempos de espera largo que pueden no ser recuperable. Si aparece este mensaje de error, esto se ha producido.
 
Una causa habitual de este problema es que cuando el depurador se evalúa como una propiedad, solo permite el subproceso que se va a inspeccionar para ejecutar. Por lo que si la propiedad está esperando en otros subprocesos se ejecuten dentro de la aplicación depurada y está en espera de forma que el tiempo de ejecución de .NET no puede interrumpir, se producirá este problema.
 
## <a name="to-correct-this-error"></a>Para corregir este error
 
Hay tres posibles soluciones para este problema.
 
### <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>Solución #1: Evitar que al depurador de la llamada a la propiedad de captador o ToString (método)
 
El mensaje de error indicará el nombre de la función que el depurador intentó llamar a. Si se puede modificar esta función, puede evitar que al depurador llamar al captador de propiedad o método ToString. Pruebe una de las siguientes acciones:
 
* Cambiar el método a algún otro tipo de código además de un captador de propiedad o método ToString y el problema desaparecerán.
    -o bien-
* (Para ToString) Definir un atributo DebuggerDisplay en el tipo y puede que el depurador evalúa un valor distinto de ToString.
    -o bien-
* (Para un captador de propiedad) Coloque el `[System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)]` atributo en la propiedad. Esto puede resultar útil si tiene un método que debe mantenerse en una propiedad por motivos de compatibilidad de API, pero realmente debería ser un método.
 
### <a name="solution-2-have-the-target-code-ask-the-debugger-to-abort-the-evaluation"></a>Solución #2: Que el código de destino se le pida el depurador para anular la evaluación
 
El mensaje de error indicará el nombre de la función que el depurador intentó llamar a. Si el captador de propiedad o método ToString a veces no se puede ejecutar correctamente, sobre todo en situaciones donde el problema es que el código necesita otro subproceso para ejecutar el código, puede llamar la función de la implementación `System.Diagnostics.Debugger.NotifyOfCrossThreadDependency` que ponerse en contacto el depurador para anular la función evaluación. Con esta solución, todavía es posible evaluar explícitamente estas funciones, pero el comportamiento predeterminado es que la ejecución se detiene cuando se produce la llamada NotifyOfCrossThreadDependency.
 
### <a name="solution-3-disable-all-implicit-evaluation"></a>Solución #3: Deshabilitar toda la evaluación implícita
 
Si las soluciones anteriores no soluciona el problema, vaya a *herramientas* > *opciones*y desactive la opción *depuración*  >   *General* > *Habilitar evaluación de propiedades y otras llamadas a función implícitas*. Esto deshabilitará la mayoría de las evaluaciones de función implícitas y debería resolver el problema.



  
