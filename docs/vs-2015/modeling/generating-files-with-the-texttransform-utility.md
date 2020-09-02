---
title: Generar archivos con la utilidad TextTransform | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, TextTransform utility
- TextTransform.exe
ms.assetid: 06a48235-fe02-403e-a1cf-2ae70b4db62f
caps.latest.revision: 43
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 18776795fdf693c855edd3f629d674089daaaebd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72666092"
---
# <a name="generating-files-with-the-texttransform-utility"></a>Generar archivos con la utilidad TextTransform
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

TextTransform.exe es una herramienta de línea de comandos que puede usar para transformar una plantilla de texto. Cuando se llama a TextTransform.exe, se especifica el nombre de un archivo de plantilla de texto como argumento. TextTransform.exe llama al motor de transformación de texto y procesa la plantilla de texto. Normalmente se llama a TextTransform.exe desde scripts. Sin embargo, normalmente no es necesario, porque puede realizar la transformación de texto en Visual Studio o en el proceso de compilación.

> [!NOTE]
> Si desea realizar la transformación de texto como parte de un proceso de compilación, considere la posibilidad de usar la tarea de transformación de texto MSBuild. Para obtener más información, vea [generación de código en un proceso de compilación](../modeling/code-generation-in-a-build-process.md). En una máquina en la que [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] está instalado, también puede escribir una aplicación o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] extensión que pueda transformar plantillas de texto. Para obtener más información, consulte [procesar plantillas de texto mediante un host personalizado](../modeling/processing-text-templates-by-using-a-custom-host.md).

 TextTransform.exe se encuentra en el siguiente directorio:

 **\Archivos de Programa\archivos Comunes\microsoft Shared\TextTemplating\11.0**

## <a name="syntax"></a>Sintaxis

```
TextTransform [<options>] <templateName>
```

#### <a name="parameters"></a>Parámetros

|**Argument**|**Descripción**|
|------------------|---------------------|
|`templateName`|Identifica el nombre del archivo de plantilla que desea transformar.|

|**Opción**|**Descripción**|
|----------------|---------------------|
|**-out** \<filename>|Archivo en el que se escribe la salida de la transformación.|
|**-r**\<assembly>|Ensamblado que se usa para compilar y ejecutar la plantilla de texto.|
|**-u**\<namespace>|Espacio de nombres que se utiliza para compilar la plantilla.|
|**-I**\<includedirectory>|Directorio que contiene las plantillas de texto incluidas en la plantilla de texto especificada.|
|**-P**\<referencepath>|Directorio en el que se van a buscar los ensamblados especificados dentro de la plantilla de texto o para utilizar la opción **-r** .<br /><br /> Por ejemplo, para incluir ensamblados que se usan para la API de Visual Studio, use<br /><br /> `-P "%VSSHELLFOLDER%\Common7\IDE\PublicAssemblies"`|
|**-DP** \<processorName> ! \<className> !\<assemblyName&#124;codeBase>|El nombre, el nombre de tipo completo y el ensamblado de un procesador de directivas que se puede usar para procesar directivas personalizadas dentro de la plantilla de texto.|
|**-a** [processorName]! [directiveName]! \<parameterName> !\<parameterValue>|Especifique un valor de parámetro para un procesador de directivas. Si especifica solo el nombre y el valor del parámetro, el parámetro estará disponible para todos los procesadores de directivas. Si especifica un procesador de directivas, el parámetro solo está disponible para el procesador especificado. Si especifica un nombre de Directiva, el parámetro solo está disponible cuando se está procesando la Directiva especificada.<br /><br />  En una plantilla de texto, incluya `hostspecific` en la Directiva de plantilla e invoque el mensaje en `this.Host` . Por ejemplo:<br /><br /> `<#@template language="c#" hostspecific="true"#> [<#= this.Host.ResolveParameterValue("", "", "parameterName") #>]`.<br /><br /> Escriba siempre las marcas '! ', incluso si omite los nombres de directiva y procesador opcionales. Por ejemplo:<br /><br /> `-a !!param!value`|
|**-h**|Proporciona ayuda.|

## <a name="related-topics"></a>Temas relacionados

|Tarea|Tema|
|----------|-----------|
|Genere archivos en una solución de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|[Generación de código en tiempo de diseño usando las plantillas de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|
|Escriba procesadores de directivas para transformar sus propios orígenes de datos.|[Personalizar la transformación de texto T4](../modeling/customizing-t4-text-transformation.md)|
|Escriba un host de plantillas de texto que le permita invocar plantillas de texto desde su propia aplicación.|[Procesar las plantillas de texto mediante un host personalizado](../modeling/processing-text-templates-by-using-a-custom-host.md)|
