---
title: Atributo buildOnLoad y (elemento) (plantillas de Visual Studio)
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#BuildOnLoad
helpviewer_keywords:
- BuildOnLoad attribute [Visual Studio Templates]
- BuildOnLoad element [Visual Studio Templates]
ms.assetid: 950f5fc1-d041-4090-9a5c-60844768a4cc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f32056aae3c860aee250248c606bbda4dbf9506c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66321270"
---
# <a name="buildonload-attribute-and-element"></a>BuildOnLoad atributos y elementos

Especifica si se debe compilar el proyecto inmediatamente después de crearlo. **BuildOnLoad** es un atributo y un elemento.

Jerarquía de elementos:

```xml
<VSTemplate>
  <TemplateData>
    <BuildOnLoad>
```

## <a name="element-syntax"></a>Sintaxis de elemento

```xml
<BuildOnLoad> true/false </BuildOnLoad>
```

## <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Clasifica la plantilla y define cómo se muestra en el cuadro de diálogo **Nuevo proyecto** o **Agregar nuevo elemento** .|

## <a name="text-value"></a>Valor de texto

Falta un valor de texto para el **BuildOnLoad** elemento. El texto debe ser `true` o `false`, que indica si se debe compilar el proyecto inmediatamente después de crearlo.

## <a name="remarks"></a>Comentarios

**BuildOnLoad** es un atributo opcional. El valor predeterminado es `false`.

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra los metadatos de un C# plantilla cuando **BuildOnLoad** se utiliza como un elemento:

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <BuildOnLoad>true</BuildOnLoad>
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

- [Elemento buildProjectOnload](buildprojectonload-element-visual-studio-templates.md)
- [Elemento TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)
- [Crear plantillas para proyectos y elementos](../ide/creating-project-and-item-templates.md)
- [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)