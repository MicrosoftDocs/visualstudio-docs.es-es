---
title: ProjectSubType (elemento) (plantillas de Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectSubType
helpviewer_keywords:
- ProjectSubType element [Visual Studio Templates]
- <ProjectSubType> element [Visual Studio Templates]
ms.assetid: f6895cd4-3e95-4f0e-aa9e-8c7750f46ed4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 16852378609b058bc1f5c1c02ea2ad54a37a2ac9
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66335921"
---
# <a name="projectsubtype-element-visual-studio-templates"></a>ProjectSubType (elemento) (plantillas de Visual Studio)
Clasifica la plantilla en una subcategoría del valor especificado en el `ProjectType` elemento.

 \<VSTemplate > \<TemplateData > \<ProjectSubType >

## <a name="syntax"></a>Sintaxis

```xml
<ProjectSubType> SubType </ProjectSubType>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Clasifica la plantilla y define cómo se muestra en el cuadro de diálogo **Nuevo proyecto** o **Agregar nuevo elemento** .|

## <a name="text-value"></a>Valor de texto
 Se requiere un valor de texto.

 Este valor especifica la subcategoría de la plantilla.

## <a name="remarks"></a>Comentarios
 `ProjectSubType` es un elemento secundario opcional de `TemplateData`.

 El `ProjectSubType` elemento proporciona una subcategoría a la [ProjectType](../extensibility/projecttype-element-visual-studio-templates.md) elemento. Este valor puede incluir:

- `SmartDevice-NETCFv1`: Especifica que los destinos de la plantilla el [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] versión 1.0.

- `SmartDevice-NETCFv2`: Especifica que los destinos de la plantilla el [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] versión 2.0.

  Si una plantilla contiene un `ProjectType` elemento con un valor de `Web`, el `ProjectSubType` elemento especifica el lenguaje de programación de la plantilla. Este elemento puede tener los siguientes valores:

- `CSharp`: Especifica que la plantilla crea un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] proyecto o elemento Web.

- `VisualBasic`: Especifica que la plantilla crea un [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] proyecto o elemento Web.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra los metadatos para una plantilla de proyecto para una [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] aplicación de dispositivo como destino el [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] versión 2.0.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic device template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <ProjectSubType>SmartDevice-NETCFv2</ProjectSubType>
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
- [ProjectType (elemento) (plantillas de Visual Studio)](../extensibility/projecttype-element-visual-studio-templates.md)