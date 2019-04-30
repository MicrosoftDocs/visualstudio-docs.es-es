---
title: TemplateContent (elemento) (plantillas de Visual Studio) | Documentos de Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateContent
helpviewer_keywords:
- TemplateContent element [Visual Studio project templates]
ms.assetid: 90ae401c-b294-49ac-98da-e0d274f5bebb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c27f9ce239d5d82dc972186912266cea0d4f1ddf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62432283"
---
# <a name="templatecontent-element-visual-studio-templates"></a>TemplateContent (Elemento, Plantillas de Visual Studio)

Especifica el contenido de la plantilla.

Jerarquía de elementos:

```xml
<VSTemplate>
  <TemplateContent>
```

## <a name="syntax"></a>Sintaxis

```xml
<TemplateContent>
    ...
</TemplateContent>
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|[BuildOnLoad](../extensibility/buildonload-visual-studio-templates.md)|Especifica si se debe compilar la solución cuando se crea un proyecto de la plantilla.|

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|Elemento opcional.<br /><br /> Especifica la organización y el contenido de las plantillas de varios proyectos.|
|[Proyecto](../extensibility/project-element-visual-studio-templates.md)|Elemento opcional.<br /><br /> Especifica los archivos o directorios que se agregarán al proyecto.|
|[Referencias](../extensibility/references-element-visual-studio-templates.md)|Elemento opcional.<br /><br /> Especifica las referencias de ensamblado necesarias para una plantilla de elemento.|
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|Elemento opcional.<br /><br /> Especifica un archivo de la plantilla.|
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|Elemento opcional.<br /><br /> Especifica los parámetros personalizados que se utilizan cuando se crea un proyecto o elemento de la plantilla.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Contiene todos los metadatos de la plantilla de proyecto, la plantilla de elemento o el starter kit de.|

## <a name="remarks"></a>Comentarios
 `TemplateContent` es un elemento requerido.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra los metadatos para una plantilla de proyecto para un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] aplicación.

```xml
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
- [Crear plantillas para proyectos y elementos en Visual Studio](../ide/creating-project-and-item-templates.md)