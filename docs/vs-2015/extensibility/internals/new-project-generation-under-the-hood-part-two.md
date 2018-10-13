---
title: 'Nueva generación de proyectos: Aspectos técnicos, segunda parte | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 73ce91d8-0ab1-4a1f-bf12-4d3c49c01e13
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5ce2ad60c2c3c072ab5e38f2dbee11035d44176a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49279596"
---
# <a name="new-project-generation-under-the-hood-part-two"></a>Nueva generación de proyectos: aspectos técnicos, segunda parte
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En [nueva generación de proyectos: Under the Hood, parte uno](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) vimos cómo **nuevo proyecto** se rellena el cuadro de diálogo. Supongamos que ha seleccionado un **aplicación de Windows de Visual C#**, se han rellenado los **nombre** y **ubicación** cuadros de texto y hace clic en Aceptar.  
  
## <a name="generating-the-solution-files"></a>Generar los archivos de solución  
 Elegir una plantilla de aplicación dirige [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] descomprimir y abrir el archivo .vstemplate correspondiente y para iniciar una plantilla para interpretar los comandos XML de este archivo. Estos comandos crean proyectos y elementos de proyecto en la solución nueva o existente.  
  
 La plantilla desempaqueta los archivos de origen, llama a las plantillas de elemento de la misma carpeta zip que contiene el archivo .vstemplate. La plantilla copia estos archivos en el nuevo proyecto, personalizarlos según corresponda. Para obtener información general de plantillas de proyecto y elemento, vea [NIB: plantillas de Visual Studio](http://msdn.microsoft.com/en-us/141fccaa-d68f-4155-822b-27f35dd94041).  
  
### <a name="template-parameter-replacement"></a>Reemplazo de parámetros de plantilla  
 Cuando la plantilla copia una plantilla de elementos a un nuevo proyecto, sustituye los parámetros de plantilla con cadenas para personalizar el archivo. Un parámetro de plantilla es un símbolo (token) especial que se va precedido y seguido por un signo de dólar, por ejemplo, $date$.  
  
 Echemos un vistazo a una plantilla de elemento de proyecto típica. Extraer y examine Program.cs en la carpeta de 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip Program Files\Microsoft Visual Studio.  
  
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
  
 Si crea un nuevo proyecto de aplicación de Windows denominado Simple, la plantilla reemplaza el `$safeprojectname$` parámetro con el nombre del proyecto.  
  
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
  
 Para obtener una lista completa de parámetros de plantilla, vea [Parámetros de plantilla](../../ide/template-parameters.md).  
  
## <a name="a-look-inside-a-vstemplate-file"></a>Una mirada a una. Archivo VSTemplate  
 Un archivo .vstemplate básico tiene este formato  
  
```  
<VSTemplate Version="2.0.0"     xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"     Type="Project">  
    <TemplateData>  
    </TemplateData>  
    <TemplateContent>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 Analizamos la \<TemplateData > sección la [nueva generación de proyectos: Under the Hood, parte uno](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md). Las etiquetas en esta sección se utilizan para controlar la apariencia de la **nuevo proyecto** cuadro de diálogo.  
  
 Las etiquetas en el \<TemplateContent > sección control de la generación de nuevos proyectos y elementos de proyecto. Este es el \<TemplateContent > sección del archivo en la carpeta \Archivos 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip de Visual Studio \Program Files\Microsoft cswindowsapplication.vstemplate.  
  
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
  
 El \<proyecto > etiqueta controla la generación de un proyecto y el \<ProjectItem > etiqueta controla la generación de un elemento de proyecto. Si el parámetro ReplaceParameters es true, la plantilla va a personalizar todos los parámetros de plantilla en el archivo de proyecto o elemento. En este caso, todos los elementos de proyecto personalizados, excepto Settings.settings.  
  
 El parámetro TargetFileName especifica el nombre y ruta de acceso relativa del archivo de proyecto resultante o elemento. Esto le permite crear una estructura de carpetas para el proyecto. Si no especifica este argumento, el elemento de proyecto tendrá el mismo nombre que la plantilla de elemento de proyecto.  
  
 La estructura de carpetas de aplicación de Windows resultante tendrá este aspecto:  
  
 ![SimpleSolution](../../extensibility/internals/media/simplesolution.png "SimpleSolution")  
  
 El primer y único \<proyecto > etiquetas en las lecturas de plantilla:  
  
```  
<Project File="WindowsApplication.csproj" ReplaceParameters="true">  
```  
  
 Esto indica a la plantilla de proyecto nuevo para crear el archivo de proyecto Simple.csproj copiando y personalizar el windowsapplication.csproj de elemento de plantilla.  
  
### <a name="designers-and-references"></a>Los diseñadores y referencias  
 Puede ver en el Explorador de soluciones que la carpeta Propiedades está presente y contiene los archivos que esperaba. Pero ¿qué proyecto hace referencia y dependencias de archivo del diseñador, como Resources.Designer.cs a Resources.resx y Form1.Designer.cs a Form1.cs?  Estos se configuran en el archivo Simple.csproj cuando se genera.  
  
 Este es el \<ItemGroup > desde Simple.csproj que crea las referencias del proyecto:  
  
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
  
 Puede ver que se trata de las referencias del seis proyecto que aparecen en el Explorador de soluciones. Esta es una sección de otro \<ItemGroup >. Se han eliminado muchas líneas de código para mayor claridad. Esta sección hace Settings.Designer.cs depende Settings.Settings creado por:  
  
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


