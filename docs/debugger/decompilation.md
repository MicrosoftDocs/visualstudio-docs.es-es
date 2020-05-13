---
title: Descompilar código .NET durante la depuración de la aplicación . Microsoft Docs
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
ms.openlocfilehash: d63c05120842d52dd54359e128d0cc5f2a195817
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "79508750"
---
# <a name="generate-source-code-from-net-assemblies-while-debugging"></a>Generar código fuente a partir de ensamblados .NET durante la depuración

Al depurar una aplicación .NET, es posible que desee ver el código fuente que no tiene. Por ejemplo, interrumpir una excepción o usar la pila de llamadas para navegar a una ubicación de origen.

> [!NOTE]
> * La generación de código fuente (descompilación) solo está disponible para aplicaciones .NET y se basa en el proyecto [ILSpy](https://github.com/icsharpcode/ILSpy) de código abierto.
> * La descompilación solo está disponible en Visual Studio 2019 16.5 y versiones posteriores.
> * Aplicar el atributo [SuppressIldasmAttribute](https://docs.microsoft.com/dotnet/api/system.runtime.compilerservices.suppressildasmattribute) a un ensamblado o módulo impide que Visual Studio intente la descompilación.

## <a name="generate-source-code"></a>Generar código fuente

Cuando se está depurando y no hay código fuente disponible, Visual Studio muestra el documento **Origen no encontrado** o, si no tiene símbolos para el ensamblado, el documento **Sin símbolos cargados.** Ambos documentos tienen una opción **de código fuente de descompilación** que genera código de C- para la ubicación actual. A continuación, se puede usar el código generado de C- como cualquier otro código fuente. Puede ver el código, inspeccionar variables, establecer puntos de interrupción, etc.

### <a name="no-symbols-loaded"></a>Sin símbolos cargados

En la ilustración siguiente se muestra el mensaje **Sin símbolos cargados.**

![Captura de pantalla de ningún documento cargado de símbolos](media/decompilation-no-symbol-found.png)

### <a name="source-not-found"></a>Fuente no encontrada

En la ilustración siguiente se muestra el mensaje **Origen no encontrado.**

![Captura de pantalla del documento no encontrado](media/decompilation-no-source-found.png)

## <a name="generate-and-embed-sources-for-an-assembly"></a>Generar e incrustar fuentes para un ensamblado

Además de generar código fuente para una ubicación específica, puede generar todo el código fuente para un ensamblado .NET determinado. Para ello, vaya a la ventana **Módulos** y, en el menú contextual de un ensamblado .NET, y, a continuación, seleccione el comando **Decompilar código fuente.** Visual Studio genera un archivo de símbolos para el ensamblado y, a continuación, incrusta el origen en el archivo de símbolos. En un paso posterior, puede [extraer](#extract-and-view-the-embedded-source-code) el código fuente incrustado.

![Captura de pantalla del menú contextual del ensamblado en la ventana de módulos con el comando de descompilar source.](media/decompilation-decompile-source-code.png)

## <a name="extract-and-view-the-embedded-source-code"></a>Extraiga y vea el código fuente incrustado

Puede extraer archivos de origen incrustados en un archivo de símbolos mediante el comando **Extraer código fuente** en el menú contextual de la ventana **Módulos.**

![Captura de pantalla del menú contextual del ensamblaje en la ventana de módulos con el comando extraer orígenes.](media/decompilation-extract-source-code.png)

Los archivos de origen extraídos se agregan a la solución como [archivos varios.](../ide/reference/miscellaneous-files.md) La característica de archivos varios está desactivada de forma predeterminada en Visual Studio. Puede habilitar esta característica desde **la** > casilla de verificación**Documentos** > de**entorno** > de**opciones** > de herramientas**Mostrar archivos varios en** el Explorador de soluciones. Sin habilitar esta característica, no podrá abrir el código fuente extraído.

![Captura de pantalla de la página de opciones de herramientas con varios archivos opción habilitada.](media/decompilation-tools-options-misc-files.png)

Los archivos de origen extraídos aparecen en los archivos varios del **Explorador**de soluciones.

![Captura de pantalla del explorador de soluciones con varios archivos.](media/decompilation-solution-explorer.png)

## <a name="known-limitations"></a>Restricciones conocidas

### <a name="requires-break-mode"></a>Requiere modo de interrupción

La generación de código fuente mediante la descompilación solo es posible cuando el depurador está en modo de interrupción y la aplicación está en pausa. Por ejemplo, Visual Studio entra en modo de interrupción cuando alcanza un punto de interrupción o una excepción. Puede desencadenar fácilmente Visual Studio para interrumpir la próxima vez![que se](media/decompilation-break-all.png)ejecute el código mediante el comando **Romper todo** ( Romper todo icono ).

### <a name="decompilation-limitations"></a>Limitaciones de descompilación

La generación de código fuente a partir del formato intermedio (IL) que se usa en ensamblados .NET tiene algunas limitaciones inherentes. Como tal, el código fuente generado no se parece al código fuente original. La mayoría de las diferencias se encuentran en lugares donde la información del código fuente original no es necesaria en tiempo de ejecución. Por ejemplo, la información como espacios en blanco, comentarios y los nombres de variables locales no es necesaria en tiempo de ejecución. Se recomienda usar el origen generado para comprender cómo se ejecuta el programa y no como un reemplazo para el código fuente original.

### <a name="debug-optimized-or-release-assemblies"></a>Depurar ensamblados optimizados o de versión

Al depurar código que se descompiló de un ensamblado compilado mediante optimizaciones del compilador, puede encontrarse con los siguientes problemas:
- Es posible que los puntos de interrupción no siempre se enlacen a la ubicación de abastecimiento coincidente.
- Es posible que no siempre se pase a la ubicación correcta.
- Es posible que las variables locales no tengan nombres precisos.
- Es posible que algunas variables no estén disponibles para su evaluación.

Puede encontrar más detalles en el problema de GitHub: [integración ICSharpCode.Decompiler en VS Debugger](https://github.com/icsharpcode/ILSpy/issues/1901).

### <a name="decompilation-reliability"></a>Fiabilidad de la descompilación

Un porcentaje relativamente pequeño de intentos de descompilación puede dar lugar a un error. Esto se debe a un error de referencia nula de punto de secuencia en ILSpy.  Hemos mitigado el error detectando estos problemas y fallando correctamente el intento de descompilación.

Puede encontrar más detalles en el problema de GitHub: [integración ICSharpCode.Decompiler en VS Debugger](https://github.com/icsharpcode/ILSpy/issues/1901).

### <a name="limitations-with-async-code"></a>Limitaciones con código asincrónico

Los resultados de la descompilación de módulos con patrones de código asincrónico/await pueden estar incompletos o fallar por completo. La implementación de ILSpy de máquinas de estado async/await y yield solo se implementa parcialmente. 

Puede encontrar más detalles en el problema de GitHub: [PDB Generator Status](https://github.com/icsharpcode/ILSpy/issues/1422).

### <a name="just-my-code"></a>Solo mi código

La configuración de [Solo mi código (JMC)](https://docs.microsoft.com/visualstudio/debugger/just-my-code) permite a Visual Studio pasar por encima del sistema, el marco de trabajo, la biblioteca y otras llamadas no gubernamentales. Durante una sesión de depuración, la ventana **Módulos** muestra qué módulos de código trata el depurador como Mi código (código de usuario).

La descompilación de módulos optimizados o de versión produce código que no es de usuario. Si el depurador se interrumpe en el código no de usuario descompilado, por ejemplo, aparece la ventana **Sin origen.** Para deshabilitar Solo mi código, vaya a**Opciones** de **herramientas** > (u**Opciones**de **depuración** > ) > **Depuración** > **general**y, a continuación, anule la selección de Habilitar solo **mi código**.

### <a name="extracted-sources"></a>Fuentes extraídas

El código fuente extraído de un ensamblado tiene las siguientes limitaciones:
- El nombre y la ubicación de los archivos generados no son configurables.
- Los archivos son temporales y Visual Studio los eliminará.
- Los archivos se colocan en una sola carpeta y no se utiliza ninguna jerarquía de carpetas que tuvieran los orígenes originales.
- El nombre de archivo de cada archivo contiene un hash de suma de comprobación del archivo.

### <a name="generated-code-is-c-only"></a>El código generado es sólo en C-
La descompilación solo genera archivos de código fuente en C. No hay ninguna opción para generar archivos en cualquier otro idioma.
