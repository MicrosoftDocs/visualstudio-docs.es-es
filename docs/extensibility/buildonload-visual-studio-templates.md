---
title: Atributo y elemento BuildOnLoad (plantillas de Visual Studio)
titleSuffix: ''
description: Obtenga información sobre el atributo y el elemento BuildOnLoad y cómo especifica si se debe compilar el proyecto inmediatamente después de su creación.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#BuildOnLoad
helpviewer_keywords:
- BuildOnLoad attribute [Visual Studio Templates]
- BuildOnLoad element [Visual Studio Templates]
ms.assetid: 950f5fc1-d041-4090-9a5c-60844768a4cc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5fe0fa745ef611395abe6244c0e207271b182cb4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927332"
---
# <a name="buildonload-attribute-and-element"></a>Atributo y elemento BuildOnLoad

Especifica si se debe compilar el proyecto inmediatamente después de su creación. **BuildOnLoad** es un atributo y un elemento.

Jerarquía de elementos:

```xml
<VSTemplate>
  <TemplateData>
    <BuildOnLoad>
```

## <a name="element-syntax"></a>Sintaxis de los elementos

```xml
<BuildOnLoad> true/false </BuildOnLoad>
```

## <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Clasifica la plantilla y define cómo se muestra en el cuadro de diálogo **Nuevo proyecto** o **Agregar nuevo elemento** .|

## <a name="text-value"></a>Valor de texto

Se requiere un valor de texto para el elemento **BuildOnLoad** . El texto debe ser `true` o `false` , lo que indica si se va a compilar el proyecto inmediatamente después de su creación.

## <a name="remarks"></a>Notas

**BuildOnLoad** es un atributo opcional. El valor predeterminado es `false`.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestran los metadatos de una plantilla de C# cuando se usa **BuildOnLoad** como elemento:

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

- [Elemento BuildProjectOnload](buildprojectonload-element-visual-studio-templates.md)
- [TemplateContent (elemento)](../extensibility/templatecontent-element-visual-studio-templates.md)
- [Crear plantillas para proyectos y elementos](../ide/creating-project-and-item-templates.md)
- [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
