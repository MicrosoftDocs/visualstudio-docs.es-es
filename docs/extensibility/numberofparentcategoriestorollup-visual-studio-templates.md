---
title: Elemento NumberOfParentCategoriesToRollUp (plantillas)
description: Obtenga información sobre el elemento NumberOfParentCategoriesToRollUp y cómo especifica el número de categorías primarias que mostrarán la plantilla en el cuadro de diálogo nuevo proyecto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#NumberOfParentCategoriesToRollUp
helpviewer_keywords:
- NumberOfParentCategoriesToRollUp element [Visual Studio Templates]
- <NumberOfParentCategoriesToRollUp> element [Visual Studio Templates]
ms.assetid: 6f9d36f5-ae23-4a92-8132-b11799e2c21a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 02c6f0e22429b268fb643c622ebd1f237a4721d3
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090478"
---
# <a name="numberofparentcategoriestorollup-element-visual-studio-templates"></a>NumberOfParentCategoriesToRollUp (elemento, plantillas de Visual Studio)
Especifica el número de categorías primarias que mostrarán la plantilla en el cuadro de diálogo **nuevo proyecto** .

 \<VSTemplate> \<TemplateData>
 \<NumberOfParentCategoriesToRollUp>

## <a name="syntax"></a>Sintaxis

```xml
<NumberOfParentCategoriesToRollUp>
1
</NumberOfParentCategoriesToRollUp>
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos
 Ninguno.

### <a name="child-elements"></a>Elementos secundarios
 Ninguno.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Clasifica la plantilla y define cómo se muestra en el cuadro de diálogo **Nuevo proyecto** o **Agregar nuevo elemento** .|

## <a name="text-value"></a>Valor de texto
 `integer`Se requiere un valor.

 Este valor especifica el número de categorías primarias que mostrarán la plantilla en el cuadro de diálogo **nuevo proyecto** .

## <a name="remarks"></a>Observaciones
 `NumberOfParentCategoriesToRollUp` es un elemento opcional.

## <a name="example"></a>Ejemplo
 En este ejemplo se muestran los metadatos de una [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] aplicación Windows. Si una plantilla con estos metadatos se coloca en dos niveles de carpeta por debajo del nodo de nivel superior [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] , la plantilla aparecerá en el nodo de nivel superior del cuadro de diálogo **nuevo proyecto** . Si `NumberOfParentCategoriesToRollUp` no se establece, la plantilla solo aparece en el nodo en el que se encuentra físicamente.

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <NumberOfParentCategoriesToRollUp>2</NumberOfParentCategoriesToRollUp>
    </TemplateData>
    <TemplateContent>
        <Project File="MyStarterKit.csproj">
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
