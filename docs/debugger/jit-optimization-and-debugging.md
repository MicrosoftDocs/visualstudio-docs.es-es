---
title: JIT optimización y depuración | Microsoft Docs
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
ms.openlocfilehash: 7346b6fd8fbd483021437638f9e134ead88a0b93
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56699150"
---
# <a name="jit-optimization-and-debugging"></a>Optimización y depuración JIT
**Cómo funcionan las optimizaciones en. NET:** si está intentando depurar el código, resulta más fácil cuando que el código está **no** optimizado. Esto es porque cuando se optimiza el código, el compilador y el tiempo de ejecución realizar cambios en el código emitido de CPU para que se ejecuta más rápido, pero tiene una asignación menos directa al código fuente original. Esto significa que los depuradores son con frecuencia no se puede indicará el valor de las variables locales y desplazarse por el código y los puntos de interrupción no funcionen según lo esperado.

Normalmente, la configuración de compilación de lanzamiento crea código optimizado y la configuración de compilación de depuración no es así. El `Optimize` propiedad de MSBuild controla si se le indica al compilador que optimice el código.

En el ecosistema de. NET, se activa código de origen a las instrucciones de CPU en un proceso en dos pasos: en primer lugar, el compilador de C# convierte el texto que escriba en un formato binario intermedio llamado MSIL y escribe en archivos DLL. Más adelante, el tiempo de ejecución .NET convierte este MSIL en instrucciones de CPU. Pueden optimizar ambos pasos hasta cierto punto, pero el segundo paso realizado por el Runtime de .NET realiza las optimizaciones más importantes.

**La opción 'Suprimir optimización JIT cargar el módulo (solo administrado)':** el depurador expone una opción que controla lo que sucede cuando se carga un archivo DLL compilado con optimizaciones habilitadas dentro del proceso de destino. Si esta opción está desactivada (el estado predeterminado), a continuación, cuando el tiempo de ejecución de .NET se compila el código MSIL en código de la CPU, que deja las optimizaciones habilitadas. Si la opción está activada, el depurador solicita que se ha deshabilitado las optimizaciones.

Para buscar el **Suprimir optimización JIT cargar el módulo (solo administrado)** opción, seleccione **herramientas** > **opciones**y, a continuación, seleccione el  **General** página bajo la **depuración** nodo.

**Cuando se debe comprobar esta opción:** Active esta opción cuando se descargan los archivos DLL de otro origen, como un paquete de nuget, y desea depurar el código de este archivo DLL. En orden para que funcione, también debe encontrar el archivo de símbolos (.pdb) de este archivo DLL.

Si solo está interesado en depurar el código que se va a crear localmente, es mejor dejar esta opción no está activada, como en algunos casos, al habilitar esta opción se retrasan significativamente la depuración. Hay dos razones para esto ralentizar:

* Código optimizado se ejecuta más rápido. Si desactiva las optimizaciones para una gran cantidad de código, puede agregar el impacto de rendimiento.
* Si tiene habilitado solo mi código, el depurador ni siquiera intentar y cargar los símbolos para los archivos DLL que se han optimizado. Buscar símbolos puede tardar mucho tiempo.

**Limitaciones de esta opción:** existen dos situaciones donde esta opción se realizará **no** trabajar:

1. En situaciones donde va a adjuntar el depurador a un proceso ya se está ejecutando, esta opción no tendrá ningún efecto sobre los módulos que ya estaban cargados en el momento en que se ha adjuntado el depurador.
2. Esta opción no tiene ningún efecto en los archivos DLL que se han compilado previamente (conocidas también como ngen'ed) en código nativo. Sin embargo, puede deshabilitar el uso del código compilado previamente, inicie el proceso con el entorno de que variable 'COMPlus_ZapDisable' establecido en '1'.

## <a name="see-also"></a>Vea también
- [Depurar código administrado](../debugger/debugging-managed-code.md)
- [Desplazarse por el código con el depurador](../debugger/navigating-through-code-with-the-debugger.md)
- [Asociar a procesos en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Proceso de ejecución administrada](/dotnet/standard/managed-execution-process)
