---
title: 'Nueva generación de proyectos: en el capó, parte dos | Microsoft Docs'
description: Eche un vistazo a lo que sucede en el entorno de desarrollo integrado (IDE) de Visual Studio a medida que crea su propio tipo de proyecto (parte 2 de 2).
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
ms.openlocfilehash: 9e45c9643a1fd2e6dcf9d5520fbb2982736b5109
ms.sourcegitcommit: 8a0d0f4c4910e2feb3bc7bd19e8f49629df78df5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/18/2020
ms.locfileid: "97668851"
---
# <a name="new-project-generation-under-the-hood-part-two"></a>Generación de nuevos proyectos: Aspectos técnicos (parte 2)

En [nueva generación de proyectos: en el capó, la primera parte](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) vimos cómo se rellena el cuadro de diálogo **nuevo proyecto** . Supongamos que ha seleccionado una **aplicación Windows de Visual C#**, ha rellenado los cuadros de texto **nombre** y **Ubicación** y ha hecho clic en Aceptar.

## <a name="generating-the-solution-files"></a>Generar los archivos de solución
 Al elegir una plantilla de aplicación [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se dirige a descomprimir y abrir el archivo. vstemplate correspondiente, así como iniciar una plantilla para interpretar los comandos XML de este archivo. Estos comandos crean proyectos y elementos de proyecto en la solución nueva o existente.

 La plantilla desempaqueta los archivos de origen, denominados plantillas de elementos, de la misma carpeta. zip que contiene el archivo. vstemplate. La plantilla copia estos archivos en el nuevo proyecto y los personaliza en consecuencia.

### <a name="template-parameter-replacement"></a>Reemplazo de parámetros de plantilla
 Cuando la plantilla copia una plantilla de elemento en un nuevo proyecto, reemplaza los parámetros de plantilla por cadenas para personalizar el archivo. Un parámetro de plantilla es un token especial precedido y seguido de un signo de dólar, por ejemplo, $date $.

 Echemos un vistazo a una plantilla de elemento de proyecto típica. Extraiga y examine Program.cs en la carpeta archivos de Programa\microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip.

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

Si crea un nuevo proyecto de aplicación de Windows denominado simple, la plantilla reemplaza el `$safeprojectname$` parámetro por el nombre del proyecto.

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

 Para obtener una lista completa de los parámetros de plantilla, vea [parámetros de plantilla](../../ide/template-parameters.md).

## <a name="a-look-inside-a-vstemplate-file"></a>Un aspecto dentro de un. Archivo VSTemplate
 Un archivo. vstemplate básico tiene este formato

```xml
<VSTemplate Version="2.0.0"     xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"     Type="Project">
    <TemplateData>
    </TemplateData>
    <TemplateContent>
    </TemplateContent>
</VSTemplate>
```

 Examinamos la \<TemplateData> sección de la [nueva generación de proyectos: en el capó, la primera parte](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md). Las etiquetas de esta sección se utilizan para controlar la apariencia del cuadro de diálogo **nuevo proyecto** .

 Las etiquetas de la \<TemplateContent> sección controlan la generación de nuevos proyectos y elementos de proyecto. Esta es la \<TemplateContent> sección del archivo cswindowsapplication. vstemplate de la carpeta \Archivos de Programa\microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip

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

 La \<Project> etiqueta controla la generación de un proyecto y la \<ProjectItem> etiqueta controla la generación de un elemento de proyecto. Si el parámetro ReplaceParameters es true, la plantilla personalizará todos los parámetros de plantilla en el archivo o elemento de proyecto. En este caso, se personalizan todos los elementos de proyecto, excepto Settings. Settings.

 El parámetro TargetFileName especifica el nombre y la ruta de acceso relativa del archivo o elemento de proyecto resultante. Esto le permite crear una estructura de carpetas para el proyecto. Si no especifica este argumento, el elemento de proyecto tendrá el mismo nombre que la plantilla de elemento de proyecto.

 La estructura de carpetas de aplicaciones de Windows resultante tiene el siguiente aspecto:

 ![Captura de pantalla de la estructura de carpetas de aplicaciones de Windows para la solución "simple" en la Explorador de soluciones de Visual Studio.](../../extensibility/internals/media/simplesolution.png)

 La primera y única \<Project> etiqueta de la plantilla lee:

```xml
<Project File="WindowsApplication.csproj" ReplaceParameters="true">
```

 Esto indica a la nueva plantilla de proyecto que cree el archivo de proyecto. csproj simple copiando y personalizando el elemento de plantilla archivo WindowsApplication. csproj.

### <a name="designers-and-references"></a>Diseñadores y referencias
 Puede ver en el Explorador de soluciones que la carpeta propiedades está presente y contiene los archivos esperados. Pero ¿qué ocurre con las referencias de proyecto y las dependencias de archivo de diseñador, como Resources.Designer.cs a Resources. resx y Form1.Designer.cs a Form1.cs?  Estos se configuran en el archivo. csproj simple cuando se genera.

 Este es el \<ItemGroup> de simple. csproj que crea las referencias del proyecto:

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

 Puede ver que estas son las seis referencias de proyecto que aparecen en el Explorador de soluciones. Esta es una sección de otra \<ItemGroup> . Se han eliminado muchas líneas de código para mayor claridad. En esta sección se hace que Settings.Designer.cs dependa de Settings. Settings:

```xml
<ItemGroup>
    <Compile Include="Properties\Settings.Designer.cs">
        <DependentUpon>Settings.settings</DependentUpon>
    </Compile>
</ItemGroup>
```

## <a name="see-also"></a>Consulte también

- [Generación de nuevos proyectos: Aspectos técnicos (parte 1)](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)
- [MSBuild](../../msbuild/msbuild.md)
