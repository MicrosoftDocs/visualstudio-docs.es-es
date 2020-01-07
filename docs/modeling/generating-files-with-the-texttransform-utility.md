---
title: Generar archivos con la utilidad TextTransform
ms.date: 07/26/2019
ms.topic: conceptual
helpviewer_keywords:
- text templates, TextTransform utility
- TextTransform.exe
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7ec659bfee9253dfb198c2747e1b5d7fb6b78f2b
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596559"
---
# <a name="generate-files-with-the-texttransform-utility"></a>Generar archivos con la utilidad TextTransform

TextTransform.exe es una herramienta de línea de comandos que puede usar para transformar una plantilla de texto. Cuando se llama a TextTransform.exe, especifique el nombre de un archivo de plantilla de texto como argumento. TextTransform.exe llama al motor de transformación de texto y procesa la plantilla de texto. Normalmente se denomina TextTransform.exe desde secuencias de comandos. Sin embargo, no se suelen ser necesario, ya que puede realizar la transformación de texto en Visual Studio o en el proceso de compilación.

> [!NOTE]
> Si desea realizar la transformación de texto como parte de un proceso de compilación, considere el uso de la tarea de transformación de texto de MSBuild. Para obtener más información, consulte [generación de código en un proceso de compilación](../modeling/code-generation-in-a-build-process.md). En una máquina donde está instalado Visual Studio, también puede escribir una aplicación o extensión de Visual Studio que puede transformar plantillas de texto. Para obtener más información, consulte [de procesamiento de plantillas de texto mediante el uso de un Host personalizado](../modeling/processing-text-templates-by-using-a-custom-host.md).

TextTransform.exe se encuentra en el directorio siguiente:

::: moniker range=">=vs-2019"

**\Archivos de programa (x86) \Microsoft Visual Studio\2019\Professional\Common7\IDE**

para la edición Professional, o

**\Archivos de programa (x86) \Microsoft Visual Studio\2019\Enterprise\Common7\IDE**

para Enterprise Edition.

::: moniker-end

::: moniker range="vs-2017"

**\Program archivos (x86) \Microsoft Visual Studio\2017\Professional\Common7\IDE**

para la edición Professional, o

**\Program archivos (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE**

para Enterprise Edition.

En versiones anteriores de Visual Studio, el archivo se encuentra en la siguiente ubicación:

**\Program archivos (x86) \Common Shared\TextTemplating\{versión}**

donde {versión} depende de la versión anterior instalada.

::: moniker-end

## <a name="syntax"></a>Sintaxis

```
TextTransform [<options>] <templateName>
```

### <a name="parameters"></a>Parameters

|**Argumento**|**Descripción**|
|-|-|
|`templateName`|Identifica el nombre del archivo de plantilla que desee transformar.|

|**Opción**|**Descripción**|
|-|-|
|**-out** \<nombreDeArchivo >|El archivo que se escribe la salida de la transformación.|
|**-r** \<assembly>|Un ensamblado que se utiliza para compilar y ejecutar la plantilla de texto.|
|**-u** \<namespace>|Un espacio de nombres que se utiliza para compilar la plantilla.|
|**-I** \<includedirectory>|Un directorio que contiene las plantillas de texto incluidas en la plantilla de texto especificado.|
|**-P** \<referencepath>|Un directorio para buscar los ensamblados especificados en la plantilla de texto o utilizando el **- r** opción.<br /><br /> Por ejemplo, para incluir ensamblados que se utiliza para la API de Visual Studio, use lo siguiente:<br /><br /> `-P "%VSSHELLFOLDER%\Common7\IDE\PublicAssemblies"`|
|**-dp** \<processorName>!\<className>!\<assemblyName&#124;codeBase>|El nombre, el nombre de tipo completo y el ensamblado de un procesador de directivas que se puede usar para procesar las directivas personalizadas dentro de la plantilla de texto.|
|**-a** [processorName]. [ ¡directiveName]! \<parameterName >! \<parameterValue >|Especifique un valor de parámetro para un procesador de directivas. Si especifica únicamente el nombre de parámetro y valor, el parámetro estará disponible para todos los procesadores de directivas. Si especifica un procesador de directivas, el parámetro está disponible solo para el procesador especificado. Si especifica un nombre de directiva, el parámetro está disponible solo cuando se procesa la directiva especificada.<br /><br /> Para obtener acceso a los valores de parámetro de una plantilla de texto o un procesador de directivas, utilice [ITextTemplatingEngineHost.ResolveParameterValue](/previous-versions/visualstudio/visual-studio-2012/bb126369\(v\=vs.110\)). En una plantilla de texto, incluya `hostspecific` en la directiva de plantilla e invocar el mensaje en `this.Host`. Por ejemplo:<br /><br /> `<#@template language="c#" hostspecific="true"#> [<#= this.Host.ResolveParameterValue("", "", "parameterName") #>]`.<br /><br /> Escriba siempre el '!' marca, incluso si se omiten el procesador opcional y nombres de directiva. Por ejemplo:<br /><br /> `-a !!param!value`|
|**-h**|Proporciona ayuda.|

## <a name="related-topics"></a>Temas relacionados

|Tarea|Tema|
|-|-|
|Generar archivos en una solución de Visual Studio.|[Generación de código en tiempo de diseño mediante plantillas de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|
|Escriba procesadores de directivas para transformar sus propios orígenes de datos.|[Personalizar la transformación de texto T4](../modeling/customizing-t4-text-transformation.md)|
|Escribir un host de plantillas de texto que permite invocar las plantillas de texto desde su propia aplicación.|[Procesar las plantillas de texto mediante un host personalizado](../modeling/processing-text-templates-by-using-a-custom-host.md)|
