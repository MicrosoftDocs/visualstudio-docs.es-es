---
title: Adición o edición de etiquetas en plantillas de proyecto
description: Obtenga información sobre cómo agregar o editar etiquetas en las plantillas de proyecto en Visual Studio.
ms.date: 04/30/2019
author: minsa110
ms.author: somin
manager: jillfra
ms.topic: reference
helpviewer_keywords:
- item templates, updating
- Visual Studio templates, updating
- project templates, updating
- updating templates [Visual Studio]
- template tagging, updating
- template tags, updating
ms.openlocfilehash: 37a1965712920420bdc4d784a003dbfbd2f2167a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85285223"
---
# <a name="add-tags-to-project-templates"></a>Adición de etiquetas en plantillas de proyecto

A partir de [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/), versión 16.1 Preview 2, puede agregar etiquetas de tipo de proyecto, plataforma y lenguaje a las plantillas de proyecto. 

Las etiquetas se usan en dos lugares del cuadro de diálogo **Nuevo proyecto**:

- Las etiquetas aparecen en la descripción de la plantilla.

   ![Plantilla de proyecto con etiquetas en el cuadro de diálogo Nuevo proyecto.](media/npd-item-with-template-tags.png)

- Las etiquetas permiten filtrar la plantilla y realizar búsquedas en ella.

   ![Búsqueda y filtrado en el cuadro de diálogo Nuevo proyecto.](media/npd-search-and-filter.png)

Para agregar etiquetas, actualice el archivo XML *.vstemplate*. Puede usar etiquetas de plantilla integradas en Visual Studio, o bien crear etiquetas de plantilla personalizadas. Las etiquetas de plantilla solo aparecen en el cuadro de diálogo **Nuevo proyecto** de Visual Studio 2019. Las etiquetas de plantilla no afectan al modo de representar la plantilla en versiones anteriores de Visual Studio.

## <a name="add-or-edit-tags"></a>Adición o edición de etiquetas

Es posible que quiera agregar o editar etiquetas en el archivo XML *.vstemplate* de la plantilla del proyecto al realizar las siguientes acciones:

* [Crear una nueva plantilla de proyecto](how-to-create-project-templates.md) mediante el Asistente para exportar plantillas.
* [Actualizar la plantilla de proyecto existente](how-to-update-existing-templates.md).
* [Crear una nueva plantilla de proyecto VSIX](../extensibility/getting-started-with-the-vsix-project-template.md).

## <a name="syntax"></a>Sintaxis

```xml
<LanguageTag> Language Name </LanguageTag>
<PlatformTag> Platform Name </PlatformTag>
<ProjectTypeTag> Project Type </ProjectTypeTag>
```

## <a name="attributes"></a>Atributos

Puede usar los siguientes atributos opcionales en escenarios de usuario avanzado:

|Atributo|Descripción|
|---------------|-----------------|
|`Package`|Un identificador GUID que especifica el id. paquete de Visual Studio.|
|`ID`|Especifica el identificador de recurso de Visual Studio.|

Sintaxis:

```xml
<LanguageTag Package="{PackageID}" ID="ResourceID" />
<PlatformTag Package="{PackageID}" ID="ResourceID" />
<ProjectTypeTag Package="{PackageID}" ID="ResourceID" />
```

## <a name="elements"></a>Elementos

### <a name="child-elements"></a>Elementos secundarios

Ninguno.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|(Obligatorio) Clasifica la plantilla y define cómo se muestra en el cuadro de diálogo **Nuevo proyecto** o **Agregar nuevo elemento**.|

## <a name="text-value"></a>Valor de texto

Se requiere un valor de texto, a menos que use los atributos `Package` y `ID`.

El texto proporciona el nombre de la plantilla.

## <a name="built-in-tags"></a>Etiquetas integradas

Visual Studio ofrece una lista de etiquetas integradas. Al agregar una etiqueta integrada, esta representa un recurso localizado. 

En la siguiente lista se muestran las etiquetas integradas disponibles en Visual Studio. Los valores correspondientes se muestran entre paréntesis.

| Etiqueta de idioma | Etiqueta de plataforma | Etiqueta de tipo de proyecto |
| -- | -- | -- |
| C++ (`cpp`) | Android (`android`) | Nube (`cloud`) |
| C# (`csharp`) | Azure (`azure`) | Consola (`console`) |
| F# (`fsharp`) | iOS (`ios`) | Escritorio (`desktop`) |
| Java (`java`) | Linux (`linux`) | Extensiones (`extension`) |
| JavaScript (`javascript`) | macOS (`macos`) | Juegos (`games`) |
| Python (`python`) | tvOS (`tvos`) | IoT (`iot`) |
| Lenguaje de consulta (`querylanguage`) | Windows (`windows`) | Biblioteca (`library`) |
| TypeScript (`typescript`) | Xbox (`xbox`) | Machine Learning (`machinelearning`) |
| Visual Basic (`visualbasic`) | | Para dispositivos móviles (`mobile`) |
| | | Office (`office`) |
| | | Otros (`other`) |
| | | Servicio (`service`) |
| | | Prueba (`test`) |
| | | UWP (`uwp`) |
| | | Web (`web`) |

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra los metadatos de una plantilla de proyecto para una aplicación Visual C#:

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>csharp</ProjectType>
        <LanguageTag>C#</LanguageTag>
        <PlatformTag>windows</PlatformTag>
        <PlatformTag>linux</PlatformTag>
        <PlatformTag>My Platform</PlatformTag>
        <ProjectTypeTag>console</ProjectTypeTag>
        <ProjectTypeTag>desktop</ProjectTypeTag>
    </TemplateData>
    <TemplateContent>
        <Project File="MyTemplate.csproj">
            <ProjectItem>Form1.cs<ProjectItem>
            <ProjectItem>Form1.Designer.cs</ProjectItem>
            <ProjectItem>Program.cs</ProjectItem>
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>
            <ProjectItem>Properties\Resources.resx</ProjectItem>
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>
            <ProjectItem>Properties\Settings.settings</ProjectItem>
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Vea también

- [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Creación de plantillas de proyecto y elemento](creating-project-and-item-templates.md)
- [Personalización de plantillas de proyectos y elementos](customizing-project-and-item-templates.md)
- [Introducción a la plantilla de proyecto VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)
