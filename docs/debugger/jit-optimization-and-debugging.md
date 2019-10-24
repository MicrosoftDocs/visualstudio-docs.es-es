---
title: Optimización y depuración JIT | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], optimized code
- optimized code, debugging
ms.assetid: 19bfabf3-1a2e-49dc-8819-a813982e86fd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 12752acf75da70fa30666f9b1780256c94bde859
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72731620"
---
# <a name="jit-optimization-and-debugging"></a>Optimización y depuración JIT
**Cómo funcionan las optimizaciones en .net:** Si está intentando depurar código, es más fácil cuando ese código **no** está optimizado. Esto se debe a que cuando se optimiza el código, el compilador y el tiempo de ejecución realizan cambios en el código de CPU emitido para que se ejecute más rápido, pero tiene una asignación menos directa al código fuente original. Esto significa que los depuradores a menudo no pueden indicar el valor de las variables locales, y los puntos de interrupción y la ejecución de código pueden no funcionar como se espera.

Normalmente, la configuración de compilación de versión crea código optimizado y la configuración de compilación de depuración no. La propiedad `Optimize` MSBuild controla si se indica al compilador que optimice el código.

En el ecosistema de .NET, el código se convierte en instrucciones de origen a CPU en un proceso de dos pasos C# : en primer lugar, el compilador convierte el texto que se escribe en un formato binario intermedio denominado MSIL y lo escribe en los archivos. dll. Después, el tiempo de ejecución de .NET convierte este MSIL en instrucciones de CPU. Ambos pasos se pueden optimizar hasta cierto punto, pero el segundo paso realizado por el tiempo de ejecución de .NET realiza las optimizaciones más significativas.

**La opción ' suprimir optimización JIT al cargar el módulo (solo administrado) ':** El depurador expone una opción que controla lo que ocurre cuando un archivo DLL compilado con optimizaciones habilitadas se carga dentro del proceso de destino. Si esta opción está desactivada (el estado predeterminado), cuando el tiempo de ejecución de .NET compila el código MSIL en el código de CPU, deja las optimizaciones habilitadas. Si la opción está activada, el depurador solicita que se deshabiliten las optimizaciones.

Para encontrar la opción **suprimir optimización JIT al cargar el módulo (solo administrado)** , seleccione **herramientas**  > **Opciones**y, a continuación, seleccione la página **General** en el nodo **depuración** .

**Cuando deba activar esta opción:** Active esta opción cuando descargó los archivos dll de otro origen, como un paquete Nuget, y desea depurar el código en este archivo DLL. Para que esto funcione, también debe buscar el archivo de símbolos (. pdb) para este archivo DLL.

Si solo le interesa depurar el código que está creando localmente, es mejor dejar esta opción desactivada, como en algunos casos, si habilita esta opción, se ralentizará considerablemente la depuración. Hay dos motivos para que esto sea más lento:

* El código optimizado se ejecuta más rápido. Si va a desactivar las optimizaciones de gran cantidad de código, se puede Agregar el impacto en el rendimiento.
* Si ha habilitado Solo mi código, el depurador no probará ni cargará símbolos para los archivos dll optimizados. La búsqueda de símbolos puede tardar mucho tiempo.

**Limitaciones de esta opción:** Hay dos situaciones en las que esta opción **no** funcionará:

1. En situaciones en las que se asocia el depurador a un proceso que ya se está ejecutando, esta opción no tendrá ningún efecto en los módulos que ya se cargaron en el momento en que se adjuntó el depurador.
2. Esta opción no tiene ningún efecto en los archivos DLL que se han compilado previamente (a. k. a ngen'ed) en el código nativo. Sin embargo, puede deshabilitar el uso de código precompilado iniciando el proceso con la variable de entorno "COMPlus_ZapDisable" establecida en "1".

## <a name="see-also"></a>Vea también
- [Depurar código administrado](../debugger/debugging-managed-code.md)
- [Desplazarse por el código con el depurador](../debugger/navigating-through-code-with-the-debugger.md)
- [Asociar a procesos en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Proceso de ejecución administrada](/dotnet/standard/managed-execution-process)
