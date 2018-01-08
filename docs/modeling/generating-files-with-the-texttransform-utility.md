---
title: Generar archivos con la utilidad TextTransform | Documentos de Microsoft
ms.custom: 
ms.date: 09/21/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text templates, TextTransform utility
- TextTransform.exe
ms.assetid: 06a48235-fe02-403e-a1cf-2ae70b4db62f
caps.latest.revision: "41"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: ebd8b73cf28452998f00dbf863e6637f6c9188e5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="generating-files-with-the-texttransform-utility"></a>Generar archivos con la utilidad TextTransform
TextTransform.exe es una herramienta de línea de comandos que puede usar para transformar una plantilla de texto. Cuando se llama a TextTransform.exe, especifique el nombre de un archivo de plantilla de texto como argumento. TextTransform.exe llama al motor de transformación de texto y procesa la plantilla de texto. TextTransform.exe se suele llamar desde secuencias de comandos. Sin embargo, no se suelen ser necesario, porque no se puede realizar la transformación de texto en Visual Studio o en el proceso de compilación.  
  
> [!NOTE]
>  Si desea realizar la transformación de texto como parte de un proceso de compilación, considere la posibilidad de utilizar la tarea de transformación de texto de MSBuild. Para obtener más información, consulte [generación de código en un proceso de compilación](../modeling/code-generation-in-a-build-process.md). En un equipo donde [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] está instalado, también puede escribir una aplicación o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] extensión que puede transformar plantillas de texto. Para obtener más información, consulte [de procesamiento de plantillas de texto mediante un Host personalizado](../modeling/processing-text-templates-by-using-a-custom-host.md).  
  
 TextTransform.exe se encuentra en el siguiente directorio:  
  
 **\Program archivos (x86) \Microsoft Visual Studio\2017\Professional\Common7\IDE**  

para la edición Professional, o

 **\Program archivos (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE**
 
 para la edición Enterprise.

En versiones anteriores de Visual Studio, el archivo se encuentra en la siguiente ubicación:

**\Program archivos (x86) \Common Shared\TextTemplating\{versión}**

donde {versión} depende de la versión anterior instalada.

## <a name="syntax"></a>Sintaxis  
  
```  
TextTransform [<options>] <templateName>  
```  
  
#### <a name="parameters"></a>Parámetros  
  
|**Argumento**|**Descripción**|  
|------------------|---------------------|  
|`templateName`|Identifica el nombre del archivo de plantilla que desea transformar.|  
  
|**Opción**|**Descripción**|  
|----------------|---------------------|  
|**-out** \<nombre de archivo >|El archivo en el que se escribe la salida de la transformación.|  
|**-r** \<ensamblado >|Un ensamblado que se utiliza para compilar y ejecutar la plantilla de texto.|  
|**-u** \<espacio de nombres >|Un espacio de nombres que se utiliza para compilar la plantilla.|  
|**-I** \<includedirectory >|Un directorio que contiene las plantillas de texto incluidas en la plantilla de texto especificado.|  
|**-P** \<referencepath >|Un directorio para buscar ensamblados especificados en la plantilla de texto o para usar el **- r** opción.<br /><br /> Por ejemplo, para incluir ensamblados utilizados para la API de Visual Studio, use lo siguiente:<br /><br /> `-P "%VSSHELLFOLDER%\Common7\IDE\PublicAssemblies"`|  
|**-dp** \<processorName >!\< className >! \<assemblyName &#124; codeBase >|El nombre, el nombre de tipo completo y el ensamblado de un procesador de directivas que puede usarse para procesar directivas personalizadas dentro de la plantilla de texto.|  
|**-a** [processorName]! [ ¡directiveName]! \<parameterName >! \<parameterValue >|Especifique un valor de parámetro para un procesador de directivas. Si especifica únicamente el nombre de parámetro y valor, el parámetro estará disponible para todos los procesadores de directivas. Si especifica un procesador de directivas, el parámetro está disponible sólo para el procesador especificado. Si especifica un nombre de directiva, el parámetro está disponible solo cuando se procesa la directiva especificada.<br /><br /> Para obtener acceso a los valores de parámetro de una plantilla de texto o un procesador de directivas, utilice <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost.ResolveParameterValue%2A>. En una plantilla de texto, incluya `hostspecific` en la directiva de plantilla e invocar el mensaje en `this.Host`. Por ejemplo:<br /><br /> `<#@template language="c#" hostspecific="true"#> [<#= this.Host.ResolveParameterValue("", "", "parameterName") #>]`.<br /><br /> Escriba siempre la '!' marca, incluso si se omiten el procesador opcional y los nombres de directiva. Por ejemplo:<br /><br /> `-a !!param!value`|  
|**-h**|Proporciona la Ayuda.|  
  
## <a name="related-topics"></a>Temas relacionados  
  
|Tarea|Tema|  
|----------|-----------|  
|Genere archivos en una solución de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|[Generación de código en tiempo de diseño mediante plantillas de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|  
|Escriba procesadores de directivas para transformar sus propios orígenes de datos.|[Personalizar la transformación de texto T4](../modeling/customizing-t4-text-transformation.md)|  
|Escribir un host de plantillas de texto que permite invocar plantillas de texto desde su propia aplicación.|[Procesar las plantillas de texto mediante un host personalizado](../modeling/processing-text-templates-by-using-a-custom-host.md)|
