---
title: Adición o edición de etiquetas en plantillas de proyecto
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
ms.openlocfilehash: 4a5113fa7f420d58892e2737ec9196422486490e
ms.sourcegitcommit: cd21b38eefdea2cdefb53e68e7a30b868e78dd6b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/22/2019
ms.locfileid: "66038631"
---
# <a name="add-tags-to-project-templates"></a>Adición de etiquetas en plantillas de proyecto

A partir de [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/), versión 16.1 Preview 2, puede agregar etiquetas de tipo de proyecto, plataforma y lenguaje a las plantillas de proyecto. Las etiquetas se usan en dos lugares en el cuadro de diálogo de nuevo proyecto:

- Las etiquetas aparecen en la descripción de la plantilla

   ![Plantilla de proyecto con las etiquetas en el cuadro de diálogo de nuevo proyecto](media/npd-item-with-template-tags.png)

- Las etiquetas permiten buscar y filtrar la plantilla

   ![Búsqueda y filtrado en el cuadro de diálogo de nuevo proyecto](media/npd-search-and-filter.png)

Puede agregar etiquetas mediante la actualización del archivo XML *.vstemplate* usando las etiquetas de plantilla integradas en Visual Studio o mediante la creación de etiquetas de la plantilla personalizadas. Las etiquetas de plantilla solo aparecen en el cuadro de diálogo de nuevo proyecto de Visual Studio 2019. No afectan a la representación de la plantilla en versiones anteriores de Visual Studio.

## <a name="add-or-edit-tags"></a>Adición o edición de etiquetas

Es posible que desee agregar o editar etiquetas en el archivo XML *.vstemplate* de la plantilla en los momentos siguientes:

* [Al crear una nueva plantilla de proyecto](/visualstudio/ide/how-to-create-project-templates) mediante el Asistente para exportar plantillas

* [Al actualizar la plantilla de proyecto existente](/visualstudio/ide/how-to-update-existing-templates)

* [Al crear una nueva plantilla de proyecto VSIX](/visualstudio/extensibility/getting-started-with-the-vsix-project-template)

## <a name="syntax"></a>Sintaxis

```xml
<LanguageTag> Language Name </LanguageTag>
<PlatformTag> Platform Name </PlatformTag>
<ProjectTypeTag> Project Type </ProjectTypeTag>
```

## <a name="attributes"></a>Atributos

Los siguientes atributos son opcionales y son para escenarios de usuarios avanzados.

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

Se requiere un valor de texto a menos que se usen los atributos `Package` y `ID`.

El texto proporciona el nombre de la plantilla.

## <a name="built-in-tags"></a>Etiquetas integradas

Visual Studio ofrece que una lista de etiquetas integradas que, cuando se agregan, representan un recurso localizado. La siguiente es una lista de etiquetas integradas y sus correspondientes valores entre paréntesis.

| Lenguaje | Plataforma | Tipo de proyecto |
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

El ejemplo siguiente muestra los metadatos de una plantilla de proyecto para una aplicación Visual C#.

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
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

- [Referencia de esquema de plantillas de Visual Studio](/visualstudio/extensibility/visual-studio-template-schema-reference)
- [Crear plantillas para proyectos y elementos](/visualstudio/ide/creating-project-and-item-templates)
- [Personalización de plantillas de proyectos y elementos](/visualstudio/ide/customizing-project-and-item-templates)
- [Introducción a la plantilla de proyecto VSIX](/visualstudio/extensibility/getting-started-with-the-vsix-project-template)