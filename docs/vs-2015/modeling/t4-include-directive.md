---
title: T4 Directiva Include | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c3de9f3-755a-47c5-a30a-65717dcaaac2
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: e8de721b7f26152cd4e7f5df1ee7eb4d04770511
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49835948"
---
# <a name="t4-include-directive"></a>Directiva Include T4
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En una plantilla de texto de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], puede incluir texto de otro archivo utilizando una directiva `<#@include#>`. Puede colocar directivas `include` en cualquier parte de una plantilla de texto antes del primer bloque de características de clase `<#+ ... #>`. Los archivos incluidos también pueden contener directivas `include`, así como otras directivas. Esto le permite compartir código de plantilla y texto reutilizable entre plantillas.  
  
## <a name="using-include-directives"></a>Usar directivas include  
  
```  
<#@ include file="filePath" [once="true"] #>  
```  
  
- `filePath` pueden se absoluto o relativo al archivo de plantilla actual.  
  
   Además, las extensiones concretas de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pueden especificar sus propios directorios para buscar archivos de inclusión. Por ejemplo, cuando se han instalado el SDK visualización y modelado (herramientas DSL), la siguiente carpeta se agrega a la lista de inclusiones: `Program Files\Microsoft Visual Studio 10.0\Common7\IDE\Extensions\Microsoft\DSL SDK\DSL Designer\11.0\TextTemplates`.  
  
   Estas carpetas de inclusión adicionales podrían depender de la extensión de archivo del archivo para incluir. Por ejemplo, la carpeta de inclusión de las Herramientas ADSL solo es accesible para la inclusión de archivos que tienen la extensión de archivo `.tt`  
  
- `filePath` pueden incluir variables de entorno delimitadas con "%." Por ejemplo:  
  
  ```  
  <#@ include file="%HOMEPATH%\MyIncludeFile.t4" #>  
  ```  
  
- El nombre de un archivo incluido no tiene que utilizar la extensión `".tt"`.  
  
   Puede que desee utilizar otra extensión, como `".t4"`, para los archivos incluidos. Esto es porque, cuando se agrega un `.tt` archivo a un proyecto, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] establece automáticamente su **Custom Tool** propiedad `TextTemplatingFileGenerator`. Normalmente no desea que los archivos incluidos se transformen individualmente.  
  
   Por otra parte, debe tener en cuenta que en algunos casos, la extensión de archivo afecta a las carpetas adicionales que se buscarán para archivos de inclusión. Esto podría ser importante al tener un archivo incluido que incluye otros archivos.  
  
- El contenido incluido se procesa casi como si formase parte de la plantilla de texto que lo incluye. Sin embargo, puede incluir un archivo que contenga un bloque de características de clase `<#+...#>` aunque la directiva `include` vaya seguida de texto normal y bloques de control estándar.  
  
- Use `once="true"` para garantizar que una plantilla se incluye una sola vez, aunque se invoque desde varios archivos de inclusión.  
  
   Este facilita la característica hará lo simplifica la compilación de una biblioteca de fragmentos de código T4 reutilizables que se puede incluir en sin preocuparse de que algún otro fragmento de código ha ya incluido.  Por ejemplo, suponga que tiene una biblioteca de fragmentos muy específicos que se encargan de procesamiento de plantillas y generación de C#.  A su vez, se usan algunas utilidades más específica de la tarea como la generación de excepciones, que, a continuación, puede usar desde cualquier plantilla más específica de la aplicación. Si dibuja el gráfico de dependencias, verá que algunos fragmentos de código se incluyeron varias veces. Sin embargo, el parámetro `once` evita las inclusiones siguientes.  
  
  **MyTextTemplate.tt:**  
  
```  
<#@ output extension=".txt" #>  
Output message 1 (from top template).  
<#@ include file="TextFile1.t4"#>  
Output message 5 (from top template).  
<#  
   GenerateMessage(6); // defined in TextFile1.t4  
   AnotherGenerateMessage(7); // defined in TextFile2.t4  
#>  
  
```  
  
 **TextFile1.t4:**  
  
```  
   Output Message 2 (from included file).  
<#@include file="TextFile2.t4" #>  
   Output Message 4 (from included file).  
<#+ // Start of class feature control block.  
void GenerateMessage(int n)  
{  
#>  
   Output Message <#= n #> (from GenerateMessage method).  
<#+  
}  
#>  
  
```  
  
 **TextFile2.t4:**  
  
```  
        Output Message 3 (from included file 2).  
<#+ // Start of class feature control block.  
void AnotherGenerateMessage(int n)  
{  
#>  
       Output Message <#= n #> (from AnotherGenerateMessage method).  
<#+  
}  
#>  
  
```  
  
 **El archivo generado resultante, MyTextTemplate.txt:**  
  
```  
Output message 1 (from top template).  
   Output Message 2 (from included file).  
        Output Message 3 (from included file 2).  
  
   Output Message 4 (from included file).  
  
Output message 5 (from top template).  
   Output Message 6 (from GenerateMessage method).  
       Output Message 7 (from AnotherGenerateMessage method).  
  
```  
  
##  <a name="msbuild"></a> Uso de las propiedades del proyecto de MSBuild y Visual Studio  
 Aunque puede usar macros de Visual Studio como $ (SolutionDir) en una directiva include, estas macros no funcionan en MSBuild. Si desea transformar plantillas del equipo de compilación, tiene que utilizar las propiedades del proyecto.  
  
 Modifique el archivo .csproj o .vbproj para definir una propiedad de proyecto. En este ejemplo se define una propiedad denominada `myIncludeFolder`:  
  
```xml  
<!-- Define a project property, myIncludeFolder: -->  
<PropertyGroup>  
    <myIncludeFolder>$(MSBuildProjectDirectory)\..\libs</myIncludeFolder>  
</PropertyGroup>  
  
<!-- Tell the MSBuild T4 task to make the property available: -->  
<ItemGroup>  
    <T4ParameterValues Include="myIncludeFolder">  
      <Value>$(myIncludeFolder)</Value>  
    </T4ParameterValues>  
  </ItemGroup>  
  
```  
  
 Ahora puede utilizar la propiedad del proyecto en plantillas de texto, que se transformarán correctamente en Visual Studio y MSBuild:  
  
```  
<#@ include file="$(myIncludeFolder)\defs.tt" #>  
```



