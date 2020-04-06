---
title: 'Nueva generación de proyectos: Bajo la capucha, Segunda parte Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 73ce91d8-0ab1-4a1f-bf12-4d3c49c01e13
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8692f2012e5f2733982f04e35a7fed415e49c636
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707018"
---
# <a name="new-project-generation-under-the-hood-part-two"></a>Nueva generación de proyectos: aspectos técnicos, segunda parte

En [Nueva generación de proyectos: Bajo la capucha, primera parte](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) vimos cómo se rellena el cuadro de diálogo Nuevo **proyecto.** Supongamos que ha seleccionado una aplicación de Windows de **Visual C,** ha rellenado los cuadros de texto **Nombre** y **ubicación** y ha hecho clic en Aceptar.

## <a name="generating-the-solution-files"></a>Generación de los archivos de solución
 La elección de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] una plantilla de aplicación indica a descomprimir y abrir el archivo .vstemplate correspondiente e iniciar una plantilla para interpretar los comandos XML en este archivo. Estos comandos crean proyectos y elementos de proyecto en la solución nueva o existente.

 La plantilla desempaqueta los archivos de origen, denominados plantillas de elementos, de la misma carpeta .zip que contiene el archivo .vstemplate. La plantilla copia estos archivos en el nuevo proyecto, personalizándolos en consecuencia.

### <a name="template-parameter-replacement"></a>Reemplazo de parámetros de plantilla
 Cuando la plantilla copia una plantilla de elemento en un nuevo proyecto, reemplaza los parámetros de plantilla por cadenas para personalizar el archivo. Un parámetro de plantilla es un token especial que va precedido y seguido de un signo de dólar, por ejemplo, $date$.

 Echemos un vistazo a una plantilla de elemento de proyecto típica. Extraiga y examine Program.cs en la carpeta Archivos de programa de Microsoft Visual Studio 8, Common7, IDE, ProjectTemplates, CSharp, Windows, Windows, Windows, WindowsApplication.zip.

```csharp
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

Si crea un nuevo proyecto de aplicación de `$safeprojectname$` Windows denominado Simple, la plantilla reemplaza el parámetro por el nombre del proyecto.

```csharp
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

 Para obtener una lista completa de parámetros de plantilla, consulte [Parámetros](../../ide/template-parameters.md)de plantilla .

## <a name="a-look-inside-a-vstemplate-file"></a>Una mirada dentro de un archivo . VSTemplate File
 Un archivo .vstemplate básico tiene este formato

```xml
<VSTemplate Version="2.0.0"     xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"     Type="Project">
    <TemplateData>
    </TemplateData>
    <TemplateContent>
    </TemplateContent>
</VSTemplate>
```

 Hemos analizado \<la sección templateData> en la nueva generación de [proyectos: Under the Hood, Parte Uno](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md). Las etiquetas de esta sección se utilizan para controlar el aspecto del cuadro de diálogo **Nuevo proyecto.**

 Las etiquetas \<de la sección de> TemplateContent controlan la generación de nuevos proyectos y elementos de proyecto. Aquí está \<la sección de> TemplateContent del archivo cswindowsapplication.vstemplate en la carpeta .

```xml
<TemplateContent>
  <Project File="WindowsApplication.csproj" ReplaceParameters="true">
    <ProjectItem ReplaceParameters="true"
      TargetFileName="Properties\AssemblyInfo.cs">
      AssemblyInfo.cs
    </ProjectItem>
    <ProjectItem TargetFileName="Properties\Resources.resx">
      Resources.resx
    </ProjectItem>
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Resources.Designer.cs">
      Resources.Designer.cs
    </ProjectItem>
    <ProjectItem TargetFileName="Properties\Settings.settings">
      Settings.settings
    </ProjectItem>
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Settings.Designer.cs">
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

 La \<etiqueta Project> controla la \<generación de un proyecto y la etiqueta ProjectItem> controla la generación de un elemento de proyecto. Si el parámetro ReplaceParameters es true, la plantilla personalizará todos los parámetros de plantilla en el archivo o elemento del proyecto. En este caso, se personalizan todos los elementos del proyecto, excepto Settings.settings.

 El parámetro TargetFileName especifica el nombre y la ruta de acceso relativa del archivo o elemento de proyecto resultante. Esto le permite crear una estructura de carpetas para el proyecto. Si no especifica este argumento, el elemento de proyecto tendrá el mismo nombre que la plantilla de elemento de proyecto.

 La estructura de carpetas de aplicaciones de Windows resultante tiene este aspecto:

 ![SimpleSolution](../../extensibility/internals/media/simplesolution.png "SimpleSolution")

 La primera \<y única etiqueta de Project> de la plantilla dice:

```xml
<Project File="WindowsApplication.csproj" ReplaceParameters="true">
```

 Esto indica a la plantilla Nuevo proyecto que cree el archivo de proyecto Simple.csproj copiando y personalizando el elemento de plantilla windowsapplication.csproj.

### <a name="designers-and-references"></a>Diseñadores y referencias
 Puede ver en el Explorador de soluciones que la carpeta Propiedades está presente y contiene los archivos esperados. Pero, ¿qué pasa con las referencias de proyecto y las dependencias de archivos de diseñador, como Resources.Designer.cs a Resources.resx y Form1.Designer.cs a Form1.cs?  Se configuran en el archivo Simple.csproj cuando se genera.

 Aquí está \<el> ItemGroup de Simple.csproj que crea las referencias del proyecto:

```xml
<ItemGroup>
    <Reference Include="System" />
    <Reference Include="System.Data" />
    <Reference Include="System.Deployment" />
    <Reference Include="System.Drawing" />
    <Reference Include="System.Windows.Forms" />
    <Reference Include="System.Xml" />
</ItemGroup>
```

 Puede ver que estas son las seis referencias de proyecto que aparecen en el Explorador de soluciones. Aquí hay una sección \<de otro> de ItemGroup. Muchas líneas de código se han eliminado para mayor claridad. Esta sección hace que Settings.Designer.cs dependa de Settings.settings:

```xml
<ItemGroup>
    <Compile Include="Properties\Settings.Designer.cs">
        <DependentUpon>Settings.settings</DependentUpon>
    </Compile>
</ItemGroup>
```

## <a name="see-also"></a>Vea también

- [Nueva generación de proyectos: aspectos técnicos, primera parte](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)
- [MSBuild](../../msbuild/msbuild.md)
