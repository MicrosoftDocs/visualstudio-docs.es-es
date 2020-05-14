---
title: Optimización y depuración JIT | Microsoft Docs
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
ms.openlocfilehash: ae11860aaa64448cd4d23b5602cf4c2da1575ce3
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2020
ms.locfileid: "75916221"
---
# <a name="jit-optimization-and-debugging"></a>Optimización y depuración JIT
Si intenta depurar código, resulta más fácil cuando ese código **no** está optimizado. Cuando se optimiza el código, el compilador y el tiempo de ejecución realizan cambios en el código de CPU emitido para que se ejecute más rápido, pero tiene una asignación menos directa al código fuente original. Si la asignación es menos directa, los depuradores a menudo no pueden indicarle el valor de las variables locales, y es posible que los puntos de interrupción y la ejecución de código no funcionen como se espera.

> [!NOTE]
> Para más información sobre la depuración JIT (Just-In-Time), lea [esta documentación](../debugger/debug-using-the-just-in-time-debugger.md).

## <a name="how-optimizations-work-in-net"></a>Funcionamiento de las optimizaciones en .NET 
Normalmente, la configuración de compilación de versión crea código optimizado y la configuración de compilación de depuración no. La propiedad `Optimize` de MSBuild controla si se indica al compilador que optimice el código.

En el ecosistema de .NET, el código se convierte de las instrucciones de origen a las de la CPU en un proceso de dos pasos: en primer lugar, el compilador de C# convierte el texto que se escribe a un formato binario intermedio denominado MSIL y escribe el MSIL en los archivos .dll. Después, .NET Runtime convierte este MSIL en instrucciones de CPU. Ambos pasos se pueden optimizar hasta cierto punto, pero el segundo paso que .NET Runtime realiza lleva a cabo las optimizaciones más significativas.

## <a name="the-suppress-jit-optimization-on-module-load-managed-only-option"></a>Opción "Suprimir optimización JIT al cargar el módulo (solo administrado)"
El depurador expone una opción que controla lo que ocurre cuando un archivo DLL que se compila con optimizaciones habilitadas se carga dentro del proceso de destino. Si esta opción está desactivada (el estado predeterminado), cuando .NET Runtime compila el código MSIL en el código de CPU, deja las optimizaciones habilitadas. Si la opción está activada, el depurador solicita que se deshabiliten las optimizaciones.

Para buscar la opción **Suprimir optimización JIT al cargar el módulo (solo administrado)** , seleccione **Herramientas** > **Opciones** y luego la página **General** del nodo **Depuración**.

![Suprimir optimización JIT](../debugger/media/suppress-jit-tool-options.png "Suprimir optimización JIT")

## <a name="when-should-you-check-the-suppress-jit-optimization-option"></a>¿Cuándo se debe activar la opción "Suprimir optimización JIT"?
Active esta opción si descargó los archivos DLL de otro origen, como un paquete NuGet, y quiere depurar el código en este archivo DLL. Para que la supresión funcione, debe buscar también el archivo de símbolos (.pdb) para este archivo DLL.

Si solo le interesa depurar el código que está compilando localmente, es mejor dejar esta opción desactivada, ya que, en algunos casos, la habilitación de esta opción ralentizará considerablemente la depuración. Hay dos motivos para esta ralentización:

* El código optimizado se ejecuta más rápido. Si va a desactivar las optimizaciones de gran cantidad de código, el impacto en el rendimiento puede ser mayor.
* Si ha habilitado Solo mi código, el depurador ni siquiera intentará cargar símbolos para los archivos DLL que estén optimizados. La búsqueda de símbolos puede tardar mucho.

## <a name="limitations-of-the-suppress-jit-optimization-option"></a>Limitaciones de la opción "Suprimir optimización JIT" 
Hay dos situaciones en las que la activación de esta opción **no** funcionará:

1. En situaciones en las que se asocia el depurador a un proceso ya en ejecución, esta opción no tendrá ningún efecto sobre los módulos que ya estaban cargados el momento en que se asoció el depurador.
2. Esta opción no tiene ningún efecto en los archivos DLL que se han precompilado (también conocidos como ngen'ed) en el código nativo. Aunque se puede deshabilitar el uso de código precompilado iniciando el proceso con la variable de entorno **"COMPlus_ReadyToRun"** establecida en **"0"** . Esto le indicará .NET Core Runtime que deshabilite el uso de imágenes precompiladas, que obliga al runtime a compilar código de marco JIT. 

    > [!IMPORTANT]
    > Si tiene como destino .NET Framework o una versión anterior de .NET Core (2.x o inferior), agregue también la variable de entorno "COMPlus_ZapDisable" y establézcala en "1".

    **Para establecer una variable de entorno para un proyecto de .NET Core en Visual Studio:**
    1. En el **Explorador de soluciones**, **haga clic con el botón derecho** en el proyecto y seleccione **Propiedades**.
    2. Vaya a la pestaña **Depurar** y, en **Variables de entorno**, haga clic en el botón **Agregar**.
    3. Establezca Nombre (clave) en **COMPlus_ReadyToRun** y establezca el valor en **0**.

    ![Establecimiento de la variable de entorno COMPlus_ReadyToRun](../debugger/media/environment-variables-debug-menu.png "Establecimiento de la variable de entorno COMPlus_ReadyToRun")

## <a name="see-also"></a>Vea también
- [Depuración de código fuente de DotNet Framework](../debugger/how-to-debug-dotnet-framework-source.md)
- [Depurar código administrado](../debugger/debugging-managed-code.md)
- [Desplazarse por el código con el depurador](../debugger/navigating-through-code-with-the-debugger.md)
- [Asociar a procesos en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Proceso de ejecución administrada](/dotnet/standard/managed-execution-process)
