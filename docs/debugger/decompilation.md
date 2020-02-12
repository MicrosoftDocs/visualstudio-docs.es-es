---
title: Descompilar código .NET durante la depuración | Microsoft Docs
ms.date: 2/2/2020
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- decompilation, debugger, exception
- debugging [Visual Studio], decompilation, source not found
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.openlocfilehash: 5087c439533aa447708d0f1bfae653054fd16089
ms.sourcegitcommit: a86ee68e3ec23869b6eaaf6c6b7946b1d9a88d01
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77144783"
---
# <a name="generate-source-code-from-net-assemblies-while-debugging"></a>Generar código fuente a partir de ensamblados .NET durante la depuración

Al depurar una aplicación .NET, es posible que desee ver el código fuente que no tiene. Por ejemplo, interrumpir una excepción o utilizar la pila de llamadas para navegar a una ubicación de origen.

> [!NOTE]
> * La generación de código fuente (descompilación) solo está disponible para aplicaciones .NET y se basa en el proyecto [ILSpy](https://github.com/icsharpcode/ILSpy) de código abierto.
> * La descompilación solo está disponible en Visual Studio 2019 16,5 y versiones posteriores.

## <a name="generate-source-code"></a>Generar código fuente

Al depurar y no hay código fuente disponible, Visual Studio muestra el documento **origen no encontrado** , o si no tiene símbolos para el ensamblado, el documento **no se ha cargado ningún símbolo** . Ambos documentos tienen una opción de **código fuente descompilado** que genera C# código para la ubicación actual. El código C# generado se puede usar como cualquier otro código fuente. Puede ver el código, inspeccionar las variables, establecer puntos de interrupción, etc.

### <a name="no-symbols-loaded"></a>No se cargaron símbolos

En la ilustración siguiente se muestra el mensaje **no se cargaron símbolos** .

![Captura de pantalla de ningún documento cargado de símbolos](media/decompilation-no-symbol-found.png)

### <a name="source-not-found"></a>Origen no encontrado

En la ilustración siguiente se muestra el mensaje **origen no encontrado** .

![Captura de pantalla del documento de origen no encontrado](media/decompilation-no-source-found.png)

## <a name="generate-and-embed-sources-for-an-assembly"></a>Generar e insertar orígenes para un ensamblado

Además de generar código fuente para una ubicación específica, puede generar todo el código fuente de un ensamblado .NET determinado. Para ello, vaya a la ventana **módulos** y, en el menú contextual de un ensamblado .net, y seleccione el comando **descompilar código fuente** . Visual Studio genera un archivo de símbolos para el ensamblado y, a continuación, inserta el origen en el archivo de símbolos. En un paso posterior, puede [extraer](#extract-and-view-the-embedded-source-code) el código fuente incrustado.

![Captura de pantalla del menú contextual del ensamblado en la ventana módulos con el comando descompilar código fuente.](media/decompilation-decompile-source-code.png)

## <a name="extract-and-view-the-embedded-source-code"></a>Extracción y visualización del código fuente incrustado

Puede extraer los archivos de código fuente que están incrustados en un archivo de símbolos mediante el comando **extraer código fuente** del menú contextual de la ventana **módulos** .

![Captura de pantalla del menú contextual del ensamblado en la ventana módulos con el comando extraer orígenes.](media/decompilation-extract-source-code.png)

Los archivos de código fuente extraídos se agregan a la solución como [archivos varios](../ide/reference/miscellaneous-files.md). La característica archivos varios está desactivada de forma predeterminada en Visual Studio. Puede habilitar esta característica en la casilla **herramientas** > **opciones** > **entorno** > **documentos** > **Mostrar archivos varios en explorador de soluciones** . Sin habilitar esta característica, no podrá abrir el código fuente extraído.

![Captura de pantalla de la página de opciones de herramientas con la opción archivos varios habilitada.](media/decompilation-tools-options-misc-files.png)

Los archivos de código fuente extraídos aparecen en los archivos varios de **Explorador de soluciones**.

![Captura de pantalla del explorador de soluciones con varios archivos.](media/decompilation-solution-explorer.png)

## <a name="known-limitations"></a>Restricciones conocidas

### <a name="requires-break-mode"></a>Requiere el modo de interrupción

La generación de código fuente mediante la descompilación solo es posible cuando el depurador está en modo de interrupción y la aplicación está en pausa. Por ejemplo, Visual Studio entra en modo de interrupción cuando alcanza un punto de interrupción o una excepción. Puede desencadenar fácilmente Visual Studio para interrumpir la próxima vez que se ejecute el código mediante el comando **interrumpir todo** (![icono interrumpir todo](media/decompilation-break-all.png)).

### <a name="decompilation-limitations"></a>Limitaciones de descompilación

La generación de código fuente a partir del formato intermedio (IL) que se usa en los ensamblados .NET tiene algunas limitaciones inherentes. Como tal, el código fuente generado no se parece al código fuente original. La mayoría de las diferencias se encuentran en los lugares en los que la información del código fuente original no es necesaria en tiempo de ejecución. Por ejemplo, la información como el espacio en blanco, los comentarios y los nombres de las variables locales no son necesarias en tiempo de ejecución. Se recomienda usar el código fuente generado para entender cómo se ejecuta el programa y no como sustituto del código fuente original.

### <a name="debug-optimized-or-release-assemblies"></a>Depuración de ensamblados optimizados o de versión

Al depurar código que se descompiló de un ensamblado que se compiló mediante optimizaciones del compilador, pueden aparecer los siguientes problemas:
- Es posible que los puntos de interrupción no siempre se enlacen a la ubicación de origen coincidente.
- La ejecución paso a paso no siempre puede ir a la ubicación correcta.
- Es posible que las variables locales no tengan nombres precisos.
- Es posible que algunas variables no estén disponibles para su evaluación.

Puede encontrar más detalles en el problema de GitHub: [integración de IChsarpCompiler. descompilador en el depurador de vs](https://github.com/icsharpcode/ILSpy/issues/1901).

### <a name="decompilation-reliability"></a>Confiabilidad de descompilación

Un porcentaje relativamente pequeño de intentos de descompilación puede producir un error. Esto se debe a un error de referencia nula de punto de secuencia en ILSpy.  Hemos mitigado el error detectando estos problemas y produciendo correctamente el intento de descompilación.

Puede encontrar más detalles en el problema de GitHub: [integración de IChsarpCompiler. descompilador en el depurador de vs](https://github.com/icsharpcode/ILSpy/issues/1901).

### <a name="limitations-with-async-code"></a>Limitaciones del código asincrónico

Los resultados de la descompilación de módulos con patrones de código Async/Await pueden estar incompletos o no funcionar correctamente. La implementación de ILSpy de Async/Await y yield State-machines solo se implementa parcialmente. 

Puede encontrar más detalles en el problema de GitHub: [PDB generator status](https://github.com/icsharpcode/ILSpy/issues/1422).

### <a name="just-my-code"></a>Solo mi código

La configuración de [solo mi código (JMC)](https://docs.microsoft.com/visualstudio/debugger/just-my-code) permite a Visual Studio desplazarse por el sistema, el marco de trabajo, la biblioteca y otras llamadas que no son de usuario. Durante una sesión de depuración, la ventana **módulos** muestra los módulos de código que el depurador trata como mi código (código de usuario).

La descompilación de módulos optimizados o de versión genera código que no es de usuario. Si el depurador interrumpe el código descompilado que no es de usuario, por ejemplo, aparecerá la ventana **no hay código fuente** . Para deshabilitar Solo mi código, vaya a **herramientas** > **Opciones** (o **depurar** **Opciones**de > ) > **depuración** > **General**y, a continuación, anule la selección de **Habilitar solo mi código**.

### <a name="extracted-sources"></a>Orígenes extraídos

El código fuente extraído de un ensamblado tiene las siguientes limitaciones:
- El nombre y la ubicación de los archivos generados no son configurables.
- Los archivos son temporales y se eliminarán con Visual Studio.
- Los archivos se colocan en una sola carpeta y en cualquier jerarquía de carpetas que no se hayan usado los orígenes originales.
- El nombre de archivo de cada archivo contiene un hash de suma de comprobación del archivo.

### <a name="generated-code-is-c-only"></a>El código generado C# solo es
La descompilación solo genera archivos de código C#fuente en. No hay ninguna opción para generar archivos en ningún otro lenguaje.