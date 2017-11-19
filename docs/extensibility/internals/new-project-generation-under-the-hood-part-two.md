---
title: "Nueva generación de proyecto: Under the Hood, segunda parte | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 73ce91d8-0ab1-4a1f-bf12-4d3c49c01e13
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f7dc04752b034f666dfcb1d72b500f2c12f54fba
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="new-project-generation-under-the-hood-part-two"></a>Nueva generación de proyecto: Under the Hood, segunda parte
En [nueva generación de proyecto: Under the Hood, una parte](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) hemos visto cómo **nuevo proyecto** se rellena el cuadro de diálogo. Supongamos que ha seleccionado un **aplicación de Windows de Visual C#**, se han rellenado los **nombre** y **ubicación** cuadros de texto y hace clic en Aceptar.  
  
## <a name="generating-the-solution-files"></a>Generar los archivos de solución  
 Elegir una plantilla de aplicación dirige [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para descomprimir y abrir el archivo .vstemplate correspondiente y para iniciar una plantilla para interpretar los comandos XML de este archivo. Estos comandos crean proyectos y elementos de proyecto de la solución nueva o existente.  
  
 La plantilla desempaqueta los archivos de origen, denominados plantillas de elementos de la misma carpeta de .zip que contiene el archivo .vstemplate. La plantilla de copia estos archivos en el nuevo proyecto, personalizarlos en consecuencia. Para obtener información general de plantillas de proyecto y elemento, vea [NIB: plantillas de Visual Studio](http://msdn.microsoft.com/en-us/141fccaa-d68f-4155-822b-27f35dd94041).  
  
### <a name="template-parameter-replacement"></a>Reemplazo de parámetros de plantilla  
 Cuando la plantilla copia una plantilla de elementos a un nuevo proyecto, se reemplaza cualquier parámetro de plantilla con cadenas para personalizar el archivo. Un parámetro de plantilla es un símbolo (token) especial que se va precedido y seguido por un signo de dólar, por ejemplo, $date$.  
  
 Echemos un vistazo a una plantilla de elemento de proyecto típico. Extraer y examine Program.cs en la carpeta de archivos de programa\Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Windows.Forms;  
  
namespace $safeprojectname$  
{  
    static class Program  
    {  
        // source code deleted here for brevity  
    }  
}  
```  
  
 Si crea un nuevo proyecto de aplicación de Windows con el nombre Simple, la plantilla reemplaza el `$safeprojectname$` parámetro con el nombre del proyecto.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Windows.Forms;  
  
namespace Simple  
{  
    static class Program  
    {  
        // source code deleted here for brevity  
    }  
}  
```  
  
 Para obtener una lista completa de parámetros de plantilla, consulte [parámetros de plantilla](../../ide/template-parameters.md).  
  
## <a name="a-look-inside-a-vstemplate-file"></a>Un vistazo dentro de una. Archivo VSTemplate  
 Un archivo .vstemplate básico tiene este formato  
  
```  
<VSTemplate Version="2.0.0"     xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"     Type="Project">  
    <TemplateData>  
    </TemplateData>  
    <TemplateContent>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 Analizamos la \<TemplateData > sección la [nueva generación de proyecto: Under the Hood, una parte](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md). Las etiquetas de esta sección se utilizan para controlar el aspecto de la **nuevo proyecto** cuadro de diálogo.  
  
 Las etiquetas en el \<TemplateContent > sección control de la generación de nuevos proyectos y elementos de proyecto. Este es el \<TemplateContent > sección del archivo cswindowsapplication.vstemplate en la carpeta de 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip \Program Visual Studio.  
  
```  
<TemplateContent>  
  <Project File="WindowsApplication.csproj" ReplaceParameters="true">  
    <ProjectItem ReplaceParameters="true"  
      TargetFileName="Properties\AssemblyInfo.cs">  
      AssemblyInfo.cs  
    </ProjectItem>  
    <ProjectItem TargetFileName="Properties\Resources.resx">  
      Resources.resx  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Resources.Designer.cs">  
      Resources.Designer.cs  
    </ProjectItem>  
    <ProjectItem TargetFileName="Properties\Settings.settings">  
      Settings.settings  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Settings.Designer.cs">  
      Settings.Designer.cs  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true" OpenInEditor="true">  
      Form1.cs  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true">  
      Form1.Designer.cs  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true">  
      Program.cs  
    </ProjectItem>  
  </Project>  
</TemplateContent>  
```  
  
 El \<proyecto > etiqueta controla la generación de un proyecto y el \<ProjectItem > etiqueta controla la generación de un elemento de proyecto. Si el parámetro ReplaceParameters es true, la plantilla personalizará todos los parámetros de plantilla en el archivo de proyecto o elemento. En este caso, todos los elementos de proyecto personalizados, excepto Settings.settings.  
  
 El parámetro TargetFileName especifica el nombre y la ruta de acceso relativa del archivo de proyecto resultante o elemento. Esto le permite crear una estructura de carpetas para el proyecto. Si no especifica este argumento, el elemento de proyecto tendrá el mismo nombre que la plantilla de elemento de proyecto.  
  
 La estructura de carpetas de aplicación de Windows resultante tiene el siguiente aspecto:  
  
 ![SimpleSolution](../../extensibility/internals/media/simplesolution.png "SimpleSolution")  
  
 El primer y único \<proyecto > etiquetas en las lecturas de plantilla:  
  
```  
<Project File="WindowsApplication.csproj" ReplaceParameters="true">  
```  
  
 Esto indica a la plantilla de proyecto para crear el archivo de proyecto Simple.csproj copiando y personalizar el windowsapplication.csproj de elemento de plantilla.  
  
### <a name="designers-and-references"></a>Diseñadores y referencias  
 Puede ver en el Explorador de soluciones que la carpeta Propiedades está presente y contiene los archivos que esperaba. Pero ¿qué hay de proyecto hace referencia a ella y dependencias de archivo del diseñador, como Resources.Designer.cs a Resources.resx y Form1.Designer.cs a Form1.cs?  Estos se configuran en el archivo Simple.csproj cuando se generan.  
  
 Este es el \<ItemGroup > de Simple.csproj que crea las referencias del proyecto:  
  
```  
<ItemGroup>  
    <Reference Include="System" />  
    <Reference Include="System.Data" />  
    <Reference Include="System.Deployment" />  
    <Reference Include="System.Drawing" />  
    <Reference Include="System.Windows.Forms" />  
    <Reference Include="System.Xml" />  
</ItemGroup>  
```  
  
 Puede ver que se trata de las referencias del seis proyecto que aparecen en el Explorador de soluciones. Esta es una sección de otra \<ItemGroup >. Se han eliminado muchas líneas de código para mayor claridad. En esta sección hace que Settings.Designer.cs dependa Settings.Settings creado por:  
  
```  
<ItemGroup>  
    <Compile Include="Properties\Settings.Designer.cs">  
        <DependentUpon>Settings.settings</DependentUpon>  
    </Compile>  
</ItemGroup>  
```  
  
## <a name="see-also"></a>Vea también  
 [Nueva generación de proyectos: aspectos técnicos, primera parte](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)  
 [MSBuild](../../msbuild/msbuild.md)