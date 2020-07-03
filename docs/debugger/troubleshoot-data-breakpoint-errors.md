---
title: 'Error: No se puede establecer el punto de interrupción de datos | Microsoft Docs'
ms.date: 12/3/2019
ms.topic: error-reference
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
ms.openlocfilehash: dab5e146d510601c6e93582b6b128abcd964b4a7
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2020
ms.locfileid: "85459940"
---
# <a name="troubleshooting-data-breakpoint-errors"></a>Solución de errores con el punto de interrupción de datos
Esta página lo guiará a través de la resolución de los errores comunes vistos cuando se usa "Interrumpir cuando cambia el valor".

## <a name="diagnosing-unable-to-set-data-breakpoint-errors"></a>Diagnóstico de errores del tipo "No se puede establecer el punto de interrupción de datos"
> [!IMPORTANT]
> Los puntos de interrupción de datos administrados se admiten en .NET Core 3.0 y versiones posteriores. Puede descargar la versión más reciente [aquí](https://dotnet.microsoft.com/download).

A continuación se muestra una lista de los errores que pueden producirse al usar puntos de interrupción de datos administrados. Contienen una explicación adicional sobre la razón por la que sucede el error y las posibles soluciones para resolverlo.

- *"La versión de .NET usada por el proceso de destino no admite puntos de interrupción de datos. Los puntos de interrupción de datos requieren que se ejecute .NET Core 3.0+ en x86 o x64".*

    - La compatibilidad con los puntos de interrupción de datos administrados empezó en .NET Core 3.0. Actualmente no se admiten en .NET Framework ni en versiones de .NET Core anteriores a 3.0. 
    
    - **Solución**: La solución sería actualizar el proyecto a .NET Core 3.0.

- *"No se encuentra el valor en el montón administrado y no se puede realizar el seguimiento".*
    - Variable declarada en la pila.
        - No se admite establecer puntos de interrupción de datos para variables creadas en la pila, porque esta variable no será válida una vez que se cierre la función.
        - **Solución alternativa**: Establezca puntos de interrupción en las líneas donde se usa la variable.

    - "Interrumpir cuando cambia el valor" en una variable que no se expande de una lista desplegable.
        - Internamente, el depurador tiene que conocer el objeto que contiene el campo del que quiere realizar el seguimiento. El recolector de elementos no utilizados puede mover el objeto por el montón, por lo que el depurador necesitará conocer el objeto que contiene la variable de la que quiere realizar el seguimiento. 
        - **Solución alternativa**: Si está en un método dentro del objeto en el que quiere establecer un punto de interrupción de datos, retroceda un fotograma y use la ventana `locals/autos/watch` para expandir el objeto y establecer un punto de interrupción de datos en el campo que desea.

- *"No se admiten puntos de interrupción de datos para campos estáticos o propiedades estáticas".*
    
    - Por el momento, no se admiten las propiedades ni los campos estáticos. Si le interesa esta característica, envíe sus [comentarios](#provide-feedback).

- *"No se puede realizar un seguimiento de los campos y propiedades de structs".*

    - Por el momento, no se admiten los campos ni las propiedades de structs. Si le interesa esta característica, envíe sus [comentarios](#provide-feedback).

- *"El valor de la propiedad ha cambiado y ya no se puede realizar un seguimiento".*

    - Una propiedad puede cambiar la forma en que se calcula durante el tiempo de ejecución y, si esto sucede, el número de variables de las que depende la propiedad aumenta y puede superar la limitación de hardware. Consulte `"The property is dependent on more memory than can be tracked by the hardware."` a continuación.

- *"La propiedad depende de más memoria de la que puede seguir el hardware".*
    
    - Cada arquitectura tiene un número establecido de bytes y puntos de interrupción de datos de hardware que puede admitir y la propiedad en la que quiere establecer un punto de interrupción de datos superó ese límite. Consulte la tabla [Limitaciones de hardware de los puntos de interrupción de datos](#data-breakpoint-hardware-limitations) para saber cuántos bytes y puntos de interrupción de datos admitidos por el hardware hay disponibles para la arquitectura que se está usando. 
    - **Solución alternativa**: Establezca un punto de interrupción de datos en un valor que pueda cambiar dentro de la propiedad.

- *"No se admiten puntos de interrupción de datos al usar el evaluador de expresiones de C# heredadas".*

    - Los puntos de interrupción de datos solo se admiten en el evaluador de expresiones de C# no heredado. 
    - **Solución**: Para deshabilitar el evaluador de expresiones de C# heredado, vaya a `Debug -> Options` y, en `Debugging -> General`, desactive `"Use the legacy C# and VB expression evaluators"`.

## <a name="data-breakpoint-hardware-limitations"></a>Limitaciones de hardware de los puntos de interrupción de datos

La arquitectura (configuración de plataforma) en la que se ejecuta el programa tiene un número limitado de puntos de interrupción de datos de hardware que puede usar. En la tabla siguiente se indica el número de registros que están disponibles para su uso por arquitectura.

| Arquitectura | Número de puntos de interrupción de datos admitidos por el hardware | Tamaño máximo de bytes|
| :-------------: |:-------------:| :-------------:|
| x86 | 4 | 4 |
| x64 | 4 | 8 |
| ARM | 1 | 4 |
| ARM64 | 2 | 8 |

## <a name="provide-feedback"></a>Proporcionar comentarios
Si tiene algún problema o sugerencia sobre esta característica, comuníquela en Ayuda > Enviar comentarios > [Notificar un problema](../ide/how-to-report-a-problem-with-visual-studio.md) en el IDE o en [Developer Community](https://developercommunity.visualstudio.com/).

## <a name="see-also"></a>Vea también
- [Uso de "Interrumpir cuando cambia el valor" en .NET Core 3.0](using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus).
- [DevBlog: Break When Value Changes: Data Breakpoints for .NET Core in Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/break-when-value-changes-data-breakpoints-for-net-core-in-visual-studio-2019/) (DevBlog: Interrumpir cuando cambia el valor: puntos de interrupción de datos para .NET Core en Visual Studio 2019)
