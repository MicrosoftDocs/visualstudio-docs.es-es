---
title: Description (elemento, plantillas de Visual Studio) | Microsoft Docs
description: Obtenga información sobre el elemento Description y cómo especifica la descripción de la plantilla tal y como aparece en el cuadro de diálogo nuevo proyecto o agregar nuevo elemento.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Description element [Visual Studio project templates]
ms.assetid: 6e12be73-081f-4c7d-898f-027c307a9fe1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8a48e80800480a6e6fa1d9576b83112fd7cdcff4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091297"
---
# <a name="description-element-visual-studio-templates"></a>Description (elemento, plantillas de Visual Studio)
Especifica la descripción de la plantilla tal y como aparece en el cuadro de diálogo **nuevo proyecto** o **Agregar nuevo elemento** .

 \<VSTemplate> \<TemplateData>
 \<Description>

## <a name="syntax"></a>Sintaxis

```
<Description>
    Template Description
</Description>
```

```
<Description Package="{PackageID}" ID="ResourceID" />
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|`Package`|Atributo opcional, para escenarios de usuario avanzados.<br /><br /> Un identificador GUID que especifica el id. paquete de Visual Studio.|
|`ID`|Atributo opcional, para escenarios de usuario avanzados.<br /><br /> Especifica el identificador de recurso de Visual Studio.|

### <a name="child-elements"></a>Elementos secundarios
 Ninguno.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Clasifica la plantilla y define cómo se muestra en el cuadro de diálogo **Nuevo proyecto** o **Agregar nuevo elemento** .|

## <a name="text-value"></a>Valor de texto
 Se requiere un valor de texto a menos que se usen los atributos `Package` y `ID`.

 En el texto se proporciona una descripción de la plantilla.

## <a name="remarks"></a>Observaciones
 `Description` es un elemento secundario necesario del `TemplateData` elemento.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestran los metadatos de una plantilla de proyecto para una [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] aplicación.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
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
