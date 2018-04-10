---
title: T4 Directiva de ensamblado | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 9f586931bd14089beca787c24d92bc2605c4d5de
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/10/2018
---
# <a name="t4-assembly-directive"></a>Directiva de ensamblado T4
En [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] la plantilla de texto en tiempo de diseño, la directiva `assembly` carga un ensamblado para que el código de plantilla pueda utilizar sus tipos. El efecto es similar a agregar una referencia al ensamblado en un proyecto de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Para obtener una descripción general de la escritura de plantillas de texto, consulte [escribir una plantilla de texto T4](../modeling/writing-a-t4-text-template.md).  
  
> [!NOTE]
>  No necesita la directiva de salida `assembly` en una plantilla de texto (preprocesada) en tiempo de ejecución. En su lugar, agregue los ensamblados necesarios para la **referencias** de su [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proyecto.  
  
## <a name="using-the-assembly-directive"></a>Usar la directiva de ensamblado  
 La sintaxis de las directivas es la siguiente:  
  
```  
<#@ assembly name="[assembly strong name|assembly file name]" #>  
```  
  
 El nombre del ensamblado debe ser uno de los siguientes:  
  
-   El nombre seguro de un ensamblado en la GAC, como `System.Xml.dll`. También puede utilizar el formulario largo, como `name="System.Xml, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"`. Para obtener más información, consulta <xref:System.Reflection.AssemblyName>.  
  
-   La ruta de acceso absoluta del ensamblado  
  
 También puede usar la sintaxis `$(variableName)` para hacer referencia a variables de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], como `$(SolutionDir)`, y usar `%VariableName%` para hacer referencia a las variables de entorno. Por ejemplo:  
  
```  
<#@ assembly name="$(SolutionDir)\MyProject\bin\Debug\SomeLibrary.Dll" #>  
```  
  
 La directiva de ensamblado no tiene ningún efecto en una plantilla de texto preprocesada. En su lugar, incluya las referencias necesarias en la **referencias** sección de su [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proyecto. Para obtener más información, consulte [tiempo de ejecución de generación de texto con plantillas de texto T4](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
## <a name="standard-assemblies"></a>Ensamblados estándar  
 Loa siguientes ensamblados se cargan automáticamente, por lo que no es necesario escribir las directivas de ensamblado para ellos:  
  
-   `Microsoft.VisualStudio.TextTemplating.1*.dll`  
  
-   `System.dll`  
  
-   `WindowsBase.dll`  
  
 Si utiliza una directiva personalizada, el procesador de directivas podría cargar ensamblados adicionales. Por ejemplo, si escribe plantillas para un lenguaje específico del dominio (ADSL), no necesita escribir directivas de ensamblado para los siguientes ensamblados:  
  
-   `Microsoft.VisualStudio.Modeling.Sdk.1*.dll`  
  
-   `Microsoft.VisualStudio.Modeling.Sdk.Diagrams.1*.dsl`  
  
-   `Microsoft.VisualStudio.TextTemplating.Modeling.1*.dll`  
  
-   El ensamblado contiene el ADSL.  
  
##  <a name="msbuild"></a> Usando las propiedades de proyecto de MSBuild y Visual Studio  
 Macros de Visual Studio como $ (SolutionDir) no funcionan en MSBuild. Si desea transformar plantillas del equipo de compilación, tiene que utilizar las propiedades del proyecto.  
  
 Modifique el archivo .csproj o .vbproj para definir una propiedad de proyecto. En este ejemplo se define una propiedad denominada `myLibFolder`:  
  
```xml  
<!-- Define a project property, myLibFolder: -->  
<PropertyGroup>  
    <myLibFolder>$(MSBuildProjectDirectory)\..\libs</myLibFolder>  
</PropertyGroup>  
  
<!-- Tell the MSBuild T4 task to make the property available: -->  
<ItemGroup>  
    <T4ParameterValues Include="myLibFolder">  
      <Value>$(myLibFolder)</Value>  
    </T4ParameterValues>  
  </ItemGroup>  
  
```  
  
 Ahora puede utilizar la propiedad del proyecto en plantillas de texto, que se transformarán correctamente en Visual Studio y MSBuild:  
  
```  
<#@ assembly name="$(myLibFolder)\MyLib.dll" #>  
```  
  
## <a name="see-also"></a>Vea también  
 [Directiva Include T4](../modeling/t4-include-directive.md)