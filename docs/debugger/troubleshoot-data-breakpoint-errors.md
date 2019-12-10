---
title: 'Error: no se puede establecer el punto de interrupción de datos | Microsoft Docs'
ms.date: 12/3/2019
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.unable_to_set_data_breakpoint
dev_langs:
- CSharp
helpviewer_keywords:
- debugging [Visual Studio], managed
- debugging managed code, data breakpoint
ms.assetid: b06b5d65-424b-490f-bf58-97583cd7006a
author: wardengnaw
ms.author: waan
manager: caslan
ms.workload:
- multiple
ms.openlocfilehash: a61a3181f47af4a660641ef02ce4ba1b31eedc46
ms.sourcegitcommit: 916bbe1d77c9253424daa86c71c40f5e1ec74400
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/09/2019
ms.locfileid: "74951931"
---
# <a name="troubleshooting-data-breakpoint-errors"></a>Solucionar errores de puntos de interrupción de datos
Esta página le guiará a través de la resolución de errores comunes que se muestran al usar "interrumpir cuando el valor cambia".

## <a name="diagnosing-unable-to-set-data-breakpoint-errors"></a>Diagnóstico de errores de "no se pueden establecer puntos de interrupción de datos"
> [!IMPORTANT]
> Los puntos de interrupción de datos administrados se admiten en .NET Core 3,0 y up. Puede descargar la última versión [aquí](https://dotnet.microsoft.com/download).

A continuación se muestra una lista de los errores que pueden producirse al usar puntos de interrupción de datos administrados. Contienen una explicación adicional sobre por qué se está produciendo el error y las posibles soluciones o soluciones alternativas para resolver el error.

- *"La versión de .NET utilizada por el proceso de destino no admite puntos de interrupción de datos. Los puntos de interrupción de datos requieren .NET Core 3.0 + en ejecución en x86 o x64 ".*

    - La compatibilidad con puntos de interrupción de datos administrados comenzó en .NET Core 3,0. Actualmente no se admite en .NET Framework o la versión de .NET Core en 3,0. 
    
    - **Solución**: la solución a esto sería actualizar el proyecto a .net Core 3,0.

- *"No se puede encontrar el valor en el montón administrado y no se puede realizar un seguimiento".*
    - Variable declarada en la pila.
        - No se admite el establecimiento de puntos de interrupción de datos para las variables creadas en la pila, ya que esta variable no será válida una vez que se cierre la función.
        - **Solución alternativa**: establezca los puntos de interrupción en las líneas donde se usa la variable.

    - "Interrumpir cuando el valor cambia" en una variable que no se expande en una lista desplegable.
        - El depurador debe saber internamente el objeto que contiene el campo del que desea realizar un seguimiento. El recolector de elementos no utilizados puede mover el objeto por el montón para que el depurador necesite conocer el objeto que contiene la variable de la que desea realizar el seguimiento. 
        - **Solución alternativa**: Si está en un método dentro del objeto en el que desea establecer un punto de interrupción de datos, vaya a un marco y use la ventana de `locals/autos/watch` para expandir el objeto y establezca un punto de interrupción de datos en el campo que desee.

- *"No se admiten puntos de interrupción de datos para los campos estáticos ni para las propiedades estáticas".*
    
    - Los campos estáticos y las propiedades no se admiten en este momento. Si está interesado en esta característica, proporcione [sus comentarios](#provide-feedback).

- *"No se puede realizar el seguimiento de los campos y propiedades de los Structs".*

    - Los campos y las propiedades de los Structs no se admiten en este momento. Si está interesado en esta característica, proporcione [sus comentarios](#provide-feedback).

- *"El valor de la propiedad ha cambiado y ya no se puede realizar un seguimiento".*

    - Una propiedad puede cambiar la forma en que se calcula durante el tiempo de ejecución y, si esto sucede, el número de variables de las que depende la propiedad aumenta y puede superar la limitación de hardware. Consulte `"The property is dependent on more memory than can be tracked by the hardware."` a continuación.

- *"La propiedad depende de más memoria de la que puede seguir el hardware."*
    
    - Cada arquitectura tiene un número establecido de bytes y puntos de interrupción de datos de hardware que puede admitir y la propiedad en la que desea establecer un punto de interrupción de datos ha superado ese límite. Consulte la tabla de [limitaciones de hardware de punto de interrupción de datos](#data-breakpoint-hardware-limitations) para averiguar cuántos puntos de interrupción de datos compatibles con el hardware y bytes están disponibles para la arquitectura que está usando. 
    - **Solución alternativa**: establezca un punto de interrupción de datos en un valor que pueda cambiar dentro de la propiedad.

- *"No se admiten puntos de interrupción de datos al C# usar el evaluador de expresiones heredado".*

    - Los puntos de interrupción de datos solo se admiten en C# el evaluador de expresiones no heredadas. 
    - **Solución**: deshabilite el evaluador de expresiones heredadas C# ; para ello, vaya a `Debug -> Options` en `Debugging -> General` desactive `"Use the legacy C# and VB expression evaluators"`.

## <a name="data-breakpoint-hardware-limitations"></a>Limitaciones de hardware de punto de interrupción de datos

La arquitectura (configuración de plataforma) en la que se ejecuta el programa tiene un número limitado de puntos de interrupción de datos de hardware que puede usar. En la tabla siguiente se indica el número de registros que están disponibles para su uso por arquitectura.

| Arquitectura | Número de puntos de interrupción de datos admitidos por hardware | Tamaño máximo de bytes|
| :-------------: |:-------------:| :-------------:|
| x86 | 4 | 4 |
| x64 | 4 | 8 |
| ARM | 1 | 4 |
| ARM64 | 2 | 8 |

## <a name="provide-feedback"></a>Proporcionar comentarios
Si tiene algún problema o sugerencias sobre esta característica, háganoslo saber a través de la ayuda > Enviar comentarios > [notificar un problema](../ide/how-to-report-a-problem-with-visual-studio.md) en el IDE o en la [comunidad de desarrolladores](https://developercommunity.visualstudio.com/).

## <a name="see-also"></a>Vea también
- [Usar "interrumpir cuando cambie el valor" en .net Core 3,0](using-breakpoints.md#BKMK_set_a_data_breakpoint_managed).
- [DevBlog: interrumpir cuando el valor cambia: puntos de interrupción de datos para .NET Core en Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/break-when-value-changes-data-breakpoints-for-net-core-in-visual-studio-2019/)
