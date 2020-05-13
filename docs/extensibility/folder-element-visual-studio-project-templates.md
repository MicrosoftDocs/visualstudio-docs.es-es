---
title: Elemento Folder (Plantillas de proyecto de Visual Studio) Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Folder
helpviewer_keywords:
- Folder element [Visual Studio project templates]
ms.assetid: 558e3d41-0db5-4c44-82bb-6bb87892b093
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cb256b8be0dd9ce68f193750bf3ff5a383d5f073
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711469"
---
# <a name="folder-element-visual-studio-project-templates"></a>Elemento Folder (plantillas de proyecto de Visual Studio)
Especifica una carpeta que se agregará al proyecto.

 \<VSTemplate \<> TemplateContent \< \<>> de carpeta de> de proyecto

## <a name="syntax"></a>Sintaxis

```
<Folder Name="Project Folder">
    <Folder> ... </Folder>
    <ProjectItem> ... </ProjectItem>
</Folder>
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|`Name`|Atributo necesario.<br /><br /> El nombre de la carpeta del proyecto.|
|`TargetFolderName`|Atributo opcional.<br /><br /> Especifica el nombre que se va a asignar a la carpeta cuando se crea un proyecto a partir de la plantilla. Este atributo es útil para usar el reemplazo de parámetros para crear un nombre de carpeta o asignar un nombre a una carpeta con una cadena internacional que no se puede usar directamente en el archivo *.zip.*|

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|`Folder`|Especifica una carpeta que se va a agregar al proyecto. `Folder`elementos pueden `Folder` contener elementos secundarios.|
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|Especifica un archivo que se va a agregar al proyecto.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Project](../extensibility/project-element-visual-studio-templates.md)|Elemento secundario opcional de [TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md).|

## <a name="remarks"></a>Observaciones
 `Folder`es un hijo `Project`opcional de .

 Puede utilizar cualquiera de los métodos siguientes para organizar los elementos del proyecto en carpetas de una plantilla:

- Incluya las carpetas en el archivo *.zip* de plantilla y agréguelas al proyecto en `ProjectItem` el archivo `Folder` *.vstemplate* especificando la ruta de acceso al archivo en los elementos, sin elementos. Éste es el método recomendado. Por ejemplo:

     `...`

     `<ProjectItem>\Folder\item.cs</ProjectItem>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

- Incluya las carpetas en el archivo *.zip* de plantilla y agréguelas al proyecto en el archivo *.vstemplate* con `Folder` elementos. Por ejemplo:

     `...`

     `<Folder name="Folder">`

     `<ProjectItem>item.cs</ProjectItem>`

     `</Folder>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

- No incluya carpetas en el archivo *.zip* `TargetFileName` de plantilla, pero agregue carpetas con el atributo del `ProjectItem` elemento. Por ejemplo:

     `...`

     `<ProjectItem TargetFileName="\Folder\item.cs">item.cs</ProjectItem>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestran [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] los metadatos de una plantilla de proyecto para una aplicación de Windows.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
    </TemplateData>
    <TemplateContent>
        <Project File="MyTemplate.csproj">
            <ProjectItem>Form1.cs<ProjectItem>
            <ProjectItem>Form1.Designer.cs</ProjectItem>
            <ProjectItem>Program.cs</ProjectItem>
            <Folder Name="Properties">
                <ProjectItem>AssemblyInfo.cs</ProjectItem>
                <ProjectItem>Resources.resx</ProjectItem>
                <ProjectItem>Resources.Designer.cs</ProjectItem>
                <ProjectItem>Settings.settings</ProjectItem>
                <ProjectItem>Settings.Designer.cs</ProjectItem>
            </Folder>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Vea también
- [Referencia de esquema de plantilla de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Creación de plantillas de proyecto y elemento](../ide/creating-project-and-item-templates.md)
- [ProjectItem (Elemento, Plantillas de elementos de Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)
