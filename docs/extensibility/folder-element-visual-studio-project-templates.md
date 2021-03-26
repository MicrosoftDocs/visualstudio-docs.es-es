---
title: Folder (elemento, plantillas de proyecto de Visual Studio) | Microsoft Docs
description: Obtenga información sobre el elemento Folder y cómo especifica una carpeta que se agregará al proyecto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Folder
helpviewer_keywords:
- Folder element [Visual Studio project templates]
ms.assetid: 558e3d41-0db5-4c44-82bb-6bb87892b093
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 40e1df1d5efeab17adf60a8e1732991cb2cac02a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070133"
---
# <a name="folder-element-visual-studio-project-templates"></a>Folder (elemento, plantillas de proyecto de Visual Studio)
Especifica una carpeta que se agregará al proyecto.

 \<VSTemplate> \<TemplateContent>
 \<Project>
 \<Folder>

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
|`Name`|Atributo necesario.<br /><br /> Nombre de la carpeta del proyecto.|
|`TargetFolderName`|Atributo opcional.<br /><br /> Especifica el nombre que se va a asignar a la carpeta cuando se crea un proyecto a partir de la plantilla. Este atributo es útil para usar el reemplazo de parámetros con el fin de crear un nombre de carpeta o asignar un nombre a una carpeta con una cadena internacional que no se pueda usar directamente en el archivo *. zip* .|

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|`Folder`|Especifica la carpeta que se va a agregar al proyecto. `Folder` los elementos pueden contener `Folder` elementos secundarios.|
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|Especifica un archivo que se va a agregar al proyecto.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Proyecto](../extensibility/project-element-visual-studio-templates.md)|Elemento secundario opcional de [TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md).|

## <a name="remarks"></a>Observaciones
 `Folder` es un elemento secundario opcional de `Project` .

 Puede usar cualquiera de los métodos siguientes para organizar los elementos de proyecto en carpetas en una plantilla:

- Incluya las carpetas en el archivo. *zip* de plantilla y agréguelas al proyecto en el archivo *. vstemplate* especificando la ruta de acceso al archivo en los `ProjectItem` elementos, sin `Folder` elementos. Éste es el método recomendado. Por ejemplo:

     `...`

     `<ProjectItem>\Folder\item.cs</ProjectItem>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

- Incluya las carpetas en el archivo *. zip* de plantilla y agréguelas al proyecto en el archivo *. vstemplate* con `Folder` los elementos. Por ejemplo:

     `...`

     `<Folder name="Folder">`

     `<ProjectItem>item.cs</ProjectItem>`

     `</Folder>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

- No incluya carpetas en el archivo *. zip* de plantilla, pero agregue carpetas mediante el `TargetFileName` atributo del `ProjectItem` elemento. Por ejemplo:

     `...`

     `<ProjectItem TargetFileName="\Folder\item.cs">item.cs</ProjectItem>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestran los metadatos de una plantilla de proyecto para una [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] aplicación de Windows.

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
- [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Crear plantillas para proyectos y elementos](../ide/creating-project-and-item-templates.md)
- [ProjectItem (Elemento, Plantillas de elementos de Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)
