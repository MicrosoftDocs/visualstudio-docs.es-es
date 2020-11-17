---
title: Createnewfolder ((elemento, plantillas de Visual Studio) | Microsoft Docs
description: Obtenga información sobre el elemento Createnewfolder (y cómo determina si el directorio de destino donde se va a crear el proyecto no existe.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CreateNewFolder
helpviewer_keywords:
- CreateNewFolder element [Visual Studio project templates]
ms.assetid: acef2016-4140-45d6-ace8-b8160eabd676
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 15633c2f701c813ca24c5484fd4108a86c57b05b
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671584"
---
# <a name="createnewfolder-element-visual-studio-templates"></a>Createnewfolder ((elemento, plantillas de Visual Studio)
Determina si hay que comprobar que el directorio de destino donde se va a crear el proyecto no existe. Si el directorio existe, se puede crear un directorio nuevo para el proyecto. Esta configuración se suele sobrescribir por medio de la marca del Registro `NewProjectRequiresNewFolder(VsTemplate)` (`HKEY_LOCAL_MACHINE/SOFTWARE(/Wow6432Node)/Microsoft/VisualStudio/<version number>/Projects/<project GUID>`) que usan todos los tipos de proyecto comunes para determinar si un proyecto nuevo se creará en un directorio nuevo.

 \<VSTemplate> \<TemplateData>
 \<CreateNewFolder>

## <a name="syntax"></a>Sintaxis

```
<CreateNewFolder>
    true/false
</CreateNewFolder>
```

## <a name="type"></a>Tipo
 `Boolean`

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos
 Ninguno.

### <a name="child-elements"></a>Elementos secundarios
 Ninguno.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Clasifica la plantilla y define cómo se muestra en el cuadro de diálogo **Nuevo proyecto** o **Agregar nuevo elemento** .|

## <a name="text-value"></a>Valor de texto
 Se requiere un valor de texto.

 El texto debe ser `true` o `false`, e indica si se debe crear o no una nueva carpeta contenedora cuando se cree un proyecto a partir de la plantilla.

## <a name="remarks"></a>Comentarios
 `CreateNewFolder` es un elemento opcional. El valor predeterminado es `true`.

 El valor especificado en el elemento `CreateNewFolder` solo se admite en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] si el sistema de proyectos subyacente lo admite.

## <a name="example"></a>Ejemplo
 En el ejemplo de código siguiente se especifica que no se debe crear una nueva carpeta al crear un proyecto a partir de la plantilla.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <CreateNewFolder>false</CreateNewFolder>
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
- [Crear plantillas para proyectos y elementos](../ide/creating-project-and-item-templates.md)
