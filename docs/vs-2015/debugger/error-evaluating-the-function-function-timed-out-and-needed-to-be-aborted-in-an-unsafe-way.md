---
title: 'Error: Evaluación de la función &#39;función&#39; agotó y tuvo que anularse de forma insegura | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.unsafe_func_eval_abort
ms.assetid: 0a9f70ed-21ad-4a10-8535-b9c5885ad8f4
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b78d4b8f433c925521a978ab5c3a5076f329c407
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47578121"
---
# <a name="error-evaluating-the-function-39function39-timed-out-and-needed-to-be-aborted-in-an-unsafe-way"></a>Error: Evaluación de la función &#39;función&#39; agotó y tuvo que anularse de forma no segura
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Error: evaluación de la función &#39;función&#39; agotó y tuvo que anularse de forma insegura](https://docs.microsoft.com/visualstudio/debugger/error-evaluating-the-function-function-timed-out-and-needed-to-be-aborted-in-an-unsafe-way).  
  
Mensaje de texto completo: evaluar la función 'function' se agotó y tuvo que anularse de forma no segura. Esto puede haber dañado el proceso de destino. 

Para que sea más fácil de inspeccionar el estado de objetos. NET, el depurador forzará automáticamente el proceso depurado se ejecute código adicional (normalmente métodos captadores de propiedades y funciones de ToString). En la mayoría de todos los escenarios, estas funciones completar rápidamente y facilitar la depuración mucho. Sin embargo, el depurador no ejecuta la aplicación en un espacio aislado. Como resultado, un captador de propiedad o método ToString que llama a una función nativa que se bloquea puede provocar tiempos de espera largo que quizás no pueda recuperarse. Si aparece este mensaje de error, esto ha sucedido.
 
Un motivo habitual para este problema es que cuando el depurador se evalúa como una propiedad, solo permite el subproceso que se va a inspeccionar para ejecutar. Por lo que si la propiedad está esperando a otros subprocesos se ejecuten dentro de la aplicación depurada y está esperando de forma que el tiempo de ejecución .NET no se puede interrumpir, se realizará este problema.
 
## <a name="to-correct-this-error"></a>Para corregir este error
 
Existen tres posibles soluciones para este problema.
 
### <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>Solución de #1: Impedir que al depurador de la llamada a la propiedad de captador o ToString (método)
 
El mensaje de error le indicará el nombre de la función que el depurador intentó llamar a. Si se puede modificar esta función, puede impedir que el depurador llamar al captador de propiedad o método ToString. Pruebe una de las siguientes acciones:
 
* Cambiar el método a algún otro tipo de código además de un captador de propiedad o método ToString y el problema desaparecerán.
    O bien
* (Para ToString) Definir un atributo DebuggerDisplay en el tipo y puede tener el depurador evaluar un valor distinto de ToString.
    O bien
* (Para un captador de propiedad) Coloque el `[System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)]` atributo en la propiedad. Esto puede ser útil si tiene un método que debe mantenerse en una propiedad por motivos de compatibilidad de API, pero debe ser realmente un método.
 
### <a name="solution-2-have-the-target-code-ask-the-debugger-to-abort-the-evaluation"></a>Solución #2: Que el código de destino se le pida el depurador para anular la evaluación
 
El mensaje de error le indicará el nombre de la función que el depurador intentó llamar a. Si el captador de propiedad o método ToString a veces no se puede ejecutar correctamente, especialmente en situaciones donde el problema es que el código necesita otro subproceso para ejecutar el código, entonces puede llamar la función de la implementación `System.Diagnostics.Debugger.NotifyOfCrossThreadDependency` para pedir el depurador para anular la función evaluación. Con esta solución, es posible evaluar explícitamente estas funciones, pero el comportamiento predeterminado es que la ejecución se detiene cuando se produce la llamada NotifyOfCrossThreadDependency.
 
### <a name="solution-3-disable-all-implicit-evaluation"></a>Solución #3: Deshabilitar toda la evaluación implícita
 
Si las soluciones anteriores no solucionan el problema, vaya a *herramientas* / *opciones*y desactive la opción *depuración*  /   *General* / *Habilitar evaluación de propiedades y otras llamadas a función implícitas*. Esto deshabilitará la mayoría de las evaluaciones de función implícitas y debería resolver el problema.



  




