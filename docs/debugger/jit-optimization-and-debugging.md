---
title: JIT optimización y depuración | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9a9b18ab38c7c19fa5208d34439bd3133099e8bc
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
ms.locfileid: "31477360"
---
# <a name="jit-optimization-and-debugging"></a>Optimización y depuración JIT
**Cómo funcionan las optimizaciones en. NET:** si está intentando depurar el código, resulta más sencillo al que el código está **no** optimizado. Esto es porque cuando se optimiza el código, el compilador y el tiempo de ejecución realizan cambios en el código emitido de CPU para que se ejecute más rápido, pero tiene una asignación menos directa al código fuente original. Esto significa que los depuradores son con frecuencia no se puede indicar el valor de las variables locales y desplazarse por el código y los puntos de interrupción no funcionen como esperaba.

Normalmente, la configuración de compilación de lanzamiento crea código optimizado y la configuración de compilación de depuración no lo hace. El `Optimize` propiedad de MSBuild controla si se le indica al compilador que optimice el código.

En el ecosistema de. NET, se activa código de origen de instrucciones de CPU de un proceso de dos pasos: en primer lugar, el compilador de C# convierte el texto que escriba en un formato binario intermedio llamado MSIL y se escribe en archivos .dll. Más adelante, el tiempo de ejecución de .NET convierte este MSIL en instrucciones de CPU. Ambos pasos pueden optimizar hasta cierto punto, pero el segundo paso realizado por el Runtime de .NET realiza las optimizaciones más importantes.

**La opción 'Suprimir optimización JIT cargar el módulo (solo administrado)':** el depurador expone una opción que controla lo que ocurre cuando se carga un archivo DLL que se compila con las optimizaciones habilitadas dentro del proceso de destino. Si esta opción está desactivada (el estado predeterminado), a continuación, cuando el tiempo de ejecución de .NET se compila el código MSIL en código de CPU, deja las optimizaciones habilitadas. Si la opción está activada, el depurador solicita que se ha deshabilitado las optimizaciones.

El **Suprimir optimización JIT cargar el módulo (solo administrado)** opción puede encontrarse en el **General** página en el **depuración** nodo en el **opciones** cuadro de diálogo.

**Cuándo se debe comprobar esta opción:** Active esta opción si ha descargado los archivos DLL de otro origen, como un paquete de nuget, y desea depurar el código de este archivo DLL. En orden para que funcione, también debe buscar el archivo de símbolos (.pdb) para este archivo DLL.

Si solo está interesado en depurar el código que se va a compilar localmente, es mejor dejar esta opción no está activada, como, en algunos casos, si se habilita esta opción se retrasan significativamente la depuración. Hay dos razones para Esto ralentizará:

* El código optimizado se ejecuta con mayor rapidez. Si desactiva las optimizaciones para una gran cantidad de código, puede sumar el impacto en el rendimiento.
* Si tiene sólo mi código habilitado, el depurador ni siquiera se intente y cargar los símbolos para archivos DLL que se optimizan. Buscar símbolos puede tardar mucho tiempo.

**Limitaciones de esta opción:** hay dos situaciones en las que esta opción realizará **no** de trabajo:

1. En situaciones donde se va a adjuntar el depurador a un proceso ya se está ejecutando, esta opción tendrá ningún efecto en los módulos que ya estaban cargados en el momento en que se asocia el depurador.
2. Esta opción no tiene ningún efecto en las DLL que se han compilado previamente (conocidos también como con Ngen) a código nativo. Sin embargo, puede deshabilitar el uso del código compilado previamente, inicie el proceso con el entorno de que variable 'COMPlus_ZapDisable' establecida en '1'.

## <a name="see-also"></a>Vea también  
 [Depurar código administrado](../debugger/debugging-managed-code.md)   
 [Desplazarse por el código con el depurador](../debugger/navigating-through-code-with-the-debugger.md)   
 [Adjuntar a procesos en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Proceso de ejecución administrada](/dotnet/standard/managed-execution-process)
