---
title: Generar archivos con la utilidad TextTransform
description: Obtenga información sobre cómo la utilidad TextTransform es una herramienta de línea de comandos que puede usar para transformar una plantilla de texto.
ms.custom: SEO-VS-2020
ms.date: 07/26/2019
ms.topic: conceptual
helpviewer_keywords:
- text templates, TextTransform utility
- TextTransform.exe
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 743b7deb118bb3506773ec1a82d2331633afa7bc
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388833"
---
# <a name="generate-files-with-the-texttransform-utility"></a>Generación de archivos con la utilidad TextTransform

TextTransform.exe es una herramienta de línea de comandos que puede usar para transformar una plantilla de texto. Al llamar a TextTransform.exe, especifique el nombre de un archivo de plantilla de texto como argumento. TextTransform.exe llama al motor de transformación de texto y procesa la plantilla de texto. TextTransform.exe normalmente se llama desde scripts. Sin embargo, no suele ser necesario, ya que puede realizar la transformación de texto en Visual Studio o en el proceso de compilación.

> [!NOTE]
> Si desea realizar la transformación de texto como parte de un proceso de compilación, considere la posibilidad de usar la tarea de transformación de texto de MSBuild. Para obtener más información, vea [Generación de código en un proceso de compilación.](../modeling/code-generation-in-a-build-process.md) En un equipo en el que Visual Studio esté instalado, también puede escribir una aplicación o una Visual Studio que pueda transformar plantillas de texto. Para obtener más información, vea [Procesar plantillas de texto mediante un host personalizado.](../modeling/processing-text-templates-by-using-a-custom-host.md)

TextTransform.exe se encuentra en el directorio siguiente:

::: moniker range=">=vs-2019"

**\Archivos de programa (x86)\Microsoft Visual Studio\2019\Professional\Common7\IDE**

para la edición Professional o

**\Archivos de programa (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE**

para Enterprise Edition.

::: moniker-end

::: moniker range="vs-2017"

**\Archivos de programa (x86)\Microsoft Visual Studio\2017\Professional\Common7\IDE**

para la edición Professional o

**\Archivos de programa (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE**

para Enterprise Edition.

En versiones anteriores de Visual Studio, el archivo se encuentra en la siguiente ubicación:

**\Archivos de programa (x86)\Common Files\Microsoft Shared\TextTemplating \{ version}**

donde {version} depende de la versión anterior instalada.

::: moniker-end

## <a name="syntax"></a>Sintaxis

```
TextTransform [<options>] <templateName>
```

### <a name="parameters"></a>Parámetros

|**Argument**|**Descripción**|
|-|-|
|`templateName`|Identifica el nombre del archivo de plantilla que desea transformar.|

|**Opción**|**Descripción**|
|-|-|
|**-out**\<filename>|Archivo en el que se escribe la salida de la transformación.|
|**-r**\<assembly>|Ensamblado que se usa para compilar y ejecutar la plantilla de texto.|
|**-u**\<namespace>|Espacio de nombres que se usa para compilar la plantilla.|
|**-I**\<includedirectory>|Directorio que contiene las plantillas de texto incluidas en la plantilla de texto especificada.|
|**-P**\<referencepath>|Directorio para buscar ensamblados especificados en la plantilla de texto o para usar la **opción -r.**<br /><br /> Por ejemplo, para incluir ensamblados usados para la API Visual Studio, use<br /><br /> `-P "%VSSHELLFOLDER%\Common7\IDE\PublicAssemblies"`|
|**-dp** \<processorName> ! \<className> !\<assemblyName&#124;codeBase>|Nombre, nombre de tipo completo y ensamblado de un procesador de directivas que se puede usar para procesar directivas personalizadas dentro de la plantilla de texto.|
|**-a** [processorName]! [directiveName]! \<parameterName> !\<parameterValue>|Especifique un valor de parámetro para un procesador de directivas. Si especifica solo el nombre y el valor del parámetro, el parámetro estará disponible para todos los procesadores de directivas. Si especifica un procesador de directivas, el parámetro solo está disponible para el procesador especificado. Si especifica un nombre de directiva, el parámetro solo está disponible cuando se procesa la directiva especificada.<br /><br /> Para acceder a los valores de parámetro desde un procesador de directivas o una plantilla de texto, use [ITextTemplatingEngineHost.ResolveParameterValue](/previous-versions/visualstudio/visual-studio-2012/bb126369\(v\=vs.110\)). En una plantilla de texto, incluya `hostspecific` en la directiva de plantilla e invoque el mensaje en `this.Host` . Por ejemplo:<br /><br /> `<#@template language="c#" hostspecific="true"#> [<#= this.Host.ResolveParameterValue("", "", "parameterName") #>]`.<br /><br /> Escriba siempre las marcas "!", incluso si omite los nombres opcionales de procesador y directiva. Por ejemplo:<br /><br /> `-a !!param!value`|
|**-h**|Proporciona ayuda.|

## <a name="related-topics"></a>Temas relacionados

|Tarea|Tema|
|-|-|
|Generar archivos en una Visual Studio solución.|[Generación de código en tiempo de diseño usando las plantillas de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|
|Escriba procesadores de directivas para transformar sus propios orígenes de datos.|[Personalizar la transformación de texto T4](../modeling/customizing-t4-text-transformation.md)|
|Escriba un host de plantillas de texto que le permita invocar plantillas de texto desde su propia aplicación.|[Procesar las plantillas de texto mediante un host personalizado](../modeling/processing-text-templates-by-using-a-custom-host.md)|
