---
title: El tiempo de espera de evaluación de la función &apos;function&apos; se agotó y tuvo que anularse de forma no segura | Microsoft Docs
description: "Texto completo del mensaje: El tiempo de espera de evaluación de la función 'function' se agotó y tuvo que anularse de forma no segura,"
ms.date: 06/18/2021
ms.topic: error-reference
ms.custom: contperf-fy21q4
f1_keywords:
- vs.debug.error.unsafe_func_eval_abort
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 94c308e9ec960f744a98f0f930999df36afff475
ms.sourcegitcommit: d3658667e768d7516cbf4461ec47bf24c8fcb7e6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112925012"
---
# <a name="error-evaluating-the-function-39function39-timed-out-and-needed-to-be-aborted-in-an-unsafe-way"></a>Error: El tiempo de espera de evaluación de la función &#39;function&#39; se agotó y tuvo que anularse de forma no segura

Texto completo del mensaje: El tiempo de espera de evaluación de la función 'function' se agotó y tuvo que anularse de forma no segura, lo que puede haber dañado el proceso de destino.

Para que sea más fácil inspeccionar el estado de los objetos .NET, el depurador fuerza automáticamente el proceso depurado para que ejecute código adicional (normalmente métodos de captador de propiedad y funciones ToString). En la mayoría de los escenarios, estas funciones terminan rápidamente y hacen que la depuración sea mucho más fácil. Pero el depurador no ejecuta la aplicación en un espacio aislado. Como resultado, un método de captador de propiedad o ToString que llame a una función nativa que deja de responder puede dar lugar a tiempos de espera largos que no se pueden recuperar. Si aparece este mensaje de error, eso es lo que ha ocurrido.

Una razón habitual por la que se produce este problema es que, cuando el depurador evalúa una propiedad, solo permite que se ejecute el subproceso que se está inspeccionando. Por tanto, si la propiedad está esperando a que otros subprocesos se ejecuten dentro de la aplicación depurada, y si está esperando de una forma que el runtime de .NET no puede interrumpir, se produce este problema.

## <a name="to-correct-this-error"></a>Para corregir este error

Vea las secciones siguientes para obtener varias soluciones posibles a este problema.

## <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>Solución 1: Evitar que el depurador llame al método de captador propiedad o ToString

El mensaje de error le indica el nombre de la función a la que el depurador ha intentado llamar. Si puede modificar esta función, puede evitar que el depurador llame al método de captador de propiedad o ToString. Pruebe una de las siguientes opciones:

* Cambie el método por otro tipo de código que no sea un método de captador de propiedad o ToString y el problema desaparece.
  o bien
* (Para ToString) Defina un atributo [DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md) en el tipo y puede hacer que el depurador evalúe algo que no sea ToString.
  O bien
* (Para un captador de propiedad) Coloque el atributo [System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)](/dotnet/api/system.diagnostics.debuggerbrowsableattribute) en la propiedad. Esto puede ser útil si tiene un método que debe permanecer como propiedad por motivos de compatibilidad con la API, pero realmente debe ser un método.

## <a name="solution-2-have-the-target-code-ask-the-debugger-to-abort-the-evaluation"></a>Solución 2: Hacer que el código de destino pida al depurador que anule la evaluación

El mensaje de error le indica el nombre de la función a la que el depurador ha intentado llamar. Si el método de captador de propiedad o ToString a veces no se ejecuta de forma correcta, especialmente en situaciones en las que el problema es que el código necesita otro subproceso para ejecutar código, la función de implementación puede llamar a [System.Diagnostics.Debugger.NotifyOfCrossThreadDependency](/dotnet/api/system.diagnostics.debugger.notifyofcrossthreaddependency) para pedir al depurador que anule la evaluación de la función. Con esta solución, sigue siendo posible evaluar estas funciones de forma explícita, pero el comportamiento predeterminado es que la ejecución se detenga cuando se produce la llamada a NotifyOfCrossThreadDependency.

## <a name="solution-3-disable-all-implicit-evaluation"></a>Solución 3: Deshabilitar toda evaluación implícita

Si las soluciones anteriores no resuelven el problema, vaya a **Herramientas** > **Opciones** y desactive el valor **Depuración** > **General** > **Habilitar la evaluación de propiedades y otras llamadas a función implícitas**. El resultado es que se deshabilitarán la mayoría de las evaluaciones de función implícitas y el problema se resolverá.

## <a name="solution-4-check-compatibility-with-third-party-developer-tools"></a>Solución 4: Comprobar la compatibilidad con herramientas de desarrollo de terceros

Si usa Resharper, vea este [problema](https://youtrack.jetbrains.com/issue/RSRP-476824) para obtener sugerencias.

## <a name="solution-5-enable-managed-compatibility-mode"></a>Solución 5: Habilitar el modo de compatibilidad administrado

Si cambia al motor de depuración heredado, es posible que pueda eliminar este error. Vaya a **Herramientas** > **Opciones** y seleccione la opción **Depuración** > **General** > **Usar modo de compatibilidad administrado**. Para obtener más información, vea [Opciones generales de depuración](../debugger/general-debugging-options-dialog-box.md).
