---
title: 'Generación de nuevos proyectos: Internamente, la segunda parte | Documentos de Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 73ce91d8-0ab1-4a1f-bf12-4d3c49c01e13
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5ccdd4cd8bafc4bc4a899ea47d62ec10e578569c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62909313"
---
# <a name="new-project-generation-under-the-hood-part-two"></a>Generación de nuevos proyectos: Aspectos técnicos (parte 2)

En [nueva generación de proyectos: Internamente, una parte](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) vimos cómo **nuevo proyecto** se rellena el cuadro de diálogo. Supongamos que ha seleccionado un **aplicación de Windows de Visual C#**, se han rellenado los **nombre** y **ubicación** cuadros de texto y hace clic en Aceptar.

## <a name="generating-the-solution-files"></a>Generar los archivos de solución
 Elegir una plantilla de aplicación dirige [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] descomprimir y abrir el archivo .vstemplate correspondiente y para iniciar una plantilla para interpretar los comandos XML de este archivo. Estos comandos crean proyectos y elementos de proyecto en la solución nueva o existente.

 La plantilla desempaqueta los archivos de origen, llama a las plantillas de elemento de la misma carpeta zip que contiene el archivo .vstemplate. La plantilla copia estos archivos en el nuevo proyecto, personalizarlos según corresponda.

### <a name="template-parameter-replacement"></a>Reemplazo de parámetros de plantilla
 Cuando la plantilla copia una plantilla de elementos a un nuevo proyecto, sustituye los parámetros de plantilla con cadenas para personalizar el archivo. Un parámetro de plantilla es un símbolo (token) especial que se va precedido y seguido por un signo de dólar, por ejemplo, $date$.

 Echemos un vistazo a una plantilla de elemento de proyecto típica. Extraer y examine Program.cs en la carpeta de 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip Program Files\Microsoft Visual Studio.

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

Si crea un nuevo proyecto de aplicación de Windows denominado Simple, la plantilla reemplaza el `$safeprojectname$` parámetro con el nombre del proyecto.

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

 Para obtener una lista completa de parámetros de plantilla, vea [Parámetros de plantilla](../../ide/template-parameters.md).

## <a name="a-look-inside-a-vstemplate-file"></a>Una mirada a una. Archivo VSTemplate
 Un archivo .vstemplate básico tiene este formato

```xml
<VSTemplate Version="2.0.0"     xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"     Type="Project">
    <TemplateData>
    </TemplateData>
    <TemplateContent>
    </TemplateContent>
</VSTemplate>
```

 Analizamos la \<TemplateData > sección la [nueva generación de proyectos: Internamente, la primera parte](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md). Las etiquetas en esta sección se utilizan para controlar la apariencia de la **nuevo proyecto** cuadro de diálogo.

 Las etiquetas en el \<TemplateContent > sección control de la generación de nuevos proyectos y elementos de proyecto. Este es el \<TemplateContent > sección del archivo en la carpeta \Archivos 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip de Visual Studio \Program Files\Microsoft cswindowsapplication.vstemplate.

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

 El \<proyecto > etiqueta controla la generación de un proyecto y el \<ProjectItem > etiqueta controla la generación de un elemento de proyecto. Si el parámetro ReplaceParameters es true, la plantilla va a personalizar todos los parámetros de plantilla en el archivo de proyecto o elemento. En este caso, todos los elementos de proyecto personalizados, excepto Settings.settings.

 El parámetro TargetFileName especifica el nombre y ruta de acceso relativa del archivo de proyecto resultante o elemento. Esto le permite crear una estructura de carpetas para el proyecto. Si no especifica este argumento, el elemento de proyecto tendrá el mismo nombre que la plantilla de elemento de proyecto.

 La estructura de carpetas de aplicación de Windows resultante tendrá este aspecto:

 ![SimpleSolution](../../extensibility/internals/media/simplesolution.png "SimpleSolution")

 El primer y único \<proyecto > etiquetas en las lecturas de plantilla:

```xml
<Project File="WindowsApplication.csproj" ReplaceParameters="true">
```

 Esto indica a la plantilla de proyecto nuevo para crear el archivo de proyecto Simple.csproj copiando y personalizar el windowsapplication.csproj de elemento de plantilla.

### <a name="designers-and-references"></a>Los diseñadores y referencias
 Puede ver en el Explorador de soluciones que la carpeta Propiedades está presente y contiene los archivos que esperaba. Pero ¿qué proyecto hace referencia y dependencias de archivo del diseñador, como Resources.Designer.cs a Resources.resx y Form1.Designer.cs a Form1.cs?  Estos se configuran en el archivo Simple.csproj cuando se genera.

 Este es el \<ItemGroup > desde Simple.csproj que crea las referencias del proyecto:

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

 Puede ver que se trata de las referencias del seis proyecto que aparecen en el Explorador de soluciones. Esta es una sección de otro \<ItemGroup >. Se han eliminado muchas líneas de código para mayor claridad. Esta sección hace Settings.Designer.cs depende Settings.Settings creado por:

```xml
<ItemGroup>
    <Compile Include="Properties\Settings.Designer.cs">
        <DependentUpon>Settings.settings</DependentUpon>
    </Compile>
</ItemGroup>
```

## <a name="see-also"></a>Vea también

- [Generación de nuevos proyectos: Aspectos técnicos (parte 1)](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)
- [MSBuild](../../msbuild/msbuild.md)