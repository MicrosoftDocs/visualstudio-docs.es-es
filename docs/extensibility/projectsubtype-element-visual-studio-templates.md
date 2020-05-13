---
title: Elemento ProjectSubType (Plantillas de Visual Studio) Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectSubType
helpviewer_keywords:
- ProjectSubType element [Visual Studio Templates]
- <ProjectSubType> element [Visual Studio Templates]
ms.assetid: f6895cd4-3e95-4f0e-aa9e-8c7750f46ed4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 27396ad1bcc4e181b2b8cecd6ca863db2412630d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701826"
---
# <a name="projectsubtype-element-visual-studio-templates"></a>Elemento ProjectSubType (plantillas de Visual Studio)
Clasifica la plantilla en una subcategoría del valor `ProjectType` especificado en el elemento.

 \<VSTemplate \<> TemplateData> \<> ProjectSubType

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

## <a name="remarks"></a>Observaciones
 `ProjectSubType` es un elemento secundario opcional de `TemplateData`.

 El `ProjectSubType` elemento proporciona una subcategoría para el [ProjectType](../extensibility/projecttype-element-visual-studio-templates.md) elemento. Este valor puede incluir:

- `SmartDevice-NETCFv1`: especifica que la [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] plantilla tiene como destino la versión 1.0.

- `SmartDevice-NETCFv2`: especifica que la [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] plantilla tiene como destino la versión 2.0.

  Si una plantilla `ProjectType` contiene un `Web`elemento `ProjectSubType` con un valor de , el elemento especifica el lenguaje de programación de la plantilla. Este elemento puede tener los siguientes valores:

- `CSharp`: especifica que la [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] plantilla crea un proyecto web o un elemento.

- `VisualBasic`: especifica que la [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] plantilla crea un proyecto web o un elemento.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestran [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] los metadatos [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] de una plantilla de proyecto para una aplicación de dispositivo destinada a la versión 2.0.

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
- [Referencia de esquema de plantilla de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Creación de plantillas de proyecto y elemento](../ide/creating-project-and-item-templates.md)
- [Elemento ProjectType (plantillas de Visual Studio)](../extensibility/projecttype-element-visual-studio-templates.md)
