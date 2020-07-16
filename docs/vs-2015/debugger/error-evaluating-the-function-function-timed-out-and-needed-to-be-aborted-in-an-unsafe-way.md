---
title: 'Error: El tiempo de espera de evaluación de la función &#39;function&#39; se agotó y tuvo que anularse de forma no segura | Microsoft Docs'
ms.date: 11/15/2016
ms.topic: reference
f1_keywords:
- vs.debug.error.unsafe_func_eval_abort
ms.assetid: 0a9f70ed-21ad-4a10-8535-b9c5885ad8f4
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a27bf67770eef770fddef0301a804e6c45579539
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2020
ms.locfileid: "86387127"
---
# <a name="error-evaluating-the-function-39function39-timed-out-and-needed-to-be-aborted-in-an-unsafe-way"></a>Error: El tiempo de espera de evaluación de la función &#39;function&#39; se agotó y tuvo que anularse de forma no segura
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Texto completo del mensaje: El tiempo de espera de evaluación de la función 'function' se agotó y tuvo que anularse de forma no segura, lo que puede haber dañado el proceso de destino. 

Para que sea más fácil inspeccionar el estado de los objetos .NET, el depurador fuerza automáticamente el proceso depurado para que ejecute código adicional (normalmente métodos de captador de propiedad y funciones ToString). En la mayoría de los escenarios, estas funciones terminan rápidamente y hacen que la depuración sea mucho más fácil. Sin embargo, el depurador no ejecuta la aplicación en un espacio aislado. Como resultado, un captador de propiedad o un método ToString que llama a una función nativa que deja de responder puede dar lugar a tiempos de espera largos que no se pueden recuperar. Si aparece este mensaje de error, eso es lo que ha ocurrido.
 
Una razón habitual por la que se produce este problema es que, cuando el depurador evalúa una propiedad, solo permite que se ejecute el subproceso que se está inspeccionando. Por tanto, si la propiedad está esperando a que otros subprocesos se ejecuten dentro de la aplicación depurada y está esperando de forma que el tiempo de ejecución de .NET no pueda interrumpir, se producirá este problema.
 
## <a name="to-correct-this-error"></a>Para corregir este error
 
Existen tres posibles soluciones para este problema.
 
### <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>Solución 1: Evitar que el depurador llame al método de captador propiedad o ToString
 
El mensaje de error le indica el nombre de la función a la que el depurador ha intentado llamar. Si puede modificar esta función, puede evitar que el depurador llame al método de captador de propiedad o ToString. Pruebe una de las siguientes opciones:
 
* Cambie el método por otro tipo de código que no sea un método de captador de propiedad o ToString y el problema desaparece.
    o bien
* (En el caso de ToString) Defina un atributo DebuggerDisplay en el tipo y puede hacer que el depurador evalúe algo que no sea ToString.
    o bien
* (En el caso de un captador de propiedad) Coloque el atributo `[System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)]` en la propiedad. Esto puede ser útil si tiene un método que debe permanecer como propiedad por motivos de compatibilidad con la API, pero realmente debe ser un método.
 
### <a name="solution-2-have-the-target-code-ask-the-debugger-to-abort-the-evaluation"></a>Solución 2: Hacer que el código de destino pida al depurador que anule la evaluación
 
El mensaje de error le indica el nombre de la función a la que el depurador ha intentado llamar. Si el método de captador de propiedad o ToString a veces no se ejecuta correctamente, especialmente en situaciones en las que el problema es que el código necesita otro subproceso para ejecutar código, la función de implementación puede llamar a `System.Diagnostics.Debugger.NotifyOfCrossThreadDependency` para pedir al depurador que anule la evaluación de la función. Con esta solución, sigue siendo posible evaluar estas funciones de forma explícita, pero el comportamiento predeterminado es que la ejecución se detenga cuando se produce la llamada a NotifyOfCrossThreadDependency.
 
### <a name="solution-3-disable-all-implicit-evaluation"></a>Solución 3: Deshabilitar toda evaluación implícita
 
Si las soluciones anteriores no resuelven el problema, vaya a *Herramientas* / *Opciones* y desactive el valor *Depuración* / *General* / *Habilitar la evaluación de propiedades y otras llamadas a función implícitas*. Con esto se deshabilitan la mayoría de las evaluaciones de funciones implícitas y se debe solucionar el problema.
