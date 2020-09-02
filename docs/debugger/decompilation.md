---
title: Descompilación de código de .NET durante la depuración | Microsoft Docs
ms.date: 2/2/2020
ms.topic: how-to
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
ms.openlocfilehash: b7d9ed2f2ceeae21b85fdb8227e65715cb07bc8b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85350568"
---
# <a name="generate-source-code-from-net-assemblies-while-debugging"></a>Generación de código fuente a partir de ensamblados .NET durante la depuración

Al depurar una aplicación .NET, es posible que desee ver el código fuente que no tiene. Por ejemplo, la interrupción de una excepción o el uso de la pila de llamadas para navegar a una ubicación de origen.

> [!NOTE]
> * La generación de código fuente (descompilación) solo está disponible para aplicaciones de .NET y se basa en el proyecto de código abierto [ILSpy](https://github.com/icsharpcode/ILSpy).
> * La descompilación solo está disponible en Visual Studio 2019 16.5 y versiones posteriores.
> * La aplicación del atributo [SuppressIldasmAttribute](https://docs.microsoft.com/dotnet/api/system.runtime.compilerservices.suppressildasmattribute) a un ensamblado o un módulo impide que Visual Studio intente descompilar.

## <a name="generate-source-code"></a>Generación de código fuente

Cuando está depurando y no hay código fuente disponible, Visual Studio muestra el documento **Código fuente no encontrado** o, si no tiene símbolos para el ensamblado, el documento **No se cargaron símbolos**. Ambos documentos tienen una opción para **descompilar código fuente** que genera código de C# para la ubicación actual. El código de C# generado se puede usar como cualquier otro código fuente. Puede ver el código, inspeccionar las variables, establecer puntos de interrupción, etc.

### <a name="no-symbols-loaded"></a>No se cargaron símbolos

En la ilustración siguiente se muestra el mensaje **No se cargaron símbolos**.

![Captura de pantalla del documento No se cargaron símbolos](media/decompilation-no-symbol-found.png)

### <a name="source-not-found"></a>Código fuente no encontrado

En la ilustración siguiente se muestra el mensaje **Código fuente no encontrado**.

![Captura de pantalla del documento Código fuente no encontrado](media/decompilation-no-source-found.png)

## <a name="generate-and-embed-sources-for-an-assembly"></a>Generación e inserción de códigos fuente para un ensamblado

Además de generar código fuente para una ubicación específica, puede generar todo el código fuente de un ensamblado de .NET determinado. Para ello, vaya a la ventana **Módulos** y, en el menú contextual de un ensamblado de .NET y, seleccione el comando **Decompile source code** (Descompilar código fuente). Visual Studio genera un archivo de símbolos para el ensamblado y, a continuación, inserta el origen en el archivo de símbolos. En un paso posterior, puede [extraer](#extract-and-view-the-embedded-source-code) el código fuente insertado.

![Captura de pantalla del menú contextual del ensamblado en la ventana de módulos con el comando para descompilar código fuente.](media/decompilation-decompile-source-code.png)

## <a name="extract-and-view-the-embedded-source-code"></a>Extracción y visualización del código fuente insertado

Puede extraer los archivos de código fuente que están insertados en un archivo de símbolos mediante el comando **Extract Source Code** (Extraer código fuente) en el menú contextual de la ventana **Módulos**.

![Captura de pantalla del menú contextual del ensamblado en la ventana módulos con el comando para extraer orígenes.](media/decompilation-extract-source-code.png)

Los archivos de origen extraídos se agregan a la solución como [archivos varios](../ide/reference/miscellaneous-files.md). La característica de archivos varios está desactivada de forma predeterminada en Visual Studio. Puede habilitar esta casilla con la casilla **Herramientas** > **Opciones** > **Entorno** > **Documentos** > **Mostrar archivos varios en el Explorador de soluciones**. Sin habilitar esta característica, no podrá abrir el código fuente extraído.

![Captura de pantalla de la página de opciones de herramientas con la opción archivos varios habilitada.](media/decompilation-tools-options-misc-files.png)

Los archivos de código fuente extraídos aparecen en los archivos varios del **Explorador de soluciones**.

![Captura de pantalla del explorador de soluciones con varios archivos.](media/decompilation-solution-explorer.png)

## <a name="known-limitations"></a>Limitaciones conocidas

### <a name="requires-break-mode"></a>Requisito del modo de interrupción

La generación de código fuente mediante la descompilación solo es posible cuando el depurador está en modo de interrupción y la aplicación está en pausa. Por ejemplo, Visual Studio entra en modo de interrupción cuando alcanza un punto de interrupción o una excepción. Puede desencadenar fácilmente Visual Studio para que ejecute la interrupción la próxima vez que se ejecute el código mediante el comando **Interrumpir todos** (![icono Interrumpir todos](media/decompilation-break-all.png)).

### <a name="decompilation-limitations"></a>Limitaciones de descompilación

La generación de código fuente a partir del formato intermedio (IL) que se usa en los ensamblados .NET tiene algunas limitaciones inherentes. Como tal, el código fuente generado no se parece al código fuente original. La mayoría de las diferencias radican en los lugares en los que la información del código fuente original no es necesaria en el entorno de ejecución. Por ejemplo, la información como el espacio en blanco, los comentarios y los nombres de las variables locales no son necesarias en el entorno de ejecución. Se recomienda usar el código fuente generado para entender cómo se ejecuta el programa y no como sustituto del código fuente original.

### <a name="debug-optimized-or-release-assemblies"></a>Depuración de ensamblados optimizados o de versión

Al depurar el código que se descompiló de un ensamblado que se compiló mediante las optimizaciones del compilador, pueden aparecer los siguientes problemas:
- Es posible que los puntos de interrupción no siempre se enlacen a la ubicación de origen coincidente.
- La ejecución paso a paso no siempre puede conducir a la ubicación correcta.
- Es posible que las variables locales no tengan nombres precisos.
- Es posible que algunas variables no estén disponibles para su evaluación.

Se puede encontrar más información en el problema de GitHub: [Integración de ICSharpCode.Decompiler en el depurador de VS](https://github.com/icsharpcode/ILSpy/issues/1901).

### <a name="decompilation-reliability"></a>Confiabilidad de la descompilación

Un porcentaje relativamente pequeño de intentos de descompilación puede producir un error. Esto se debe a un error de referencia nula de punto de secuencia en ILSpy.  Hemos mitigado el error detectando estos problemas y degradando correctamente el intento de descompilación.

Se puede encontrar más información en el problema de GitHub: [Integración de ICSharpCode.Decompiler en el depurador de VS](https://github.com/icsharpcode/ILSpy/issues/1901).

### <a name="limitations-with-async-code"></a>Limitaciones del código asincrónico

Los resultados de la descompilación de módulos con patrones de código async/await pueden estar incompletos o no funcionar correctamente. La implementación de ILSpy de máquinas de estado de async/await y solo se implementa parcialmente. 

Se puede encontrar más información en el problema de GitHub: [Estado del generador de PDB](https://github.com/icsharpcode/ILSpy/issues/1422).

### <a name="just-my-code"></a>Solo mi código

La configuración de [Solo mi código](https://docs.microsoft.com/visualstudio/debugger/just-my-code) permite que Visual Studio depure paso a paso por instrucciones el sistema, el marco, la biblioteca y otras llamadas que no son de usuario. Durante una sesión de depuración, la ventana **Módulos** muestra los módulos de código que el depurador trata como mi código (código de usuario).

La descompilación de módulos optimizados o de versión genera código que no es de usuario. Si el depurador interrumpe el código descompilado que no es de usuario, por ejemplo, aparecerá la ventana **No hay origen**. Para deshabilitar Solo mi código, vaya a **Herramientas** > **Opciones** (o **Depurar** > **Opciones**) > **Depuración** > **General** y, a continuación, anule la selección de **Habilitar Solo mi código**.

### <a name="extracted-sources"></a>Códigos fuente extraídos

El código fuente extraído de un ensamblado tiene las siguientes limitaciones:
- El nombre y la ubicación de los archivos generados no son configurables.
- Los archivos son temporales y se eliminarán por Visual Studio.
- Los archivos se colocan en una sola carpeta y no se utiliza ninguna jerarquía de carpetas que tenían los códigos fuente originales.
- El nombre de archivo de cada archivo contiene un hash de suma de comprobación del archivo.

### <a name="generated-code-is-c-only"></a>El código generado es solo de C#.
La descompilación solo genera archivos de código fuente en C#. No hay ninguna opción para generar archivos en ningún otro lenguaje.
